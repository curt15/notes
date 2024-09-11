Links:	[[PYTHON]] - [[PROGRAMMING]]
Rel: [[python 3rd party packages]]
Ref: [home](https://kivy.org/#home); [docs](https://kivy.org/doc/stable/); [reStructuredText renderer](https://kivy.org/doc/stable/api-kivy.uix.rst.html); 

 kivy (multi-touch apps) 
 
 --- 

```pip install kivy```

--- 




--- 
#media 
Rel: [[sockets]]

sentdex video tut I believe

chatapp.py
```py
import os
import sys

import kivy
from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.gridlayout import GridLayout  # other layout structures exist
from kivy.uix.textinput import TextInput 
from kivy.uix.button import Button
from kivy.uix.screenmanager import ScreenManager, Screen
from kivy.clock import Clock
from kivy.core.window import Window
from kivy.uix.scrollview import ScrollView
kivy.require("1.10.1")

import socket_client # socket_client imports the server stuff, but won't need to touch that other than for error handling

# potential security issues:
# 1. passing through kivy
# 2. very little security checks from socket based tut


class ConnectPage(GridLayout):
	def __init__(self, **kwargs):
		super().__init__(**kwargs) # GridLayout __init__
		self.cols = 2  # num cols in grid

		if os.path.isfile('prev_details.txt'):
			with open('prev_details.txt', 'r') as f:
				d = f.read().split(',')
				prev_ip = d[0].strip()
				prev_port = d[1].strip()
				prev_username = d[2].strip()
		else:
			prev_ip = ''
			prev_port = ''
			prev_username = ''

		self.add_widget(Label(text='IP:'))  # top left
		self.ip = TextInput(text=prev_ip, multiline=False)
		self.add_widget(self.ip) # top right

		self.add_widget(Label(text='Port:')) # next left
		self.port = TextInput(text=prev_port, multiline=False)
		self.add_widget(self.port) # etc.

		self.add_widget(Label(text='Username:'))
		self.username = TextInput(text=prev_username, multiline=False)
		self.add_widget(self.username)

		self.add_widget(Label()) # blank space


		self.join = Button(text='Join')
		self.join.bind(on_press=self.join_button) # on_hover? hold?
		self.add_widget(self.join)

	def join_button(self, instance):
		# can get stuff at any time, not just scripty / button click
		port = self.port.text
		ip = self.ip.text
		username = self.username.text

		with open('prev_details.txt', 'w') as f:
			f.write(f"{ip}, {port}, {username}")

		info = f"Attempting to join {ip}:{port} as {username}"
		chatapp.info_page.update_info(info)

		chatapp.screen_manager.current = "Info"
		Clock.schedule_once(self.connect, 1) # 1 second into the future

	def connect(self, _): # instance, how many s gone by since schedule. Always 1 in this case, so _ to denote it's useless to us.
		port = int(self.port.text)
		ip = self.ip.text
		username = self.username.text

		if not socket_client.connect(ip, port, username, show_error):
			return

		chatapp.create_chat_page()
		chatapp.screen_manager.current = "Chat"



class ScrollableLabel(ScrollView):
	def __init__(self, **kwargs):
		super().__init__(**kwargs)
		self.layout = GridLayout(cols=1, size_hint_y=None)
		self.add_widget(self.layout)

		self.chat_history = Label(size_hint_y=None, markup=True) # markup to change colors for ea user
		self.scroll_to_point = Label() # target to scroll to

		self.layout.add_widget(self.chat_history)
		self.layout.add_widget(self.scroll_to_point)

	def update_chat_history(self, message):
		self.chat_history.text += '\n' + message # not sanitized

		self.layout.height = self.chat_history.texture_size[1] + 15 # 15 pixels for space at bottom
		self.chat_history.height = self.chat_history.texture_size[1]
		self.chat_history.text_size = (self.chat_history.width*0.98, None)

		self.scroll_to(self.scroll_to_point)

	def update_chat_history_layout(self, _=None):
		""" calling layout changes again from above again to maintain layout """
		self.layout.height = self.chat_history.texture_size[1] + 15
		self.chat_history.height = self.chat_history.texture_size[1]
		self.chat_history.text_size = (self.chat_history.width*0.98, None)



class ChatPage(GridLayout):
	def __init__(self, **kwargs):
		super().__init__(**kwargs)
		self.cols = 1
		self.rows = 2

		self.history = ScrollableLabel(height=Window.size[1]*0.9, size_hint_y=None)
		self.add_widget(self.history)

		self.new_message = TextInput(width=Window.size[0]*0.8, size_hint_x=None, multiline=False)
		self.send = Button(text='Send')
		self.send.bind(on_press=self.send_message)

		bottom_line = GridLayout(cols=2)
		bottom_line.add_widget(self.new_message)
		bottom_line.add_widget(self.send)
		self.add_widget(bottom_line)

		Window.bind(on_key_down=self.on_key_down)

		Clock.schedule_once(self.focus_text_input, 1)
		socket_client.start_listening(self.incoming_message, show_error)

		self.bind(size=self.adjust_fields)

	def adjust_fields(self, *_):

		# chat history height @ 90%, but leaving min 50px at bottom for new msg / send button:
		if Window.size[1] * 0.1 < 50:
			new_height = Window.size[1] - 50
		else:
			new_height = Window.size[1] * 0.9
		self.history.height = new_height

		# new message width @ 80%, but leaving min 160px for send button:
		if Window.size[0] * 0.2 < 160:
			new_width = Window.size[0] - 160
		else:
			new_width = Window.size[0] * 0.8
		self.new_message.width = new_width

		# update chat history layout:
		Clock.schedule_once(self.history.update_chat_history_layout, 0.01)


	def send_message(self, _): # return whether you hit send button or enter key - we don't care
		message = self.new_message.text
		self.new_message.text = '' # remove message from box once sent
		if message:
			self.history.update_chat_history(f"[color=dd2020]{chatapp.connect_page.username.text}[/color] > {message}")
			socket_client.send(message)

		Clock.schedule_once(self.focus_text_input, 0.1)


	def on_key_down(self, instance, keyboard, keycode, text, modifiers):
		if keycode == 40:
			self.send_message(None)


	def focus_text_input(self, _):
		self.new_message.focus = True

	def incoming_message(self, username, message):
		self.history.update_chat_history(f"[color=20dd20]{username}[/color] > {message}")



class InfoPage(GridLayout):
	def __init__(self, **kwargs):
		super().__init__(**kwargs)
		self.cols = 1

		self.message = Label(halign='center', valign='middle', font_size=30) # or .kv files
		self.message.bind(width=self.update_text_width) # update size dynamically
		self.add_widget(self.message)

	def update_info(self, message):
		self.message.text = message

	def update_text_width(self, *_): # anything else, but we don't care
		self.message.text_size = (self.message.width * 0.9, None) # none bc not worried about y



class ChatApp(App):
	def build(self):
		# return ConnectPage()
		self.screen_manager = ScreenManager()

		self.connect_page = ConnectPage()
		screen = Screen(name='Connect') # use "Connect" now anytime we want to ref this screen
		screen.add_widget(self.connect_page)
		self.screen_manager.add_widget(screen)

		self.info_page = InfoPage()
		screen = Screen(name='Info')
		screen.add_widget(self.info_page)
		self.screen_manager.add_widget(screen)

		return self.screen_manager

	def create_chat_page(self):
		"""
		Same logic as above.
		Separated out bc we need to connect before we can run this / build page.
		"""
		self.chat_page = ChatPage()
		screen = Screen(name='Chat')
		screen.add_widget(self.chat_page)
		self.screen_manager.add_widget(screen)

def show_error(message):
	chatapp.info_page.update_info(message)
	chatapp.screen_manager.current = "Info"
	Clock.schedule_once(sys.exit, 10)


if __name__ == "__main__":
	chatapp = ChatApp()
	chatapp.run()


```

socket_client.py
```py
"""
Copied directly. Slightly modified code from chatapp in sockets.
"""
import socket
import errno
from threading import Thread

HEADER_LENGTH = 10
client_socket = None

# Connects to the server
def connect(ip, port, my_username, error_callback):

    global client_socket

    # Create a socket
    # socket.AF_INET - address family, IPv4, some otehr possible are AF_INET6, AF_BLUETOOTH, AF_UNIX
    # socket.SOCK_STREAM - TCP, conection-based, socket.SOCK_DGRAM - UDP, connectionless, datagrams, socket.SOCK_RAW - raw IP packets
    client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    try:
        # Connect to a given ip and port
        client_socket.connect((ip, port))
    except Exception as e:
        # Connection error
        error_callback('Connection error: {}'.format(str(e)))
        return False

    # Prepare username and header and send them
    # We need to encode username to bytes, then count number of bytes and prepare header of fixed size, that we encode to bytes as well
    username = my_username.encode('utf-8')
    username_header = f"{len(username):<{HEADER_LENGTH}}".encode('utf-8')
    client_socket.send(username_header + username)

    return True

# Sends a message to the server
def send(message):
    # Encode message to bytes, prepare header and convert to bytes, like for username above, then send
    message = message.encode('utf-8')
    message_header = f"{len(message):<{HEADER_LENGTH}}".encode('utf-8')
    client_socket.send(message_header + message)

# Starts listening function in a thread
# incoming_message_callback - callback to be called when new message arrives
# error_callback - callback to be called on error
def start_listening(incoming_message_callback, error_callback):
    Thread(target=listen, args=(incoming_message_callback, error_callback), daemon=True).start()

# Listens for incomming messages
def listen(incoming_message_callback, error_callback):
    while True:

        try:
            # Now we want to loop over received messages (there might be more than one) and print them
            while True:

                # Receive our "header" containing username length, it's size is defined and constant
                username_header = client_socket.recv(HEADER_LENGTH)

                # If we received no data, server gracefully closed a connection, for example using socket.close() or socket.shutdown(socket.SHUT_RDWR)
                if not len(username_header):
                    error_callback('Connection closed by the server')

                # Convert header to int value
                username_length = int(username_header.decode('utf-8').strip())

                # Receive and decode username
                username = client_socket.recv(username_length).decode('utf-8')

                # Now do the same for message (as we received username, we received whole message, there's no need to check if it has any length)
                message_header = client_socket.recv(HEADER_LENGTH)
                message_length = int(message_header.decode('utf-8').strip())
                message = client_socket.recv(message_length).decode('utf-8')

                # Print message
                incoming_message_callback(username, message)

        except Exception as e:
            # Any other exception - something happened, exit
            error_callback('Reading error: {}'.format(str(e)))
```

socketserver.py
```py
"""
Copied directly. Exact code from chatapp in sockets.
"""
import socket
import select

HEADER_LENGTH = 10

IP = "127.0.0.1"
PORT = 1234

# Create a socket
# socket.AF_INET - address family, IPv4, some otehr possible are AF_INET6, AF_BLUETOOTH, AF_UNIX
# socket.SOCK_STREAM - TCP, conection-based, socket.SOCK_DGRAM - UDP, connectionless, datagrams, socket.SOCK_RAW - raw IP packets
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# SO_ - socket option
# SOL_ - socket option level
# Sets REUSEADDR (as a socket option) to 1 on socket
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)

# Bind, so server informs operating system that it's going to use given IP and port
# For a server using 0.0.0.0 means to listen on all available interfaces, useful to connect locally to 127.0.0.1 and remotely to LAN interface IP
server_socket.bind((IP, PORT))

# This makes server listen to new connections
server_socket.listen()

# List of sockets for select.select()
sockets_list = [server_socket]

# List of connected clients - socket as a key, user header and name as data
clients = {}

print(f'Listening for connections on {IP}:{PORT}...')

# Handles message receiving
def receive_message(client_socket):

    try:

        # Receive our "header" containing message length, it's size is defined and constant
        message_header = client_socket.recv(HEADER_LENGTH)

        # If we received no data, client gracefully closed a connection, for example using socket.close() or socket.shutdown(socket.SHUT_RDWR)
        if not len(message_header):
            return False

        # Convert header to int value
        message_length = int(message_header.decode('utf-8').strip())

        # Return an object of message header and message data
        return {'header': message_header, 'data': client_socket.recv(message_length)}

    except:

        # If we are here, client closed connection violently, for example by pressing ctrl+c on his script
        # or just lost his connection
        # socket.close() also invokes socket.shutdown(socket.SHUT_RDWR) what sends information about closing the socket (shutdown read/write)
        # and that's also a cause when we receive an empty message
        return False

while True:

    # Calls Unix select() system call or Windows select() WinSock call with three parameters:
    #   - rlist - sockets to be monitored for incoming data
    #   - wlist - sockets for data to be send to (checks if for example buffers are not full and socket is ready to send some data)
    #   - xlist - sockets to be monitored for exceptions (we want to monitor all sockets for errors, so we can use rlist)
    # Returns lists:
    #   - reading - sockets we received some data on (that way we don't have to check sockets manually)
    #   - writing - sockets ready for data to be send thru them
    #   - errors  - sockets with some exceptions
    # This is a blocking call, code execution will "wait" here and "get" notified in case any action should be taken
    read_sockets, _, exception_sockets = select.select(sockets_list, [], sockets_list)


    # Iterate over notified sockets
    for notified_socket in read_sockets:

        # If notified socket is a server socket - new connection, accept it
        if notified_socket == server_socket:

            # Accept new connection
            # That gives us new socket - client socket, connected to this given client only, it's unique for that client
            # The other returned object is ip/port set
            client_socket, client_address = server_socket.accept()

            # Client should send his name right away, receive it
            user = receive_message(client_socket)

            # If False - client disconnected before he sent his name
            if user is False:
                continue

            # Add accepted socket to select.select() list
            sockets_list.append(client_socket)

            # Also save username and username header
            clients[client_socket] = user

            print('Accepted new connection from {}:{}, username: {}'.format(*client_address, user['data'].decode('utf-8')))

        # Else existing socket is sending a message
        else:

            # Receive message
            message = receive_message(notified_socket)

            # If False, client disconnected, cleanup
            if message is False:
                print('Closed connection from: {}'.format(clients[notified_socket]['data'].decode('utf-8')))

                # Remove from list for socket.socket()
                sockets_list.remove(notified_socket)

                # Remove from our list of users
                del clients[notified_socket]

                continue

            # Get user by notified socket, so we will know who sent the message
            user = clients[notified_socket]

            print(f'Received message from {user["data"].decode("utf-8")}: {message["data"].decode("utf-8")}')

            # Iterate over connected clients and broadcast message
            for client_socket in clients:

                # But don't sent it to sender
                if client_socket != notified_socket:

                    # Send user and message (both with their headers)
                    # We are reusing here message header sent by sender, and saved username header send by user when he connected
                    client_socket.send(user['header'] + user['data'] + message['header'] + message['data'])

    # It's not really necessary to have this, but will handle some socket exceptions just in case
    for notified_socket in exception_sockets:

        # Remove from list for socket.socket()
        sockets_list.remove(notified_socket)

        # Remove from our list of users
        del clients[notified_socket]
```
