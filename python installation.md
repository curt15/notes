Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[pip]]
Ref: https://www.python.org/downloads/
Tags: #public 

--- 

The most simple and effective way to install Python is to visit https://python.org/.

Under the "Downloads" tab choose the appropriate .pkg/.exe for your OS.

When the download completes, click the installer in your Downloads folder and follow the short on-screen instructions. 
- Ensure to check the box to: **"Add Python 3.X to PATH"**, which will allow you to use ```python``` or ```python3``` from your command line. 

... -> 
- [[#macos]]
- [[#windows]]
- [[#advanced]] 

--- 
### [[macos]]

Open **Finder** and navigate to **/Applications/Python 3.X/**.
Click the  ```Install Certificates.command``` file, this will ensure that Python is able to successfully access the internet (e.g. using the [[requests]] library). 


Open **Terminal.app**

```bash
% which python
/usr/bin/python
```
```bash
% which python3
/Library/Frameworks/Python.framework/Versions/3.9/bin/python3
```
-> ```python``` is pointing to our system's **/usr/bin/python** (Python 2.7), ```python3``` is pointing to our freshly installed Python 3.9. So...

We'll use ```python3``` to create our first virtual environment: 
```bash
% python3 -m venv venv
```
```bash
% source venv/bin/activate
# ...
(venv) % 
```
Using ```source``` ^^, we are able to active it. 

We can have it activated by *default* anytime when opening a new Terminal.app window  open adding to our [[sh profile]] (found at **~/.bashrc** or **~/.zshrc**) by adding the following lines:

```bash
# ...
alias activate=". ~/venv/bin/activate"
activate
# ...
```

Otherwise, notice that anytime you open Terminal.app, your prompt (e.g. ```%```) isn't prepended with  e.g. ```(venv)```. 

See [[pip]] for more about virtual environments.

--- 
### [[windows]]

Open **cmd.exe**.

```powershell
C:\> where python3
C:\Users\alice\AppData\Local\Microsoft\WindowsApps\python3.exe
```
```powershell
C:\> where python
C:\Users\alice\AppData\Local\Programs\Python\Python3X\python.exe
C:\Users\alice\AppData\Local\Microsoft\WindowsApps\python3.exe
```
-> ```python3``` is pointing to open a link to the Windows Store, ```python``` (firstly) points to our freshly installed Python 3.9. So... 

We'll use ```python``` to create our first virtual environment: 
```powershell
C:\> python -m venv venv
```
```powershell
C:\> .\venv\Scripts\activate
# ...
(venv) C:\> 
```
Using ```.\venv\bin\activate``` we are able to activate it and the prepended ```(venv)``` let's us know it has been activated.

Additionally: 
```pip install wheel pyreadline``` to enable Tab-auto-completions within the python shell.

See [[pip]] for more about virtual environments.

--- 
### advanced
...via package managers:
- [[macos]]: see [[homebrew]] to learn how to ```brew install python@3.x``` directly from **Terminal.app**.
- [[windows]]: see [[chocolatey]] to learn how to ```choco install python``` directly from **cmd.exe**. 
- [[linux]]: e.g. ```sudo apt-get install python 3.x``` (if not already found installed ```python3 -v```), and additionally ```sudo apt-get -y python3-pip python3-dev python3-venv``` if necessary.

