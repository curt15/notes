Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[macos]]; [[linux]]; [[commands]]
Ref: 
Tags: #public 

--- 
dd = heavy-lifting, bit-by-bit copy

```sh

```

if="input file"(source)
of="output file"(destination)
```sh

dd if=/dev/sda of=/dev/sdb

dd if=/dev/sda2 of=~/backup.img # to backup or bootable media

dd if=/dev/zero of=/dev/sdb # copies from a preset bunch of zeros; used to wipe the destination partition 

```


```sh
sudo dd if=/dev/zero of=/dev/sdX bs=1M status=progress
sudo dd if=/dev/urandom of=/dev/sdX count=7 status=progress
```

see also: [[fdisk]]


