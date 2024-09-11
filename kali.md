Links: [[TECHNOLOGY]]
Rel: [[security]]

--- 

ophcrack = a rainbow table tool - avail on this (Debian-derived) distro designed for digital forensics and penetration testing

```
dd if=kali-linux-2020.4-rpi.img of=/dev/disk2





# 
sudo rm /etc/ssh/ssh_host_*
sudo dpkg-reconfigure openssh-server
sudo service ssh restart


# 
sudo adduser alice
sudo usermod -aG sudo alice
sudo pkill -u kali
sudo deluser kali

# 
sudo nano /etc/ssh/sshd_config
# AllowUsers alice bob
sudo systemctl restart ssh

# 
sudo nano /etc/hostname
sudo nano /etc/hosts
# kali -> new_host_name

sudo reboot now
uname -a


############ network ? 
iw dev
ip link show wlan0
sudo macchanger -s wlan0
sudo macchanger -r wlan0 # random
sudo macchanger -s wlan0
iw wlan0 link # check if connected
sudo iw wlan0 scan | grep 'SSID:'
sudo -i
wpa_passphrase ssid_name >> /etc/wpa_supplicant.conf
# enter_psk_into_stdin
wpa_supplicant -B -D wext -i wlan0 -c /etc/wpa_supplicant.conf
iw wlan0 up



#
sudo apt update
sudo apt upgrade


########## tight vnc ?
vncserver
netstat -tupln
vncserver -kill :1



```

--- 
kali_livepersist

[docs](https://www.kali.org/docs/usb/kali-linux-live-usb-install/)

[medium article](https://medium.com/@fatahnuram/creating-kali-linux-live-usb-with-persistence-a-simple-guide-54e3eb01b6aa)

--- 