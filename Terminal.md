Links: [[PROGRAMMING]] - [[TECHNOLOGY]]
Rel: [[macos]]
Ref: https://ss64.com/osx

--- 
#### macOS DHCP release renew commands
```
sudo ipconfig set en1 BOOTP
sudo ipconfig set en1 DHCP

sudo ifconfig en1 down
sudo ifconfig en1 up

networksetup -listnetworkserviceorder
networksetup -setbootp Wi-Fi
networksetup -setdhcp Wi-Fi
```

#### calander & pipe to clipboard:
```
cal | pbcopy
pbpaste
```

#### textutil convert filetyle:
```
textutil -convert filetype filename
```

#### defaults:
```
defaults read /Library/Preferences/SystemConfiguration/com.apple.airport.preferences | grep SSIDString
```

####  burn an iso to disk :
```
diskutil list

sudo umound /dev/<identifier> (OR) diskutil unmount /dev/<identifier>
sudo dd if=<path/to/example.iso of=</dev/r<identifier> bs=1m
```