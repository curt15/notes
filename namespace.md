Links: [[PROGRAMMING]] - [[TECHNOLOGY]] - [[PYTHON]]
Rel: [[macos]]; [[linux]]; [[windows]]
Tags: 

--- 

a **namespace** is an abstract container that holds logically grouped unique identifiers (and the value of the things that they reference) by a name.

When you open up a new window of Terminal.app and type [[ls]] (or cmd.exe and type [[dir]])
```sh
% ls
Desktop
Documents
Downloads
Library
Movies
Music
Pictures
Public
```
note the various namespaces being used:
- (1) [[ls]] is a command that owns the namespace "ls".
- (2) each listed directory (on the current path) owns it's own name ("Desktop", "Documents", ...) too.

The [[set]] command will show you a nice long list of some of the other namespaces being used within your current environment:
```sh
% set
```
-> create your own local **variable**...
```sh
% x="This is my important string."
% echo $x
This is my important string.
```
and see that your definition of "x" can now be found if you call [[set]] again!
```sh
% set
...
x='This is my important string.'
...
```

--- 
Note that when you close and re-open (or open a new window) of your CLI that the definition for "x" is gone... 
```sh
% echo $x

```

see: [[sh profile]] for an introduction to adding variables to your shell's default scope.





