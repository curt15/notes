Links: [[PROGRAMMING]]
Rel: [[macos]]; [[pnano]]
Ref: [applescript key codes](https://eastmanreference.com/complete-list-of-applescript-key-codes) (note: wasn't able to get working && req extra privileges); [Replacing Characters in a String](https://macosxautomation.com/applescript/sbrt/sbrt-06.html) (note: no string interpolation in applescript); 
- https://apple.stackexchange.com/questions/97713/simple-script-for-uri-handling
- https://stackoverflow.com/questions/471581/how-to-map-a-custom-protocol-to-an-application-on-the-mac/3704396#3704396
- https://www.macosxautomation.com/applescript/linktrigger/
- [Terminal do script](https://discussions.apple.com/thread/1903907)
- (Terminal and) [[iterm2]] 's **do shell script**
- [[iterm2]] best = **write text "text"** for executing command in current window (it returns)
Tags: #public 

--- 

-> /Applications/pnano.app/Contents/info.plist
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

```
on open location myURL
	
	set oldDelims to AppleScript's text item delimiters
	set newDelims to {"://"}
	set AppleScript's text item delimiters to newDelims
	
	set pathname to item 2 of the text items of myURL
	tell application "Terminal"
		activate
		do script "/usr/bin/nano " & pathname
	end tell
	
	set AppleScript's text item delimiters to oldDelims
end open location
```

```
on open location myURL
	
	set oldDelims to AppleScript's text item delimiters
	set newDelims to {"://"}
	set AppleScript's text item delimiters to newDelims
	
	set pathname to item 2 of the text items of myURL
	
	tell application "iTerm"
		create tab with default profile command "/usr/bin/nano \(pathname)"
		tell current window
		
			do shell script "/usr/bin/nano " & pathname
		end tell
	end tell
	
	set AppleScript's text item delimiters to oldDelims
end open location
```
--- 

--- 
...

couldn't get keystrokes in [[iterm]] ...

```

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
	
	set cmd2 to "/Users/curtis/prog/.envs/venv/bin/nb-rprint --note=\"" & filename & "\""
	
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
		
		tell current session of current tab of current window
			write text "hi"
			tell application "System Events"
				
				keystroke (key code 4)
			end tell
		end tell
		
	end tell
	
	set AppleScript's text item delimiters to oldDelims
	
end open location
```


--- 
```

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
	
	set cmd2 to "/Users/curtis/prog/.envs/venv/bin/nb-rprint --note=\"" & filename & "\""
	
	
	tell application "iTerm"
		tell current session of current tab of current window
			write text "clear"
			write text cmd2
			split vertically with default profile command cmd
		end tell
	end tell
	
	tell application "iTerm"
		activate
		create window with default profile command cmd
		
	end tell
	
	tell application "iTerm"
		create window with default profile command cmd2
		do shell script cmd2
		
	end tell
	
	set AppleScript's text item delimiters to oldDelims
	
end open location
```

--- 
```bash
	tell application "iTerm"
		tell current session of current tab of current window
			write text "clear"
			write text cmd2
			
			repeat with aTab in tabs
				set profName to profile name of current session of aTab
				if profName is "PNANO" then
				select aTab
				tell aTab to close
				end tell
				exit repeat
			end if
			end repeat
			
			
			
			split vertically with default profile command cmd
		end tell
	end tell
```

```bash
        set foundProfile to false
       repeat with aTab in tabs
            set profName to profile name of current session of aTab
            if profName is "XXXXX" then
                select aTab
                set foundProfile to true
                exit repeat
            end if
        end repeat
        if not foundProfile then
            create tab with profile "XXXXX"
        end if
```


--- 

```set filename to myURL's item i as string if myURL's item i of the text items of myURL ends with ".md"```
```
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
	
	set filename to myURL's item i as string if myURL's item i of the text items of myURL ends with ".md"
	
	set cmd to "/usr/local/Cellar/nano/5.8/bin/nano " & pathname
	
	set cmd2 to "/Users/curtis/prog/.envs/venv/bin/nb-rprint --note=\"" & filename & "\""
	
	tell application "iTerm"
		activate
		create window with default profile command cmd
		
	end tell
	
	tell application "iTerm"
		create window with default profile command cmd2
		
	end tell
	
	set AppleScript's text item delimiters to oldDelims
	
end open location
```

