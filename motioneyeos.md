Links: [[TECHNOLOGY]]
Ref: https://github.com/ccrisan/motioneyeos/wiki

---


use raspberrypi imager -> 

add **wpa_supplicant.conf** to root 
```
country=US
update_config=1
ctrl_interface=/var/run/wpa_supplicant

network={
    scan_ssid=1
    ssid="MyWiFiSSID"
    psk="S3cr3tp@$$w0rc|"
}
```