Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python standard library]]

--- 
```py
import sockets
```

--- 


AF stands for Address Family
PF stands for Protocol Family
INET stands for INTERNET

AF_INET refers to addresses from the internet (IP addresses specifically)
PF_NET referes to anything in the protocol (usually sockets/ports.AF_INET in the address family
	used to designate what types of connections the socket can communicate with (in this case Internet Protocol v4 addresses))

When creating a socket you specify its address family and can then only use that type to communicate with.
For the most part AF_INET for socket programming over a network is the safest. AF_INET6 also exists.

client.py
```
import socket


HEADERSIZE = 10

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  # same socket as server in this example, but typically remote...

# connecting to send information:
s.connect((socket.gethostname(), 1234))


while True:

	full_msg = ''
	new_msg = True
	while True:
		msg = s.recv(16) # 1024 = buffer. Decision on how big of data chunks to recieve at a time.
		if new_msg:
			print(f"new message length: {msg[:HEADERSIZE]}")
			msglen = int(msg[:HEADERSIZE])
			new_msg = False

		full_msg += msg.decode('utf-8') # sent and recieved as bytes

		if len(full_msg)-HEADERSIZE == msglen:
			print("Full msg recvd")
			print(full_msg[HEADERSIZE:])
			new_msg = True
			full_msg = ''

	print(full_msg)
```

server.py
```
import socket
import time

HEADERSIZE = 10 # allows up to 1,000,000,000 bytes

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM) # socket is endpoint that recieves data / communication

# binding to recieve information:
s.bind((socket.gethostname(), 1234)) # (IP, port) in this case localhost, 4 digit port
s.listen(5) # queue = 5

while True:
	clientsocket, address = s.accept()
	# clientsocket is the foreign socket
	# address is the sender IP
	print(f"Connection from {address} has been established!")
	
	# a fixed length header is safe and tells client how long the message is.
	msg = "Welcome to the server!"
	msg = f'{len(msg):<{HEADERSIZE}}' + msg # :< is left alignment, ^ is centered, etc.
	clientsocket.send(bytes(msg, "UTF-8")) # or string.encode()

	# clientsocket.close() # Allows finally recieving the full_msg by the client 

	# example of repeating message. Can be sensor data, etc.
	while True:
		time.sleep(3)
		msg = f"The time is {time.time()}"
		msg = f'{len(msg):<{HEADERSIZE}}' + msg
		clientsocket.send(bytes(msg, "UTF-8"))
```


--- 

#### chat app

client.py
```
import socket
import select
import errno # match specific error codes - no message rto recv vs else
import sys

# client tells server what their username is
# infinte loop of if client has message to send, send message; also, recieve messsage from server

HEADER_LENGTH = 10

IP = '127.0.0.1'
PORT = 1234

my_username = input('Username: ')

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect((IP, PORT))
client_socket.setblocking(False) # receive function won't be blocking

username = my_username.encode('utf-8')
username_header = f"{len(username):<{HEADER_LENGTH}}".encode('utf-8')
client_socket.send(username_header + username)

while True:
	message = input(f"{my_username} > ")

	if message: # sending if not just hitting enter
		message = message.encode('utf-8')
		message_header = f"{len(message):<{HEADER_LENGTH}}".encode('utf-8')
		client_socket.send(message_header + message)
	try:
		while True:
			# receive things
			username_header = client_socket.recv(HEADER_LENGTH)
			if not len(username_header): # didn't get any data for whatever reason
				print('Connection closed by the server')
				sys.exit()

			username_length = int(username_header.decode('utf-8').strip())
			username = client_socket.recv(username_length).decode('utf-8') # recieving exact amount of bytes in username

			message_header = client_socket.recv(HEADER_LENGTH)
			message_length = int(message_header.decode('utf-8').strip())
			message = client_socket.recv(message_length).decode('utf-8')

			print(f"{username} > {message}")

	except IOError as e:
		if e.errno != errno.EAGAIN and e.errno != errno.EWOULDBLOCK: # OS specific error if there are no messages to recieve. Don't want to handle this.
			print('Reading error', str(e))
			sys.exit()
		continue

	except Exception as e:
		print('General error', str(e))
		sys.exit()
```


server.py
```
import socket
import select

HEADER_LENGTH = 10
IP = "127.0.0.1"
PORT = 1234

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1) # socket option level, , 1=true

server_socket.bind((IP, PORT))
server_socket.listen()

sockets_list = [server_socket, ] # clients

clients = {}





def receive_message(client_socket):
	try:
		message_header = client_socket.recv(HEADER_LENGTH)

		if not len(message_header):
			return False

		message_length = int(message_header.decode('utf-8').strip())
		return {'header': message_header, 'data':client_socket.recv(message_length)}

	except:
		return False


while True:
	read_sockets, _, exception_sockets = select.select(sockets_list, [], sockets_list) # read list, write list, error ons

	for notified_socket in read_sockets:
		if notified_socket == server_socket: # someone jsut connected and we need to accept / handlefor it
			client_socket, client_address = server_socket.accept()

			user = receive_message(client_socket)
			if user is False:
				continue

			sockets_list.append(client_socket)

			clients[client_socket] = user

			username = user['data'].decode('utf-8')

			print(f"Accepted new connection from {client_address[0]}:{client_address[1]} username:{username}")

		else:
			message = receive_message(notified_socket)

			if message is False:
				print(f"Closed connection from {clients[notified_socket]['data'].decode('utf-8')}")

				sockets_list.remove(notified_socket)
				del clients[notified_socket]
				continue

			user = clients[notified_socket]

			username = user['data'].decode('utf-8')
			msg = message['data'].decode('utf-8')

			print(f"Recieved message from {username}: {msg}")

			for client_socket in clients:
				if client_socket != notified_socket:
					client_socket.send(user['header'] + user['data'] + message['header'] + message['data'])

	for notified_socket in exception_sockets:
		sockets_list.remove(notified_socket)
		del clients[notified_socket]
```

---> pickled 

client.py
```
import socket
import pickle

HEADERSIZE = 10

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.connect((socket.gethostname(), 1234))


while True:

	full_msg = b'' # bytes
	new_msg = True
	while True:
		msg = s.recv(16)
		if new_msg:
			print(f"new message length: {msg[:HEADERSIZE]}")
			msglen = int(msg[:HEADERSIZE])
			new_msg = False

		full_msg += msg

		if len(full_msg)-HEADERSIZE == msglen:
			print("Full msg recvd")
			print(full_msg[HEADERSIZE:])

			d = pickle.loads(full_msg[HEADERSIZE:])
			print(d)

			new_msg = True
			full_msg = b''

	print(full_msg)
```

server.py
```
import socket
import pickle

HEADERSIZE = 10

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

s.bind((socket.gethostname(), 1234))
s.listen(5)

while True:
	clientsocket, address = s.accept()
	print(f"Connection from {address} has been established!")
	
	d = {1: "Hey", 2: "There"}
	msg = pickle.dumps(d)

	msg = bytes(f'{len(msg):<{HEADERSIZE}}', 'utf-8') + msg
	clientsocket.send(msg) 
```