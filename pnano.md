Links: [[PROJECTS]]
Rel: [[applescript]]
Ref: 
- https://unix.stackexchange.com/questions/497146/create-a-custom-url-protocol-handler
- https://unix.stackexchange.com/questions/112267/create-clickable-links-in-terminal#437585
- https://www.willmcgugan.com/blog/tech/post/building-rich-terminal-dashboards/
- https://rich.readthedocs.io/en/latest/layout.html#setting-renderables
- https://rich.readthedocs.io/en/latest/console.html#paging
- https://izziswift.com/is-there-a-way-to-make-a-link-clickable-in-the-osx-terminal/
- https://github.com/lepture/mistune

wiki system for nano 

| python | nano | 

--- 
**bugs**

- Activity Monitor iTerm & nano @ 98% cpu... ==> it's (was) the rich Live -> better to simply print, but ...
- -> when split 

doesn't work with " ' " in the name \[\[It's called The Internet\]\], and \[\["Words"\]\] -> repl " %22, but... otherwise, #todo hande for common ones: https://www.degraeve.com/reference/urlencoding.php

so:
- sending "close" command, but nano still running? 

--- 

[INDEX](nano:///Users/curtis/Library/Mobile%20Documents/com~apple~CloudDocs/Stuff/onotes/INDEX.md)

--- 
... 

```py
from rich.console import Console

console = Console()
console.print("Visit my [link=nano:///Users/curtis/main.py]blog[/link]!")

import pnbp
laddr = 'nano://' + pnbp.Notebook().NOTE_PATH.replace(' ', '%20') + '/test1.md'
console.print(f"Visit my [link={laddr}]blog[/link]!")

nb = pnbp.Notebook()
n = nb.get('test1')

from rich.markdown import Markdown
# ...
md = Markdown(text=n.md)
```

--- 
[[applescript]]:

using ```/Applications/Utilities/Script Editor.app``` (built-in),
-> "New Document" -> ... -> on save: "File Format: **Application**" -> move .app -> /Applications


-> /Applications/pnano.app

--- 
```py
on replace_chars(this_text, search_string, replacement_string)
	set AppleScript's text item delimiters to the search_string
	set the item_list to every text item of this_text
	set AppleScript's text item delimiters to the replacement_string
	set this_text to the item_list as string
	set AppleScript's text item delimiters to ""
	return this_text
end replace_chars


on open location myURL
	
	set oldDelims to AppleScript's text item delimiters
	set newDelims to {"://"}
	set AppleScript's text item delimiters to newDelims
	
	set pathname to item 2 of the text items of myURL
	set pathname to replace_chars(pathname, "%20", "\\ ")
	
	set newDelims to {"/"}
	set AppleScript's text item delimiters to newDelims
	
	set filename to item (count of the text items in pathname) of the text items of pathname
	
	set cmd to "nano " & pathname
	
	tell application "iTerm"
		activate
		
		try
			tell second session of current tab of current window
				close
			end tell
		end try
		
		tell current session of current tab of current window
			split vertically with default profile command cmd
		end tell
		
	end tell
	
	set AppleScript's text item delimiters to oldDelims
	
end open location
```


--- 
... actually 
one iteration behind, w/ pnbp direct integration
```py

on replace_chars(this_text, search_string, replacement_string)
	set AppleScript's text item delimiters to the search_string
	set the item_list to every text item of this_text
	set AppleScript's text item delimiters to the replacement_string
	set this_text to the item_list as string
	set AppleScript's text item delimiters to ""
	return this_text
end replace_chars


on open location myURL
	
	set oldDelims to AppleScript's text item delimiters
	set newDelims to {"://"}
	set AppleScript's text item delimiters to newDelims
	
	set pathname to item 2 of the text items of myURL
	set pathname to replace_chars(pathname, "%20", "\\ ")
	
	set newDelims to {"/"}
	set AppleScript's text item delimiters to newDelims
	
	set filename to item (count of the text items in pathname) of the text items of pathname
	
	set cmd to "/usr/local/Cellar/nano/5.8/bin/nano " & pathname
	
	set cmd2 to "/Users/curtis/prog/.envs/venv/bin/nb-pprint --note=\"" & filename & "\""
	
	tell application "iTerm"
		activate
		
		try
			tell second session of current tab of current window
				close
			end tell
		end try
		
		tell current session of current tab of current window
			write text "clear && printf '\\e[3J'"
			write text cmd2
			
			split vertically with default profile command cmd
			
		end tell
		
	end tell
	
	set AppleScript's text item delimiters to oldDelims
	
end open location

```
--- 

-> /Applications/pnano\.app/Contents/Info\.plist

```xml
<key>CFBundleURLTypes</key>
	<array>
		<dict>
			<key>CFBundleURLName</key>
			<string>Pnano URL</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>nano</string>
			</array>
		</dict>
	</array>
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
	<key>CFBundleAllowMixedLocalizations</key>
	<true/>
	<key>CFBundleDevelopmentRegion</key>
	<string>en</string>
	<key>CFBundleExecutable</key>
	<string>applet</string>
	<key>CFBundleIconFile</key>
	<string>applet</string>
	<key>CFBundleIdentifier</key>
	<string>com.apple.ScriptEditor.id.pnano</string>
	<key>CFBundleInfoDictionaryVersion</key>
	<string>6.0</string>
	<key>CFBundleName</key>
	<string>pnano</string>
	<key>CFBundlePackageType</key>
	<string>APPL</string>
	<key>CFBundleShortVersionString</key>
	<string>1.0</string>
	<key>CFBundleSignature</key>
	<string>aplt</string>
	<key>CFBundleURLTypes</key>
	<array>
		<dict>
			<key>CFBundleURLName</key>
			<string>Pnano URL</string>
			<key>CFBundleURLSchemes</key>
			<array>
				<string>nano</string>
			</array>
		</dict>
	</array>
	<key>LSMinimumSystemVersionByArchitecture</key>
	<dict>
		<key>x86_64</key>
		<string>10.6</string>
	</dict>
	<key>LSRequiresCarbon</key>
	<true/>
	<key>NSAppleEventsUsageDescription</key>
	<string>This script needs to control other applications to run.</string>
	<key>NSAppleMusicUsageDescription</key>
	<string>This script needs access to your music to run.</string>
	<key>NSCalendarsUsageDescription</key>
	<string>This script needs access to your calendars to run.</string>
	<key>NSCameraUsageDescription</key>
	<string>This script needs access to your camera to run.</string>
	<key>NSContactsUsageDescription</key>
	<string>This script needs access to your contacts to run.</string>
	<key>NSHomeKitUsageDescription</key>
	<string>This script needs access to your HomeKit Home to run.</string>
	<key>NSMicrophoneUsageDescription</key>
	<string>This script needs access to your microphone to run.</string>
	<key>NSPhotoLibraryUsageDescription</key>
	<string>This script needs access to your photos to run.</string>
	<key>NSRemindersUsageDescription</key>
	<string>This script needs access to your reminders to run.</string>
	<key>NSSiriUsageDescription</key>
	<string>This script needs access to Siri to run.</string>
	<key>NSSystemAdministrationUsageDescription</key>
	<string>This script needs access to administer this system to run.</string>
	<key>OSAAppletShowStartupScreen</key>
	<false/>
	<key>WindowState</key>
	<dict>
		<key>bundleDividerCollapsed</key>
		<true/>
		<key>bundlePositionOfDivider</key>
		<real>0.0</real>
		<key>dividerCollapsed</key>
		<false/>
		<key>eventLogLevel</key>
		<integer>2</integer>
		<key>name</key>
		<string>ScriptWindowState</string>
		<key>positionOfDivider</key>
		<real>416</real>
		<key>savedFrame</key>
		<string>414 1152 700 626 -286 800 1920 1080 </string>
		<key>selectedTab</key>
		<string>description</string>
	</dict>
</dict>
</plist>

```

--- 

