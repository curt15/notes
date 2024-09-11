Links: [[PROGRAMMING]] - [[TECHNOLOGY]]
Rel: [[macos]]; [[linux]]; [[windows]]
Tags: #private 

shared cli stuff

--- 

A **Command-line interface (CLI)** aka "shell" is a computer program that exposes the central working processes of the Operating System (OS) to a user or other programs via text input (generally called: "commands") that can be integrated together in automation via "scripting". 

--- 

Shells will naturally limit the ability of non-**superuser/administrator** users from accessing some of these powerful functions. 

windows: cmd.exe // powershell.exe
- (right-click -> "Run as Administrator") 
- if you are logged in as an Administrator user, you now have full access

macos/linux: Terminal.app // etc
- **sudo** commandname
- if you are a sudoer, will be prompted for a password to continue the command that requires it 

--- 

**"directories" == "folders"**

--> "Path"

. - the current directory
.. - the previous dir, upstream

windows
- c: = drive path
- \\ = root directory (& path symbol)

macos/linux
- / = root directory (& path symbol)
- ~ = home directory 

--- 

**Tab autocomplete**

windows
- will auto-complete to the first alphabetically listed, no matter what

macos/linux
- will auto-complete only if/to enough given to differentiate between any other equivalent to the point 


--- 

Wildcard = \*

\*.ext - asterisk is a wild-card - anything w/ ".ext" extension
\*.\* - star-dot-star = everything

--- 

set - view list of environment variables

--- 

whoami - show username that's currently logged in

--- 

flags / switches
\-
/

--- 

man / help

man man
help /?

--- 

"can fix all network problems w/ 3 commands 95% of the time":
ping
traceroute vs tracert
ipconfig vs ifconfig