Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[gitea]]
Ref: 
- https://www.raspberrypi.org/software/operating-systems/#raspberry-pi-os-32-bit
- 
--- 
| ctrl + shift + +/- | 

--- 
1. Raspberry Pi 4 Model B (4GB) + sense hat
- Raspberry Pi OS (32-bit) w/ Desktop 60gb
- 

--- 
1. use Raspberry Pi Imager.app 
2. initial start up (timezone, network, etc.)
3. Preferences > Raspberry Pi Configuration >
- System > Auto login -> Disabled
- Interfaces > VNC -> Enabled
5. create new user & reboot 
```sh
sudo adduser alice
sudo usermod -aG sudo pi alice
shutdown -r now
```
5. log-in as new user -> delete user pi
```sh
sudo deluser pi
```
7. Preferences > Recommended Software -> VNC Viewer



```sh


```

2. 
