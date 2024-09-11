Links: [[TECHNOLOGY]]
Rel: [[linux]]; [[windows]]
Tags: 
Refs: 
- https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptLangGuide/reference/ASLR_control_statements.html

--- 
- [[Terminal]].app - default [[command-line interface]]
- [[homebrew]] - package manager
- [[apps]]


--- 
- [[macos scripting]]
- [[Oh My Zsh]]
- [[osquery]]
- Apple developer iOS sim

--- 

/Applications
/System/Applications
/System/Applications/Utilities

/
Applications
Library
System
Users
Volumes
bin
cores
dev
etc -> private/etc
home -> /System/Volumes/data.home
opt
private
sbin
tmp -> private/tmp
use
var -> private/var

~
Desktop
Documents
Downloads
Library
Movies
Pictures
Public


Contacts
~/Library/Application\ Support/AddressBook


https://developer.apple.com/library/archive/documentation/General/Reference/InfoPlistKeyReference/Articles/AboutInformationPropertyListFiles.html

`~/Library/Preferences` ->
com.apple. .plist 





--- 

linking to ibooks: https://support.apple.com/en-us/HT202929 see [[RHCSA RHCE Red Hat Linux Certification 7th ed]] for example

--- 

| hotkey       | action     |
| :------------- | :----------: | 
|  cmd + shift + D | open dictionary (hover cursor over word) | 
| cmd + shift + . | toggle view hidden items in Finder. |
| cmd + Tab | toggle btwn open Applications. |
| control + Tab | toggle btwn current Application's open windows. |
| alt/option + click (in Dock) | toggle options (e.g. iTunes - choose Library) |
| cmd + R  | Reinstall the latest macOS that was installed on your Mac. (Recovery boot) | 
| option + R | Upgrade to the latest macOS that is compatible with your Mac. |
| cmd + option + shift + R | Reinstall the macOS that came with your Mac, or the closest version still available. |
| option (->boot) | -> image from thumb-drive |
| shift (-> safe boot) | -> hold shift during power on |
| control + option + shift + power | SMC (system management controller; "how accepting power from battery") reset (on iMac, just unplug) |
| cmd + option + p + r | NVRAM reset |
| cmd + "+" | Zoom in Application (larger text) |
| cmd + "-" | Zoom out Application (smaller text) |
| cmd + spacebar  | Spotlight Search |
| cmd + "\`" | cycle through windows |
| control + cmd + F | fullscreen toggle |
| cmd + option + control + power | shutdown |
| alt + < > (+shift) | jump cursor to next word (and highlight) |
| alt + a (+shift) | jump to start of line (and highlight) |
| alt + e (+shift) | jump to end of line (and highlight) |
| alt + cmd + <> | firefox - switch tabs L/R |
| cmd + m | minimize app window |
| control + ^ | Mission Control |
| cmd + shift + t | (firefox) open recent closed tabs | 
| cmd + , | open Preferences for current Application |
| fn + cmd + <- -> | scroll to top/bottom of Application window |
| cmd + control + q | lock screen |

--- 

Hoykey.app
| cmd + shift + ENTER | terminal |
| cmd + shift + O | Obsidian |
| cmd + shift + I | | Firefox (Internet) |
| cmd + shift +  B | Books.app |
| cmd + shift +  S | Sublime Text.app |

Flow -- Terminal full display 

--- 
	
## TERMINAL COMMANDS: 
https://ss64.com/osx/

caffeinate
dscl
dseditgroup
bless

scutil  # change hostname from cli
scutil --set ComputerName “newname”
scutil --set LocalHostName “newname”
scutil --set HostName “newname”


resetpassword

homebrew

--- 


## ETC:

#### "[[ other ]]"

#### linking to ibooks:
https://support.apple.com/en-us/HT202929
see [[RHCSA RHCE Red Hat Linux Certification 7th ed]] for example


#### backup mobile device to external drive
- https://appletoolbox.com/backup-iphone-external-drive/#When_to_Delete_the_Old_Backup_Folder
- [How to move your iPhone or iPad backups to an external hard drive](https://www.imore.com/how-move-your-iphone-or-ipad-backups-external-hard-drive)

```ln -s /Volumes/Archive/MobileSync/Backup/ ~/Library/Application\ Support/MobileSync/```


#### global startup file responsible for initializing path:
``` .etc/profile ```


#### Wireless Diagnostics -> "Window" -> Scan (find best wifi channels)

#### Serial Number System:
XXXX YYYY ZZZZ

--- 

Amethyst window tiling 
```brew install amethyst```