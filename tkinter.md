Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[tkhtmlview]]; [[python standard library]]
Ref: [docs](https://docs.python.org/3/library/tkinter.html) ; [keysyms recognized by Tk](https://www.tcl.tk/man/tcl8.4/TkCmd/keysyms.html)
- https://stackoverflow.com/questions/37383755/keyboard-shortcuts-with-tkinter-in-python-3 (had issues getting multi-key press responses)

builtin interface to the Tk GUI toolkit 

--- 

**tkinterwindow.py**
use it to open a picture named 'example.jpg' in the same directory
```py
# via sentdex tut vid
from tkinter import *
from PIL import Image, ImageTk #pip install Pillow

class Window(Frame):

	def __init__(self, master=None): #master=None is default...
		Frame.__init__(self, master)

		self.master = master #calling this frame our master widget (main frame)

		self.init_window() #not built into Tkinter, building and using below

	def init_window(self):
		self.master.title('GUI title')

		self.pack(fill=BOTH, expand=1)

		## AS AN EXAMPLE, BUT BETTER TO HAVE BUTTON IN A MENU:
		# quitButton = Button(self, text='quit', command=self.client_exit)
		# quitButton.place(x=0, y=0) #starting at top left and moving by pixels.

		menu = Menu(self.master) #define the menu
		self.master.config(menu=menu) #append it to the main frame

		file = Menu(menu) #define file as part of our Menu() named menu
		file.add_command(label='Exit', command=self.client_exit) #add the command for the file button in menu
		menu.add_cascade(label='File', menu=file) #add the file button in the menu drop-down

		#1. Define the menu, 2. Add buttons within the menu, 3. Add cascade
		edit = Menu(menu)
		edit.add_command(label='Redo')
		edit.add_command(label='Undo') #not adding command, but must here.
		edit.add_command(label='Show Image', command=self.showIMG)
		edit.add_command(label='Show Text', command=self.showTXT)
		menu.add_cascade(label='Edit', menu=edit)

	def client_exit(self):
		exit()

	def showIMG(self):
		load = Image.open('example.jpg') # Pillow class.function
		load = load.resize((400, 300), Image.ANTIALIAS) # (height, width)
		render = ImageTk.PhotoImage(load) # Pillow
		img = Label(self, image=render) #packs in img or text
		img.image = render
		img.place(x=0,y=0)

	def showTXT(self):
		text = Label(self, text='Hey there good lookin!')
		text.pack()



root = Tk() #calling our root window
root.geometry("400x300")

app = Window(root)

root.mainloop() #initializes and generates the window
```
-> Expand by using different widgets (text boxes, etc).
Label() is a widget