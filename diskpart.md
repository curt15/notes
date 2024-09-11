Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[windows]]; [[commands]]

--- 
diskpart - a command-line tool w/ ability to do anything to mass storage (alone=interactive prompt)
diskpart -> list disk (/volume/partition) - shows you all of the disks(/volumes/partitions) available to system
diskpart -> list disk ("Disk 0") - your bootable (bad to F with)
diskpart -> select partition 1 - select a partition
diskpart -> format FS=NTFS quick - format disk as selected File System
diskpart -> assign letter=x - assign a disk/volume/partition to a disk letter