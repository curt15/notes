Links: [[PROGRAMMING]]
Ref: https://www.sublimetext.com/

```sh
/Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl
# open, 

```
--- 
Tools > build systems -> e.g. Python 

cmd+shift+P --> Package Control

packages: BinaryPlist, PowerShell,
SublimeJedi: https://github.com/srusskih/SublimeJEDI
PrettyJSON: cmd+ctrl+j https://packagecontrol.io/packages/Pretty%20JSON

| cmd+d -> | additionally highlight next-most highlighted regex |
| cmd+shift+L | cursor select all highlighted lines ("latch") |
| control+shift+G | **Goto** definition |
| cmd+shift+B | build system (after menubar: Tools > build systems -> e.g. Python )
| cmd+click (file) | open 2n file in split pane |

- : set default virtualenv and interpreter path && sublime_completions_visibility -> "all"

--- 
- Preferences -> Package Settings -> Jedi -> Settings - User
```/Users/curtis/Library/Application\ Support/Sublime\ Text\ 3/Packages/User/sublime_jedi.sublime-settings``` :
```json
{
	"python_virtualenv": "/Users/curtis/prog/.envs/venv",
	"python_interpreter": "/Users/curtis/prog/.envs/venv/bin/python",
	"follow_imports": true,
	"sublime_completions_visibility": "all",
	"enable_in_sublime_repl": true
}
```

--- 
https://www.sublimetext.com/docs/3/projects.html
--- 

### quick references:

- (type) html --> (Press) tab --> 
```
<!DOCTYPE html>
	<html>
	<head>
		<title></title>
</head>
<body>

</body>
</html>
```


