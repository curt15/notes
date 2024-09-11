Links: [[TECHNOLOGY]]

--- 
Core 2 (220-1002)

Domain 1: Operating Systems
Domain 2: Security
Domain 3: Software Troubleshooting
Domain 4: Operational Procedures


________________________________________________________________
Chapter 1: Safety and Professionalism

Professional Communication Part 1:
(obj 4.7 - Given a scenario, use proper communication techniques and professionalism)
— Be on time - if going to be late, contact the customer
— Actively listening - allow to describe problem in great detail; take notes if necessary
— Clarify customer statements - ask open ended questions to narrow scope of problems
— Maintain positive attitude / project confidence
— Use proper language and avoid jargon, acronyms, and slang
— Set and meet expectations/timeline and communicate status with customer


Professional Communication Part 2:
— Be culturally sensitive
— Use appropriate professional titles
— Avoid distractions when working with customers
— Avoid being judgemental
— Avoid dismissing customer problems
— Deal appropriately with customers’ confidential and private materials
— Don’t argue with customers or be defensive
— Follow up with customer later to verify satisfaction
— Provide proper documentation on services provided
— Offer different repair/replacement options


Physical Safety:
(obj 4.4 Explain common safety procedures)
— Disconnect power before repairing PC
— Equipment grounding
— Remove jewelry
— Fire extinguisher - 
	- (A) Wood fires
	- (B) Grease fires
	- (C) Electrical fires - Electrical Fire Safety - have one of these
— Lifting techniques
	- lift with legs, not back
	- Weight limitations: 25 pounds or more needs assistance - OCEA rule
	- clear away debris
	- use hand truck
	- call for help

** quiz - What can have a negative impact in a wireless network environment? RFI - Radio Frequency Interference (RFI) can interfere with wireless signals.
	- Which is not a good way to prevent or reduce ESD? Antistatic Toolkit - no such thing

________________________________________________________________
Chapter 2: The Visible Computer

What is an Operating System?:
(obj 1.1 - Compare and contrast common operating system types and their purposes)
— “a program to run all of the programs”

— Kernel - core part of OS that handles primary memory management
	- Resource Monitor
	- Process ID - every program gets unique

— OS knows how to talk to a specific type of CPU
	- specific amount of wires on bottom of CPU designated to talk to memory
	- today 64-bit is most common, 32-bit less
	- specific version of operating systems to deal with this

— Hardware 
	- device drivers - software used by the OS to control computer components (hardware)
	- Device Manager

— Storage
	- File Explorer
	- heirarchial organization of data - folders & files

— Networking
	- Control Panel -> Network and Internet -> Network Connections


Users and Super Users:
(obj 1.5 Given a scenario use Microsoft operating system features and tools)
— User account - Database of names/passwords
— Super user or administrator account - account that allows higher levels of control

— every computer in existance has a user system
— every computer in existance has some type of super user accounts

— The Windows super user is called Administrator
— The Linux and macOS super user is called Root


Why Windows?:
(obj 1.1)
— Per Processor Agreement - Bill Gates gave copy of Windows to every Intel processor purchase

— Networking - accessing resources from a different computer on your network requires your user/password on the other computer to access
	- Domain - (Active Directory) - Windows Server - an OS that sets up a:
	- Domain Controller - allows Single sign-on (SSO) - login to any computer 
	- Linux and macOS systems has SSO features to login and act as a Windows
		- macOS - File Sharing and Print Sharing
		- Linux - Samba
	- Windows owns the SSO concept
	- important in enterprise environments
— UAC (User Account Control) - prevents usage of powerful programs by users with limited permissions


Windows Editions and Versions:
(obj 1.2 - Compare and contrast features of Microsoft Windows versions)
— Editions
	- Home edition - homes and small offices
		- can’t join a windows domain
		- often come with media tools, etc
	- Pro versions
		- basic tools to do whatever need to do
		- always have ability to join Domain
		- ability to take advantage of CPU power
	- Enterprise edition 
		- can’t buy from local stores
		- volume discounting
		- features to take control of tens to thousands of computers

— Versions
	- Windows 7
		- Media Center - don’t confuse with Media Player
			- last version to have this
		- Control Panel - single source to change things
		- start button and task bar
	- Windows 8
		- unveiled to be used on more devices (smart phones, tablets)
		- has task bar, no start button
		- Microsoft Store
		- Charms bar - introduced new Settings function
			- still has Control Panel, but now split
		- OneDrive - Cloud storage
	- Windows 8.1
		- adds back start button
		- still no one was a huge fan of Windows 8
	- Windows 10
		- Charms bar is gone
		- Start menu - tiles are now here
		- Settings button - more complicated settings, Control Panel almost unnecessary
		- right click on start button
		- Media Center unavailable


Touring the macOS:
(obj 1.1)
— Apple menu - far left on top bar - changes based on application open
— Status menu - far right on top bar
— Dock - programs you use the most
— Finder - folder contents on system
— System Preferences - equivelent to Settings/Control Panel
— Terminal - Unix commands
— Command-q used to fully quit application

Touring Linux:
— often found in routers, raspberry PIs, Android Phones
— Absolutely free
— Linux = Kernel of the operating system
— GNU licence - freeware - allows people to write linux kernel to connect to a hard drive or desktop environment
— Distro - packaged Linux distributions (e.g. Raspian for RaspberryPi)

— Ubuntu - most commonly used distro
	- Dash - equivalent to Windows Task Bar
	- can open multiple desktops
	- Terminal - everything critical done through command prompt
	- not a lot of penetration from the desktop
— Fedora Linux distro -
	- KDE desktop environment
— GNOME - only real alternative to KDE
— Linux Mint Distro
	- Cinnamon environment
	- gives look and feel of Windows


________________________________________________________________
Chapter 3: CPUs

32-Bit vs. 64-Bit Processing:
— modern CPUs have thousands of wires/contacts
— CPU must grab lines of code from RAM
— Job of motherboard is to connect external data bus to everything
— 8-bit allows 8 lines of binary code
— MCC (memory contoller chip) - additional chip or built into CPU these days
— Address bus - direct connection between MCC and CPU to allow CPU to ask for specific line of code from memory needed - not used to move data
	- 16-bit = 00000000000000000-1111111111111111; 2^16 = 65,536 bytes of RAM accessible
	- 32-bit = 2^32 = 4,294,967,296 bytes = ~4GB RAM
	- 64-bit = 2^64 = 1.844x10^19 bytes
	- 32-Bit processors won’t see/use more than 4GB RAM
	- 64 bit gives more memory

** exam tip: make sure to use correct version of OS - every OS will show you what you have
	- x86 denotes 32-bit CPU
	- x64 denotes 64-bit CPU

— software comes in 32/64-bit versions - can install 32-bit versions of software on 64-bit Windows
	- A 32-bit application can’t use more than 4GB of RAM
	- e.g. Office 365 better for compatibility to install 32-bit version by default

— 32-bit is alive and well, but more specialized 

________________________________________________________________
Chapter 4: RAM

Virtual Memory:
(obj 1.6 - Given a scenario, use Microsoft Windows Control Panel utilities)
— 2GB for Operating system (Windows)
— Small applications vs Graphics programs - use more/less RAM
— Out of memory error
— Virtual memory - allows OS to use part of hard drive as memory
	- better to have the amount of RAM you need

— Control Panel -> System Properties -> Advanced Properties -> Performance Options -> Advanced
	- shows amount of hard drive allocated for virtual memory
	** Exam tip: Automatically manage paging file size for all drives - 
		- paging file = part of hard drive the OS thinks is RAM
		- set to automatic
— Command Prompt
	- dir /ah - show me everything that has the attribute of hidden
	- swapfile.sys - size shows currently allocated; generally smaller than shown in above
		- Swap file = virtual memory

— Computer slows down when using virtual memory
— Should only be used when physical memory is exhausted
— Generally reccomended to let the OS manage the size of the virtual memory file
— Best answer for performance is to add RAM


________________________________________________________________
Chapter 7: Power Supply

Power Protection:
(obj 4.5 - Explain environmental impacts and appropriate controls)
— Spikes and sags - power over time from power company is SIN wave
	- 120 V
	- 60 cycles/second = 60Hz (US standard)
	- Sag = Short term voltage dip - often get < 120 V (transformer down, etc.)
	- Brownout = Intentional or unintentional drop in voltage
		- can keep computer from running / cause reboots
	- Spikes = Provided more voltage than what you’re expecting
		- can get 300 V suddenly
		- can destroy your computer 
	- Sag and brownout = same thing
	- Spike and surge = same thing

— Surge suppressor/protector - catches surge and eats higher power
	- Trip alert - shuts off power
	- Ethernet cabling, landline, and USB surge suppressors exist
	** don’t worry about UL ratings
	- downside to cheap - will be a good surge suppressor once, then becomes a power strip
	- use with: flatbed scanners, printers, etc. - anything cheap

— UPS (uninterruptable power supply) - protects from spikes/surges AND sags/brownouts
	- UPS batteries - pick up where power company isn’t providing
	- often have a UPS side and simple surge protector side
	- tools exist that show available power
	- APS website will show how much time system can be powered down
	- use with: any other system

— A power supply has a built-in surge suppresssor, but also provides power to the computer
	- doesn’t protect from sags or brownouts


________________________________________________________________
Chapter 9: Implementing Mass Storage

Understanding Partioning:
(obj 1.3 - Summarize general OS installation considerations and upgrade methods)
— turning a physical hard drive into a logical electronic device readable by an operating system
	- gives “rooms” that can be used 
	- Swap partition - used in Linux to be able to use virtual memory vs Windows that creates files
	- Recovery partition - holds back ups of OS

OSes themselves make partitions:
— 1. Tool/utility used to create partitions
— 2. Mount partitions
	- Windows - manefest as drive letters with a colon (C:, D:, E:, etc.)
	- macOS/Linus - manifest as a directory tree aka folders (/, /cdrom, etc.)


MBR Partitioning:
— Master boot record (MBR) - the oldest type of partition still used today - defines partitions and shows computer where to find OS.
— Happens on a very particular area of hard disk:
	- LBA 0 - specific sector read first in boot order (assuming drive is first)
		- boot loader - first code read off of mass storage -
		- points to the beginning of one of partitions on partition tables
		- boot loader is assigned an active partition
		- Max 2 TB per partition
		- Limited to 4 partitions

— Windows 7 - (most modern versions don’t do MBR well)
	- Disk Management - set up disks for MBR (or GUID)
		- “New Simple Volume”
			- define amount of space you want to use
			- Assign Drive Letter or Path
			- go through Formatting
			- updates the partition table so Windows sees new “E:” or whatever drive
			- can partition here to multiple drive letters

— Primary partitions - MBR’s allowd 4 partitions
— Extended partitions - allows logical drive letters beyond the 4
	- Logical drives
	- visible by different colors

— 2 TB limits became a problem leading to GPT partitioning


GPT Partitioning:
— GUID Partition Table (GPT) - designed to take advantage of the power of UEFI BIOSes to provide a broad cross section of advanced features
— (GUID) Global Unique Idenfitier - 128-bit value that defines your unique partitioning table
— 128 partitions per/drive - term used is “volumes” - no longer primary/extended partitions
—  18.8 million terabytes/partition
— Windows 10 used GPT, no longer MBR - but backwards compatable
— “Protective MBR” - used when plugged into older systems - will give warning that cannot read LBA partitions so doesn’t instantly erase it
	- piece of info part of MBR that says “I’m a GPT!”
		- so a GPT capable system will ignore the first part and go to partitions themselves
	-> LBA 1 - Primary GPT Header
	-> LBA 2 - Secondary GPT Header - back up of primary

— Windows 8.1 - (GPT works exact same in 10)
	- Disk Management
		- (Windows 8.1 still allows to set drives up as MBR)
		- New Simple Volume
			- works the same as previous MBR set-up


Understanding File Systems:
— File Allocation Table - keeps track of things LBA by LBA basis where things are on a partition
	- FAT16 - 
	- FAT32 -

— part of format process queries each LBA block to see if can read/write data and replaces value on bad block with hexadecimal value to denote to not use
— large files fill up multiple blocks and reference down the table to others that reference different pieces of same file. Last block ends in “FFFF” to denote end of file.

— Fragmentation 
	- occurs when file is deleted 
	- file allocation stays the same
	- in directory where file was saved, first letter of file name changed to a lower case sigma
	- denotes blocks available to be written over
	- writing a new file, overwrites
	- if larger than the old file, allocation jumps from writing to these to new blocks
	- in order to get to file, will need to go all over hard drive to get it
	- especially a problem with HDDs


Popular File Systems:
— FAT32 - old
	- supports up to 8TiB volumes
	- each file can be up to 4TiB
	- works on small drives

— NTFS - new technology file system
	- Massive volumes up to 16 EiB
 	- Individual files up to 256 TiB
	- MFT (Master File Table) - vs FAT
		- sits in middle of volume - impossible to erase
	- u.c. Compression
	- u.c. Encryption
	- Security - has the de facto standard for individual and network system security on all OSes

— ExFAT - between FAT32 and NTFS - better for smaller drives (e.g. Thumb drive)
	- supports the same NTFS sizes
	- Less overhead - not really compressable/encryptable

— CDFS (Compact Disc File System)
	- works on CDs, Blu-rays, DVDs etc.
	- u.c. Optical
	- individual files up to 4 GiB

Linux has vast file systems available. Need these 2 for exam:
— ext3
	- supports 32 TiB volumes
	- supports 2 GiB files
— ext4
	- supports 2 EiB volumes
	- supports 16 TiB files


— HFS+ (Heirarchial File System Plus) - macOS exclusive
	** exam objective says HFS, but this has been obselete for 20+ years
	- supports 8 EiB volumes and files

** CompTIA exam probably not going to test on exact numbers, however, need to understand why you would use something (e.g. setting up a Windows OS, use NTFS)


Formatting in Action:
(obj 1.2)
Windows 10:
— Disk Management ->
	- Initialize Disk - join new disk to the system
	- “New Simple Volume”
	- can mount to an empty NTFS folder vs assigning a drive letter
	- Format Partition
		- NTFS or exFAT
		- if small, FAT32 can show up
		- “Allocation unit size:” - set to default
		- “Volume label:” - whatever you want
		- “Perform a quick format” - will build data structures but won’t test
		- “Enable file and folder compression” - can always do later
— with a USB drive - right click -> “Format…”
	- Window’s determines file system type by size of drive
	- wan’t less overhead of file allocation tables with smaller drives
	- default will be most efficient choice
	- erases everything

Ubuntu Linux:
— Disks (default tool in Ubuntu, tons exist) ->
	- “Format Partition…” - give name, choose to erase
		- “Internal disk for use with Linux systems only (Ext4)”
		- “Password protect volume (LUKS)” - a convenient time to do so
		- can partition as NTFS, FAT, other


Dynamic Disks:
(obj 1.5)
— Dynamic disks - unique to Windows - allows features like shrink or expand (vs. basic disk)
— happens automatically if selecting to use advanced features

— “Extend volume…” - keeps data intact
— “Shrink volume…” - queries volume to see where data is and how much it can shrink
— Spanned volume - can take 2 or more and OS looks at as a single drive
	- never do it - fills first drive first, then another
	- only time is if fill a drive; temporary fix until you can get a bigger drive
	- bad because now you have 2 points of failure
— “New striped volume…” - 2 drives that act as 1 drive (RAID 0)
	- allows to save data quickly
	- downside: if you lose 1 drive you lose everything
— “New mirrored volume…” - copy on 2 drive
	- if 1 dies, data still accessible

reccomended best practices:
— 1. Keep the boot drive basic (not dynamic)
— 2. Set boot drive to GPT - gives more features/flexability
— 3. Easy to create dynamic drives - but if you switch back to basic you lose data 


Software RAID in Storage Spaces:
— Windows allows easy RAID 0 (striped volume) and RAID 1 (mirrored volume) through software in Disk Management

— Storage settings -> Storage Spaces - allows RAID 5
	- “Create a new pool and storage space”
	- pool - like an array, preassigned drives that work together to do something
		- “Resilency type:”
			- “Simple” - create normal drives
			- “Two-way mirror” - allows to set pool size to whatever, even above available
			- “Parity” = RAID 5 - requires 3 drives
			- “Three-way mirror” - requires 5 drives
				- Microsoft’s proprietary RAID
				- can use different size drives without producing wasted space
				- can lose 2 of any drives and be okay

— Disk Management - sees end result of array from Storage spaces as a single drive
— Downside of software RAID - can slow down system vs hardware RAID


Encrypting Mass Storage:
(obj 1.2)
— File-based encryption - software feature of OS to encrypt particular file or folder
— Encrypting File System (EFS) - on Windows, built-in to NTFS
	- right click on file/folder -> Properties -> Advanced -> “Encrypt contents to secure data”
	- anytime you log in will decrypt for you
	- even law inforcement (as far as known) can’t crack
— No built-in tool in macOS
— tons of options for Linux

— Disk-based encryption - software feature of OS to encrypt entire drives
— BitLocker - used in Windows
— FileVault - macOS
— Linux has tons available
— Trusted Platform Module (TPM) - manefests as a chip on motherboard - robust key built-in
	- must make sure it’s turned on
	- (on Windows) System Setup
		-> Trusted Computing - Enable
	- System and Security -> BitLocker Drive Encryption
		- won’t work unless TPM turned on
		- can encrypt only where files are stored or entire drive
		- saves key to different drive
		- New encrypted mode vs Compatible mode (for installing drive back to old devices)
		- can turn on BitLocker without TPM (thumb drive) - choose complicated password


________________________________________________________________
Chapter 11: Building a PC

Boot from Everything:
(obj 1.3)
— ISO Images - perfect copy of OS that was originally optical media
— Burning - the process of getting an ISO onto the device
	- USB thumb drives, optical media, SD cards

— Network -> name -> Software -> Microsoft OS and Office ISOs
	- view -> options -> view-> uncheck “Hide extensions for known file types”
	- right click on ISO and select “Mount” - shows actual files setup and ready to install
	- “Unmount” / eject
	- right click on iso and select “Burn disc image” - will automatically make an installation disk

— Rufus - freeware to burn an ISO to a thumb drive
— make sure to change boot order to boot from the thumbdrive / optical media

— PXE booting and Apple Netboot - allows booting from a network - select network ID

— (on Windows) Control Panel -> All Control Panel Items -> Recovery
	- plug in a thumb drive
	- “Create a recovery drive” - (check “Back up system files to the recovery drive”)
	- allows to boot from Windows Re in case something goes wrong


Installing Windows:
— Preinstallation
	- check minimum hardware requirements for OS
	- 8 GB RAM (reccomended)
	- 250 GB hard drive (reccomended)
	- Hardware compatability list - research online
	- Enterprise - hardware manufacturers will work with you to verify

— Know your network
— Know your domain name
— Know the local account names
— Know your Microsoft account

Installation:
— Change language, time, currency, keyboard formats
— Install now (“Repair your computer” available on this screen)
— Type Windows product key (can get around momentarily; certain time allowed for unlicenced copy)
— Select the operating system you want to install
— Agree to Applicable notices and licence terms (“If you ever get a chance, read them. They’re absolutely terrifying.”)
— “Which type of installation do you want?”
	- Upgrade: Install Windows and keep files, settings, and applications
	- Custom: Install Windows only (advanced) = clean install
— Choose drive
— Wait through a few reboots while installs
— Choose region
— Choose keyboard layout
— “How would you like to set up?” - personal use / for an organization
	- he chooses organization even at home for added features
— “Sign in with Microsoft” - click “Domain join instead” - even if not joining a Domain
	- allows you to create a local account (vs an online account)
	- choose name & pass
	- create security questions
— “Make Cortona your personal assistant?” - “Well, I’m not playing Halo, so I’m going to decline.”
— “Choose privacy settings for your device”
	- telemetry settings (location, cortana stores voice info, tailored ads,
	- he chooses No for everything
— Networks - allow your device to be discoverable


Post-Installation Tasks:
— Device Manager
	- stuff on motherboard that Windows doesn’t recognize
	- install from motherboard optical media (or go online for more recent drivers)
	- pro tip: don’t install the browser or whatever other garbage included in these installs
	- update drivers for video cards (go to manufacturer for latest)
	- check back here to make sure everything is good

— System Settings -> Update & Security
	- “Change active hours” - choose when you don’t want updates (restarts)
	- can choose automatic download updates (OS and/or MS software) and notifications
	-> Advanced options
		- “Show a notification when your PC requires a restart to finish updating”
		- can pause updates - on Windows you cannot choose to NOT update unless Enterprise

— Control Panel -> Recovery
	- Recovery disk - personal copy of Windows installation media
	- looks for a flash drive (16GB minimum)
	- Windows system properly installed w/ device drivers, updating, but no applications

— Control Panel -> System Properties -> System Protection
	- Restore point - snapshot of system as it currently is
		- preserve applications, drivers, the registry, and other critical system files
		- not user files!
	- before creating a restore point, System Protection must be enabled
	-> “Configure…” - turn on and set up drive space
	-> “Create…” - give descriptive name

— Settings -> Windows Security
	- Windows 10 today comes with anti-malware installed, on, and working properly
	- has a firewall set up by default too
	- just a check on post-installation

— Control Panel -> System and Security -> File History
	- File history - allows you to keep back up copies of any changes on a file-by-file basis
	- off by default


Windows Installation options:
— Clean install - blank storage, put in installation media, and install
— Upgrade install - already have Windows 7/8.1 and upgrage
	- an upgrade keeps applications, sign-on, desktop setup
	- if you have an older home version - upgrades to Windows 10 Home
	- older pro version -> Windows 10 Pro
	- upgrading from Windows 7 Home -> Windows 10 Pro requires clean install

— Multiboot - support multiple OSes on a single drive
	- need extra hard drive or unpartitioned space on primary drive
	- when booting up, will get a “Choose an operating system” screen
	- e.g. Windows Server + Windows 10

— Unattended installation - used when setting up a ton of computers at once, but allowing some flexibility to users on certain things depending on needs (e.g. choosing user/password)
	- answer file - generated to answer installation questions; only pops up whats necessary
	- Windows System image Manager - free tool to generate answer file
		- creates autounattend.xml
		- drag and drop into installation media (root)
		- on boot will automatically skip prewritten question answers
— Image deployment - distribute a single system image to multiple identical systems
	- when setting up multiple computers - hardware must be identical
	- can set up a single laptop w/ applications, domain, firewall settings, etc.
	- then using a network, can distribute that single image to all laptops
	- User State Migration Tool (USMT) - Windows’ solution to this
		- often use 3rd party tools (e.g. Ghost)


________________________________________________________________
Chapter 12: Windows Under the Hood

What is the Registry?:
(obj 1.5)
— The Registry stores Windows settings - internet address, users & passwords, desktop, software installed, etc. 
	- Registry Editor (regedit.exe) - application to manipulate binary Registry files
	- Linux stores this in text files (billions)
	- Windows cannot boot without the Registry

— regedit
	- organizes all Registry data into 5 root keys:
	- HKEY_CLASSES_ROOT - what everything in computer defined to be able to do
		- what application used to open file extension types & info on what type of info
		- can manually change icons here
		- area least often entered - complicated
	- HKEY_LOCAL_MACHINE - defines settings for the computer
		- drivers, hardware, software, screen saver, etc
		- shorthand = “HKLM”
	- HKEY_CURRENT_CONFIG - defines what aspect of system hardware are being used now
		- different users have different settings taking advantage of hardware in different ways
		- is a subset of hkey_local_machine
	- HKEY_USERS - lists all users on machine
		- defines how console is set up, device drivers, keyboard layout, etc
	- HKEY_CURRENT_USER - info of user currently logged in
		- is a subset of hkey_users
	- deeper settings:
	- HKEY_LOCAL_MACHINE -> SOFTWARE -> Microsoft -> Windows -> CurrentVersion
		-> Run - anything that autostarts on computer here
			- to add: right click - “New” - “Key” - choose type - right click - “Modify..”
			- CompTia doesn’t expect, but good to know where is later as tech
		-> RunOnce - runs itself and then removes
		- can make a copy of pieces of registry: right click on folder - “Export”
			- important to to keep original copy when mainpulating
			- if problem occurs, right click on folder - “Merge”
			- if making changes and works great - can use export on other machines

— The registry files are stored in C:\\Windows\System32\config


Processes:
— Applications - stuff in a window, running in the lower right corner; can see and deal with
— Services - stuff running in the background
— Apps + services = processes - 2 discrete groups of things running on a computer; take up memory

— Task Manager -> “Details”
	- PID = Process ID
	- right click on process
		-> “End task” - can be dangerous to arbitrarily end processes
		-> “End process tree” 
			- running programs require external libraries for things like scroll wheel
			- .dll (dynamic link libraries) or .exe stores this inherent information
			- or things like networking tools rely on others to do things
			- Dependancy heirarchy

— Process Explorer - 3rd party software
	- shows process tree nested in window


Services:
— Services - program that comes with Windows to manage services (group of processes)

— “Status” - shows blank or running
— right click on individual service
	-> “Properties”
		- “Startup type:” Manual, Automatic, Disabled
		- can start/stop services here
		- sometimes can’t see started service on Task Manager…
		- because part of a service host - single .exe that runs multiple services


Your Windows Toolset:
(obj 1.6)
— Right-click on an object to view its context menu

— Control Panel
	** CompTIA exams assume Large icons view for Control Panel
	-> Administrative Tools 
		-> System Configuration - boot up configuration stuff
			- can uncheck certain services and applications from starting up

— Settings - a lot of overlap with Control Panel
	- often pushes you to a Control Panel applet

— Tons of ways to get to the same things. Can always just use search bar, type in name of tool you’re looking for, and pops right up.

**exam tip: not going to test you on which buttons to click to get to where (some hotkeys)


Windows 7 Task Manager:
(obj 1.5)
— “thermometer / blood pressure meter of your system”
— hotkey = “Ctrl + alt + del” or “Ctrl + Shift + Esc”
— 6 tabs:
	- Applications
	- Processes
	- Services
	- Performance - overview of how system is running (memory)
	- Networking - rough idea of how hard network is using
	- Users - who is currently logged in

— Resource Monitor - tool for more granular view - get to through Performance tab
	** pro tip: in Windows 7 this is the only place to get the process ID (PID)
	- see everything reading + writing to disk
	- Pages - allocation of memory 
	- Hard fault - program uses hard drive as memory when RAM out of pages
		- lower hard disk faults/s not a problem; hundreds = not enough RAM 
	- CPU - shows percentage of CPU usage by Processes and Services


Windows 10 Task Manager:
— same shortcuts as before + right-click on Windows key -> “Task Manager”
— shows percentage of CPU usage overall and by process
— right-click on individual service for properties, file location, etc.
— Performance - shows typical Resource Monitor stuff
— go to Resource Monitory to see more granular stuff (e.g. what individual cores are doing)

— Background processes are services
— Windows 10 Task Manager is split out into Processes, Performance, App History, Startup, Users, Details, and Services


Information and Configuration Tools:
— System Information (msinfo32) - old information tool
	- BIOS version, processor info, RAM amount, etc.
	- System Summary is convienient, other tabs less used
	- use to get a quick snapshot

— System Configuration (msconfig) - 
	- General - startup selection
		- Selective startup - useful when diagnosing issue from background service vs item
	- Boot - Safe boot - turns off complex device drivers, virtual memory, high-end video, etc
		- Network - same as Minimal (above), but allows network card for internet access
		- Active Directory repair - reestablish connection to server (**exam)
	- Tools - directs you to other stuff

— Control Panel -> System
	- important place for info and configuration
	- Windows version
	- change name
	- input product key
	-> System protection - create/edit restore points
	-> Advanced System settings = same window as System protection, gives differen tab
		- virtual memory settings
		- Data Execution Prevention (DEP) 
			- programs require memory allocations (called pages)
			- unless specifically need to, don’t let programs stomp on others
			- stops exploit that might crash system
			- by default, leave DEP as is and don’t mess with

— Microsoft Management Console (MMC) - allows creation of custom tools/utilities
	- Add or Remove Snap-ins
		- e.g. make a utility to open Disk Management & Device Manager at the same time
		- file, save as, “ “.mcc


Performance Monitor:
— Performance baseline - gives an idea of how well computer runs before installing stuff (e.g. Steam games) that slows a system down

— Performance Monitor - tool to do this
	- realtime mode - see how it’s doing at the moment
		- Counter
			- shows %Processor Time over time
			- can “Add Counters”
				- %User Time
				- LogicalDisk - counter that shows individual disk usage
					- Avaliable MBytes
			- can change colors of counter graphs
			** exam won’t ask you what counters show what
	- Data Collector Sets - user defined set of counters
		- Create data logs
		- choose intervals
		- cyclic logs - write over old stuff at a certain size
		- Reports - shows results
		- preset data collector sets - System Diagnostics & System Performance


Event Viewer:
— default events that Windows logs:
— 1. Applications - anything happening within an application itself that may be of interest
— 2. Security - log on/off
— 3. Setup - initial set up of Windows and updates that take place
— 4. System - Windows core system itself - often where you go when things “blow up”
	- Event Log Online Help - to give you information about errors
	- often much better to just cut and paste into search engine

— Audit policy - custom event logging
— Local Security Policy - software to set up an audit policy
	- 2 programs in one:
	- Sets up the policies for the system 
		- e.g. complex passwords required, 3x incorrect passwords disables account
	- Adjust Audit Policy in Local Security Policy 
		- certain events not on by default that you want logged
		- e.g. “Audit account logon events” - Success/Failures
		- e.g. “Audit account management” - creating users / changing permissions


Tools for Programmers:
“The bane of my existance are these people called programmers. Programmers are evil, terrible people, and they sleep in basements, and they eat junk food…”

—  Structured Query Language (SQL) - type of computer communication allowing apps to talk to databases
— Open Database Connectivity (ODBC) - allows application to link to the database
	- creates a standard linkage format
	- e.g. local & remote sales computers accessing database of Inventory, Pricing, etc.

— ODBC Data Source Administrator - tool comes standard on Windows
	- “System DSN” -> “Add”
		- select your SQL server
		- “Create a New Data Source to SQL Server”
			- “Name:” - given by people who wrote program
			- “Description:” - doesn’t matter
			- “Server:” - given
			- Give other info given by programmers -> Finish
	- usually handled through installation

— Component Object Model (COM+) - allows to share databases and more
	- e.g. bits of files stored on one server passed to everybody
	- if developing a program, don’t have to write every piece, puts all together
	- developed by Windows (pretty much exclusive used by Windows)
— Component Services - builtin tool for COM+
	-> “COM+ Applications”
		- right-click -> “New” - create a new application
			- library or server application
			- set how to login
			- define roles (who can delete database, etc.)
	- “You won’t ever go into Component Services without a programmer on the phone with you”
	- important to have some comfort with the interface


________________________________________________________________
Chater 13: Users, Groups, and Permissions

Introduction to Users and Groups:
(obj 2.6 - Given a scenario, use Microsoft operating system featurs and tools)
— NTFS (New Technology File System) 
	- NTFS permissions - allows granular control of shared drives, folders, documents
		- e.g. read only, add files to folder only, access folder but no view of contents, etc.
	-  Allow vs. deny - right-click on items -> “Properties” -> “Security”

— Users and groups
	- bad idea to apply permissions to user accounts
	- e.g. Janet quits, now Jane needs access, better to assign a group
	- a group is a container for user accounts
	- can give specific access to groups
	- individual user account can be a part of multiple groups
	- can have groups within groups


Managing Users and Groups:
3 places to do this:
— Settings -> Accounts
	-> Other people 
		- create a new account
		- change account type
			- Administrator vs standard user - built in groups to Windows

— Control Panel -> User Accounts
	- provides more account control
	- change account name (yours)
	- change account type (yours)
	- add a new user account
	- change account type (administrator vs standard user)


— Local Users and Groups
	- one of oldest applications in Windows
	- provides the most control over users and groups
	- Control Panel -> Administrative Tools -> Computer Management
	- default accounts exist - downarrow on icon denotes deactivated
	- Guest account
	- Power Users - one click beneath Administrator account
		- can’t take control of other user accounts stuff
	- Performance Log Users, Performance Monitor Users, Backup Operators, etc.
		- groups used by programs
		- e.g. running Performance Monitor allows users to view info for whole system
	-> “New User…”
		- give user name, full name, description, password
		- can set password expiration
		- can disable account - if someone quits, don’t want to delete
		-> right-click on individual user -> “Properties” -> Member Of - select groups
		-> right-click in Groups -> “New Group…”
			- give group name, add members
	

NTFS Permissions:
(obj 2.6 - Compare and contrast the differences of basic Microsoft Windows OS security settings)
— NTFS permissions don’t care if you’re logging into the system locally or on a network.
— You can’t get to the resource on a network without a second step to share on network
	- (covered in a later section)

— right-click on item (files, folder, etc.) -> “Properties” -> “Security”
— Full Control
	- on folders - Enables you to do anything you want. (e.g. change name, read, write, delete)
	- on files - Enables you to do anything you want to the file.
— Modify 
	- on folders - Enables you to read, write, and delete both files and subfolders.
	- on files - Enables you to read, write, and delete the file.
— Read and Execute 
	- on folders - Enables you to see the contents of the folder and any subfolders as well as run any executable programs or associations in that folder.
	- on files - Enables you to open and run the file.
— List folder contents - Enables you to see the contents of the folder and any subfolders
— Read - Enables you to view a folder’s contents and open any file in the folder.
— Write 
	- on folders - Enables you to write to files and create new files and folders.
	- on files - Enables you to open and write to the file.

— choose permissions to give specifically to the selected user
— Inheritance - if you put a file or subfolder in a folder, it will take on same default NTFS permissions
— Allow vs. deny - stop inheritance - can select “Deny” in the same window

** exam doesn’t go into detail about needing to know every detail of these NTFS permissions


Linux and macOS Permissions:
(obj 1.9 - Given a scenario, use features and tools of the Mac OS and Linux client/desktop operating systems)
— Owner, group, and everyone 
	- owner - person that created and saved the file
		- R W X - read, write, and execute privileges
			- execute allows you to run script files
			- for things like word processing documents, don’t need/want execute
	- group - owner can set specific R W X for people in specific group
	- everyone - owner can set specific R W X permission to everyone

— (on Linux:) right-click on file/folder -> “Properties” -> “Permissions”
— (on Mac:) right-click on file/folder -> “Get Info” -> “Sharing & Permissions”


File Explorer:
(obj 1.6)
— primary tool to look at files and folders on a system
— quick launch from task bar or type “file explorer” into search

— Navigation pane - left
	- Quick access - Desktop, Downloads, Documents, and stuff you’ve clicked on a lot
		- right-click on file/folder to put into quick access
		- pinned items will always be there
	- This PC - computer itself
		- right-click on This PC -> “Properties” = great way to get to system information
		- Drives
	- Cloud services - e.g. OneDrive account will always be here
	- Network - access shared folders/files on network
— Preview pane - right
— Details pane - right

— can change icons, details, 
— View options - “View” -> “Options”
	-> General (General options)
		- “Open File Explorer:” - This PC / Quick access
		- open folders in same window or it’s own
		- single/double click to open an item
		- Privacy - show frequently/recently used files/folders in Quick access
			- Clear File Explorer History
	-> View
		- Show hidden files, folders, and drives
		- Hide extensions (for known file types)
			- File associations - “all files with extension open by default with this application”
				- can change under file Properties
		- Hide protected operating system files (Reccomended)
		- can choose to apply these settings to all folders
	- Attributes - settings you can apply to a folder/file to define interesting aspects
		- (set for items under General)
		- Read-only - cannot be deleted
		- Hidden
		- more attributes… (-> “Advanced”)
			- File is ready for archiving
			- Allow this file to have contents indexed in addition to file
				- on by default - allows easier searching
			- Compress contents to save disk space
			- Encrypt contents to secure data
— Manage
	- option menu at top when highlighted on an executable
	- e.g. “Run as administrator”, “Troubleshoot compatability”


Sharing Resources:
(obj 1.8 - Given a scenario, configure Microsoft Windows networking on a client/desktop)
— Microsoft LAN Manager - predates Windows - tool used in “operating systems of your forefathers with names like DOS” - installed to look at other peoples hard drives
	- lives and breates on Windows today

— NTFS vs. share permissions
	- NTFS has no networking function built into it
	- Network shares - advertise out to network that particular folder is available
		- then have access based on NTFS permissions
	- Universal Naming Convention (UNC) - \\name_of_serving_machine\thing_shared
	- network shares doesn’t care what file system is (NTFS, exFAT, etc.)

— right-click on file/folder -> “Give access to” -> “Specific people…”
	- Read vs Read/Write
	- can choose “Everyone” - anybody who can get to system via the network has access
	- Microsoft best practices says: if you’re going to share something leave it wide open and use good NTFS permission control to limit what people can do.

— File Explorer -> Network
	-> individual system - will show network shared folders
	- Mapping drives - right-click -> “Map network drive…”
		- give it a drive letter
		- choose to reconnect at sign-in
		- can choose to Connect using different credentials
			- allows connection on different machines


Security Policies:
(obj 1.5)
— Local Security Policy - application used to set up device specific policies
	- Account Policies
		- Maximum password age - how long allowed before change required
		- Minimum password length
		- Password must meet complexity requirements - upper&lower alpha + numeric
		- Enforce password history - can’t reuse x number of previous passwords
		- Store passwords using reversible excryption - allow easier to crack passwords
		** on exam
	- Account Lockout Policy
		- Account lockout threshold - set num of incorrect password attempts
		- Account lockout duration - time locked out after incorrects 
		- Reset account lockout counter after 
			- certain amount of time at x/max incorrect attempts before reverts to zero
	- Local Policies
		- Audit Policies - already covered
		- User Rights Assignment - things like “Allow log on locally”
		- Security Options - things like “Rename administrator account

— Domain policies - administrator of domain can overwrite local security policies applied to groups


________________________________________________________________
Chapter 14: Maintaining and Optimizing Operating Systems

Patch Management:
(obj 2.7 - Maintaining and Optimizing Operating Systems)
— updating built-in software to ensure they are the safest and most stable they can be
— enterprise environments often requires a form and committee

— Windows Update (in Windows 7)
	- Control Panel -> System and Security -> Windows Update
	- Check for updates
	- KB values give details about updates
	- Windows 7 has 2 categories of updates: Important and Optional
		- Important = Critical updates
	-> Change settings
		- install updates automatically, choose when to install, check but let me choose, never
		- choose when to install
		- can choose Give me reccomended updates the same way I recieve important updates
		- can choose Allow users to install updates on this computer
		- MS products (Office, etc) can choose here
		- 3rd party tools (e.g. Adobe) sometimes have their own update utility
		- device drivers - have to go to site to see if update
		- Firmware - Update the System Setup BIOS

— Windows Update (in Windows 10)
	Settings -> Windows Update
	- choose active hours - “don’t update during this time”
	- see update history
	- can Uninstall updates
	- Recovery options - back out of updates in one big shot
	- no option in Windows 10 to choose updates
	- can pause to delay, but can’t stop updates (unless Windows Enterprise)

— Patch management in Ubuntu Linux
	- Software & Updates - manual updates
	- Livepatch - slick interface (like Windows 10)

— Patch management in macOS
	- through App Store (before Mojave - exam came out before)
	- Mojave has seperate Update app
	- pretty much automated, like Windows 10


Working with Disks:
(obj 1.5)
— Error checking - check for errors on HHDs and SDDs
— Optimization - way to organize HDDs (lesser extent in SSDs) to run more efficiently

— right-click on drive -> “Properties” -> “Tools”
	-> “Error checking” - click to run - details shows Event Viewer
		- Chkdsk - check disk
		- checks file table for the partition and verifies each LBA block can read & write data
	-> “Optimize and defragment drive” - click Optimize - 
		- Optimization/disk defragment/defrag
		- in SSDs: Pages store 2-8kb, Blocks store 32-256 pages
			- cannot erase individual pages, only blocks
			- “trim” - runs to identify AFU (“available for use”) pages and marks as such
			- starts allowing rewrites/reuse of pages


Working with Applications:
(obj 1.1)
— installing and uninstalling applications
— Install program - choose where to install, click to run
	- installing into Program Files (x86) indicates a 32-bit program
	- installing into Program Files (x64) indicates a 64-bit program

— Control Panel -> Programs and Features
	- tool used to find programs, see info, and uninstall
	- applications don’t always uninstall nicely
	- check website to see what it’s leaving behind if gives message
	- Registry settings, temporary files, etc

— CCleaner - tool to help remove stuff left behind after uninstall (**not on exam)
	- finds homeless stuff in Registry that needs to be deleted
	- make a back up of Registry beforehand - use at your own risk

— Windows Features offeres additional apps


System Restore:
(obj 1.5)
— System Restore focuses on applications, the Registry, and a few critical system files
— Comes into play when adding/changing applications and device drivers
— Run System Restore, do something, then you can access the System Restore to go back
— Even if Windows doesn’t boot, can access restore points from Windows Recovery Environment

— System Properties -> System Protection ->
	-> “Configure…”
		- make sure it’s on
		- set disk space to use
	-> “Create…” - creates a restore point
	-> “System Restore…”
		- note: Windows itself makes it’s own restore points
		- choose restore point you want


Backing up Your Files:
(obj 4.3 - Maintaining and Optimizing Operating Systems)
— A system repair disk is a bootable media that helps with recovery (different from a backup)
— need an external mass storage device

— Windows Backup and Restore (Windows 7)
	- Control Panel -> Backup and Restore (Windows 7)
	- Create a system image 
		- Image-level backup - system itself, not applications
		- choose external disk / save to network
		- select drives you want to backup
		- Start backup
	- File-level backup 
		- Set up backup
		- choose external disk
		- Let Windows choose - everything + create a system image
		- Let me choose - select individual drives and y/n for system image

— Can test your backups by going into Restore From Backup and if Windows sees it, it’s fine
— Between a System Restore, System Image, and a traditional Backup you’ve pretty much saved your entire system - however, you need to go through this process

— File History (Windows) - Control Panel -> File History - turn on - everything automatically saved
— Time Machine (Mac)


Task Scheduler:
(obj 1.5)
— Enables users to schedule repetitious tasks
— many tasks are prescheduled by Windows (by default)
	- Windows 10 automatically defragments hard drives every week
	- Error checking must be initiated by the user
	- Some driver updates may happen automatically, but not on a scheduled basis

— Control Panel -> Administrative Tools -> Task Scheduler
	- choose a task (Task Scheduler Libary -> Windows)
	- “Triggers” - what actually sets off the task (e.g. Sunday @ 7pm)
	- “Conditions” - e.g. Wake system for task if off
	- “Settings” - e.g. Run task as soon as possible after a scheduled start is missed
	- “History” - listing of how many times task has been run
	- right-click on Task Scheduler Library -> “Create Basic Task…”
	- give task a name and description
	- select Trigger (e.g. Daily, Weekly, Monthly, One time, When the computer starts, …)
	- select Action (e.g. Start a program, Send an email, Display a message (last 2 depreciated))
	- select Finish

— Microsoft Windows does a good job of maintaining and optimizing it’s operating system so not really ever much to do here “except if you feel like Paint-ing at 5 o’ clock, it’ll set it up for ya.”


________________________________________________________________
Chater 15: Working with the Command-Line Interface

Understanding the CLI:
(obj 1.4 - Given a scenario, use appropriate Microsoft command line tools)
— Command-line Interface (CLI) - alternative to GUI
— search “cmd” to access the Command Prompt 
	- just one choice out of many different CLI’s known as shells 
	- also included in Windows is PowerShell 
	- Bash shell - in Linux & Mac
	- all store common functions
— Warning: shells have access to powerful functions (e.g. can wipe entire hard drives) that can reek havoc - all shells have a way to limit certain commands to the superuser/administrator
— Every command can be integrated into scripts

In Windows:
— can right-click on cmd -> “Run as Administrator”
	- now can run any of thousands of powerful commands
— dir - shows date & time created, size in bytes, name, and <DIR> to denote folder
	** directory and folder are interchangable terms
	- dir /p - shows dir stuff one page at a time
	- anything you add to the end of a command is known as a switch
—  /? - switch used to learn about command
	- equivalent output to help commandname
	** know both for exam
— cls - screen clear
— C:\WINDOWS\system32> - the prompt itself - is pointing to a specific directory

In Linux:
— sudo - command to run command as superuser
	- can’t right-click to “Run as Administrator” in Linux
	- su - allows you to type password once and run everythin as a superuser
		- considered a bad idea
— ls - shows directories and files - equivalent to dir
	- ls -l - shows all files and folders w/ permissions and owner name
		- switches use a dash in the Linux world
— clear - clears screen
— man commandname - shows manual of command including available switches


Navigating the CLI:
In Windows:
— starts you in the home directory (of your individual user)
— Directories denoted by a backslash (“\”)

— . - dot - where you are right now
— .. - double dot - previous folder upstream

— cd - change directory
	- cd .. - move one dir back
	- cd \ - moves you to the root directory - holds core files 
	- cd\windows - moves you to this windows folder, from the root directory
		- can include a space or not
		- is a shortcut for cd c:\Windows - because you’re already in the C drive
	- cd \Users\michaelm - moving multiple levels of dirs in one command
	- cd Temp - don’t need the “\” if you’re in the dir that “Temp” exists in
— d: - to get to a different drive, type drive letter followed by a colon
	- you don’t use cd here
	- command prompt will take you back to the dir you were in when you left the previous drive

On Linux:
— Linux doesn’t use a drive letter concept - volumes are mounted as folders under root directory “/“
— Directories denoted by a foreward slash (“/“)
— Tab - on both systems autocompletes
— cd - same command, but Linux cares about capitalization
	- cd ~ - takes you back to home directory
	- cd / - takes you to root directory
— pwd - print working directory - shows where you are


Working with Folders:
On Windows:
— md foldername - make directory with desired name
	- use command in dir you want it to be
	- Windows does not look at capitalization
	- cannot have “Mike” and “mike” directories in the same folder
	- can have a dir called “Mike” and a sub-dir called “mike”
— rd foldername - remove directory (if empty)
	- rd /s - use this switch to remove directories and its contents

On Linux:
— mkdir foldername - make directory with desired name
	- Bash cares about capitalization; can make dir “Mike” and “mike”
— rmdir foldername - remove directory (if empty)
— rm -r foldername -remove directory and its contents


Working with Files:
On Windows:
— *.ext - asterisk is a wild-card - means anything with extension type
— *.* - star-dot-star - everything

— del filename.txt - delete a file
	- not going to a recycle bin - must be careful
	- del *.txt - delete everything in current dir with extension
— copy filename.txt k:\  - copy a file to destination path
— move filename.txt k:\ - moves file - deletes the original after copying
— important to look in the destination to make sure everything copied/moved correctly
— If copy or move sees a file that exists already with the same name in destination path will give a warning and ask to confirm (Y/N/All)

On Linux:
— rm filename.txt - remove file
	- linux uses the same asterick wildcard…
	- rm * - remove everything in directory
	- rm M* - remove everything beginning with “M” from directory
— cp filename.txt Path/to/destination - copy file to destination
— mv filename.txt Path/to/destination - move file to destination


Working with Drives:
On Windows:
— format e: /FS:NTFS - format drive with selected format type
	- format e: /FS:NTFS /Q - quick format
	- format command is only available with administrative privileges
	- Commands available with standard privileges vs. administrative privileges (objective term)
	** be careful - can format c: drive and wipe Windows

— chkdsk - “check disk” - does error correction by checking file table and anything marked as bad is skipped over, and anything marked as good says it’s good
	- not helpful by itself
	- chkdsk /f - this switch actually “fixes”

— sfc /scannow - System File Checker - looks at backup store vs working files
	- if finds any bad copies, will write over them from the store
— dism /online /cleanup-image /restorehealth - Deployment Image Servicing & Management - goes online to Microsoft, finds version you’re running, and compares to your system store - and if any problems found, fixes them.
— always run sfc /scannow & dism as a pair - run sfc, run dism - now we assume everything ok, but run sfc a second time to make sure everything is happy - “you literally cannot have bad system files unless there’s some horrible corruption on your hard drive by using this methodology; it will fix everything, everytime, and it’s absolutely amazing.”

— diskpart - command-line tool - ability to do anything to mass storage
	- gives you an interactive prompt
	- help - all commands you can run
	- list disk - shows you all the disks you have
		- Disk 0 - your bootable - bad 
	- example of partitioning and formatting a drive:
	- select disk 1
	- create partition primary
	- list partition
	- select partition 1
	- format FS=NTFS quick
	- assign letter=x:


Super Copy Commands:
On Windows:
— xcopy - heavy-lifting copy - designed to copy files, directories,
	- features like verify the copy as it copies
	- xcopy c:\backup x: /s /v /h
		- xcopy dir_to_move move_to_loc /switches
		- /s - copy everything in sub-directories
		- /v - verify every copy
		- /h - don’t move hidden files
— robocopy - nearly identical to xcopy - designed to handle more verification and speed
	- robocopy c:\backup x: /s /xa:h
		- /s - same as xcopy
		- /xa:h - don’t move hidden
	- both xcopy and robocopy are network aware, e.g.:
	- robocopy D:\VMs “\\Server\vmbackup” - change destination to UNC value

On Linux:
— dd - Linux’s heavy-lifting copy - a bit-by-bit copier
	- works the best when copying entire partitions
	- dd if=/dev/sda of=/dev/sdb
		- if - source
		- of - destination
	- dd if=/dev/sda2 of=~/backup.img
		- creates an image file of sda2
		- used as backup or bootable media
	- dd if=/dev/zero of=/dev/sdb
		- if=dev/zero - copies from a preset bunch of zeros
		- used to wipe the destination partition


Advanced Windows Command Line:
— shutdown - shuts down computer
	- /s - just shut it down
	- /r - shut down and restart the system
	- can use switches to time when you want the shutdown to take place, etc.

— tasklist - lists all processes running on system
— taskkill process - kill process by name or process ID
	- taskkill /PID 2704

— a group policy (set by domain administrator) trumps local security policies
— gpupdate - queries server and forces updates to system from group policies
— gpresult /R - outputs applied group policies from the gpupdate
	- /R - smallest output that can generated


Advanced Linux Commands:
(obj 1.9)
— shutdown - shuts down computer - give you one minute by default
	- shutdown -c - cancels shutdown
	- shutdown -r - shuts down computer in one minute and reboots
	- shutdown now

— apt-get - repository to get almost any program available to do anything you want
 	- used in Debian based Linux distros (e.g. Ubuntu)
	- sudo apt-get update - update onboard repository to knows current versions of avail programs
		- whenever you install Debian based Linux, run this
	- sudo apt-get install joe - downloads and installs program “joe”
	- sudo apt-get upgrade - upgrades every application on system
		- can specific specific program by adding name to the end
	- sudo apt-get remove joe - delete/uninstall specific program
	- apt-get is fairly depreciated at this point, but still works 99% of the time
	- apt - more commoly used tool for this now (**but know apt-get for exam)

— ps - check running processes and displays all of current logged in user
	- gives you process ID and name of the program
	- ps aux - show all processes from system, all users, and with details
		- shows USER, PID, %CPU, terminal/moniter using, START, COMMAND running it
	- ps aux | grep “libre” - 
		- “|” - pipe - funnel output to the next command
		- “grep” - global regular expression print the string given
	- kill 13482 - kill the process at the process ID given
		- can kill multiple processes depending on dependancy

— vi - text editor - ancient
	- (**on the exam, but 1000 better text editors out there)
	- i - switch to input mode
	- … - tons of other commands to move cursor, etc.


Command-Line Permissions:
(obj 1.4)
On Windows:
— icacls - program to change NTFS permissions
	- icacls folderorfiletoapplyto /grant Mike:F - give full control to the user Mike
	- (** not on the exam)

On Linux:
— chmod - Linux command to change permission
	- ls -l - to check permissions
		- -rwxrwxrwx 1 fred mike
		- RWX for User, Group, Other; owner username; filename
		- if off, letter will be replaced with a “-“ (dash)
		- 421 - 4+2+1 = 7
	- chmod 777 filename - gives User, Group, and Other RWX permissions
	- chmod 664 filename - gives User and Group RX, and Other R permissions
— chown - change owner
	- ls -l
		-  -rw-rw-r-- 1 mike timmy
	- sudo chown fred timmy - change owner to fred
	- ls -l
		- -rw-rw-r-- 1 fred timmy
— passwd - change password on account currently logged into
	- sudo passwd
		- “Enter new UNIX password:”
		- “Retype new UNIX password:”
		- “passwd: password updated successfully”
** Need to know Linux permission commands for exam


Introduction to Scripting:
(obj 4.8 - Identify the basics of scripting)
— Batch file - text file where each line makes up a series of commands
	- Notepad - text editor on Windows

— Goal = Delete log files with a script:
	cd c:\Users\michaelm\Desktop\Logs
	del *.log
	- save with extension “.bat”
	- only works in your own system

— Environment variable - certain phrases that point to certain places or things that work for anything throughout the operating system. (e.g. HOMEPATH=\Users\michaelm)
	- set - command to see list of environment variables
	cd %HomePath%\Desktop\Logs
	del *.log
	- now it works for anyone that logs in

— Ways to do more advanced things e.g. “Delete only logs that are 15 days or more old” with batch files, but Windows released PowerShell for these purposes.
— right-click start -> “Windows PowerShell (Admin)
	- same basic cmd commands work
	- PowerShell extension “.ps1”
	- cmdlet - PowerShell script
	- right-click to open .ps1 file and it opens the Windows PowerShell ISE
		- Integrated Scripting Environment (ISE) - color-coded text editor; highlights errors

— (On Linux:) Bash scripts - have extension “.sh”
	- provide powerful scripting functions
	- # - comments
	- echo - put something up on the screen


Interpreted Languages:
— “.exe” - executable files - preset list of commands designed to talk to Windows and your CPU
	- Compiled code - code written in some language, and then compiled
	- compiler - generates the .exe files
	- downside to .exe files: different compilers for different OSes and CPUs
	- must be programmed for Windows and Mac environment
	- e.g. C, C#

— Interpreted programs - when you need things more broad (e.g. the Internet)
	- e.g. Visual Basic, Python, JavaScript
	- still write programs within a language
	- interpreter - built into OSes and (most of the time) work the same in all
	- don’t convert to a .exe; run code through interpreter and does what it needs to do
	- interchangable terms with “scripting language”

— Visual basic - “.vbs”
	- ‘ - comments
	- Variables - values that can change based on how we manipulate them
	- Intergers and strings - variable types
	- by setting variable types, can use less memory and have better controls on it
		- e.g. “if we denote a certain variable as a string, we’ll try not to add them together”
	- Dim - declares variables
	- Comment syntax (objective term)
	- pretty specific to Windows

— Python - “.py”
	- popular, runs on every operating system; known to be easy to read
	- will see a lot particularly in a Linux environment

— Javascript - “.js” - tool built into every browser to allow “web applications” vs static web pages
	- Client-side applications - JavaScript is the tool for this
		- For statement - conditional loop
		- If statement - conditional
		- Functions - chunks of code that run over and over again
	- is interpreted in real-time on browser when you access a web app
	- Server-side applications - accessing a database, etc.


________________________________________________________________
Chapter 16: Troubleshooting Operating Systems

Windows Recovery Environment:
(obj 3.1 - Given a scenario, troubleshoot Microsoft Windows OS problems)
— Windows pre-installation environment (WinPE)
	- mini operating system used to start the installation process
— Windows Recovery Environment (WinRE)
	- added utilities to WinPE to “create the ultimate philips screwdriver”
	- provides access to essential troubleshooting tools
	- (both are) loadable from a self-created boot drive or Windows Installation media
	- rather than clicking on “Install now” from WinPE screen, “Repair your computer”

— “Repair your computer” -> Troublehooting
	- System Restore - Use a restore point recorded on your PC to restore Windows
	- Uninstall Updates - Remove recently installed quality or feature updates from Windows
		- used iff having a problem with updates
	- System Image Recovery - Recover Windows using a specific image file
		- must have created an image
		- will query you as to where it’s located
		- In Windows 10, Microsoft suggests using 3rd party tools vs using their system imaging 
		- (e.g. Macrium Reflect 7 Free Edition, EaseUS Todo Backup Free)
		- WinRE can recover from images created from these tools
	- Startup Repair - Fix problems that keep Windows from loading
		- looks at startup items, removes vast majority of them
		- he does’t like very much - later video will give better option
	- Command Prompt - Use the Command Prompt for advanced troubleshooting


Advanced Windows Startup Options:
— Advanced startup options give you some very agressive ways to granularly start up your computer in just the way you want in order to get certain things done.

3 different ways to get to these options (in Windows 8/10):
—> System Configuration
— Safe boot 
	- Minimal - sets up just the minimum amount of things to get Windows booted
	- Alternative shell - boots straight to a Command Prompt after logging in graphically
	- Active Directory repair - get reconnected to Windows server the system is a member of
	- Network - Safeboot + activates network card - useful to get drivers, etc.
	- additional selectable options:
	- No GUI boot - no “starting Windows spinner” and screen will be black up to logo login screen
	- Base video - common to choose if have a bad video card
	- OS boot information - “Not that terribly important”
	- Boot logging - every program that logs when it boots up will log start and success

—> Settings -> Recovery -> “Advanced Startup” Restart now

— Boot up windows, immediately shut off @ blue screen, boot up again, turn off again, boot up a third time and you will get to “Automatic Repair” screen -> Advanced options -> Startup settings -> Restart 
	- Press a number to choose from the options below:
	- 1.) Enable debugging (special tool allowing to step through a lot of things)
	- 2.) Enable boot logging
	- 3.) Enable low-resolution video (800x600 - use if have a bad video driver)
	- 4.) Enable Safe Mode (turns off all kinds of swap files, 64-bit talk to hard drives, etc.)
		- brings you to a very simple Windows
		- if driver problem, Windows will be able to boot up
	- 5.) Enable Safe Mode with Networking
	- 6.) Enable Safe Mode with Command Prompt
	- 7.) Disable driver signature enforcement
	- 8.) Disable early launch anti-malware protection
	- 9.) Disable automatic restart after failure (handy if constant reboot and can’t get out


Troubleshooting Boot Problems:
3 main categories of problems:
— 1. Boot problems - computer has booted up, but it can’t find Windows or Windows is messed up and it can’t start Windows.
— 2. Windows never loads to a desktop
— 3. Bizarre things happen at desktop level - error screens, freezing, or blue screen of death

— Black screen - is laptop in hybernate mode? is computer actually turned on? is there a problem with the boot order?
	- if computer is booting up (in fact, Windows is actually running):
	- Device driver issues - most commonly a graphics card
		- Step 1: Boot to Safe mode (Safe boot) - use the 3x reboot method
		- Step 2; Get to Device Manager 
			- right-click on driver -> “Properties”
			- check the Version number and research
				- bad patches happen and Windows can automatically updates to
			- options:
			-> “Roll Back Device Driver”
			-> “Update Driver” - often manufacturer will release to fix particular problem
			-> “Disable Device” - Windows will default to a basic video
		- can also go into Event Viewer from driver Properties -> “View All Events…”
			- will give specific events to the driver
			- select most recent event to the problem
			- cut+paste info into search engine
			- often not the first person to have problem and fix will be given
	- No OS found - Windows can’t even boot up:
		- #1 problem is thumb drives and boot order issues
		- Step 1: scan around and check for thumb drives
		- Step 2: Reset/update boot order - from System Setup
	- Did you just do something?:
		- adding a new hard drive, new RAM, etc.
		- undo what you just did and see if Windows boots up
		- search online to find answer to problem you need
	- If boot files for Windows corrupt:
		-> WinRE (Windows Recovery Environment)
		- Repair installation or Reimage/reload OS
		- choice here is often guess work
		- if it’s really corrupted, probably have a hard drive issue
			- reinstalling Windows from scratch here
			- “good thing you have a backup huh?”


Troubleshooting at the GUI:
— Reboot - “Have you tried turning it off and turning it back on again?”

— Never boots - We know Windows is trying to load, but we just sit there and it never actually gets to a desktop - get the infamous Microsoft spinning wheel or nothing every happens
	- Windows OS itself is probably ok, but something in the startup causing issues
	- Reboot! - atleast 3x, if it doesn’t boot correctly by then,
		- will give you Advanced Settings options - boot into Safe Mode
	-> Event Viewer -> “Windows Logs” -> “System”
		- take a look at the errors from the top
		- will tell you what is making Windows sit and wait
	- from there start your own diagnostics depending on what you see
		- waiting for a particular service?
		- unable to find some bizarre looking file?
		- search online and find one of the 50,000 other people who have already had problem

— Windows is fine, just incredibly slow:
	- can be application issues or not enough RAM
	- “16 GB of RAM for Windows 10 these days is just about the absolute minimum”
	- can boot into Safe Mode and run chkdsk /f to see if have problem on the drive itself
		- (rare at this point)
	- application issues?: Mark Russinovich - Sysinternals
		- released a ton of utilities on his site sysinternals and Microsoft hired him
		- all of his tools are free (www.sysinternals.com)
		- (**need to know his name)
		- Autoruns - tool to exhaustively check everywhere things might autostart on system
			- if Event Viewer showing some program causing trouble
			- Safe Mode -> Autoruns
			- can shut off individual services, applications, causing issues getting to desktop

— Corrupted profile - able to log in (get to login screen), but never get to a desktop - could be a corrupted drive, will need to wipe the account and start over, but try:
— (on Windows 7:) -> Safe mode -> Control Panel -> Administrative Tools
	-> Computer Management (right-click -> “Run as administrator”)
	-> “Local Users and Groups”
	- find the corrupted profile that is causing trouble
	- right-click -> “New User…” - create new user for person
	- if you look in File Explorer - won’t have a folder for new user until their first log in	-> cmd (right-click -> “Run as Administrator”)
		- robocopy c:\Users\Fred c:\Users\Fred2 /s
		- copies everything (including subdirectories w/ /s)
		- should skip everything that has corrupted
— (on Windows 10:)
		- neosmart.net/wiki/corrupt-user-profile
		- “Fix #1: Registry Editor”
		- one of the few times you will go into Registry to fix problems
		- read info and follow steps
— His favorite personal fix to this is copying all files to a thumb drive and just wiping and recreating as a new profile…


Troubleshooting Applications:
— Windows boots up correctly, at the desktop, and then ugly things start to happen in three main areas:

— 1. System running slow
	- immediate thought is “malware, malware, malware” - high probability here
	- if not malware:
	-> Task Manager -> “Processes”
	- find stuff eating up CPU (but could find Disk)
	- turn them off - if you can’t, do a web search
	- storage can be an issue:
	- Defragmentation - even w/ an SSD this can help things
	- chkdsk - “one dll file that’s on a bad spot on a drive can slow the system down”
	- Look at Event Viewer application log - can give clues as to what might be taking place

— 2. Applications blowing up
— can be using an application, it crashes, and gives you an error window - best case scenario
— can be using an application, computer freezes
	- look at Event Viewer application log - but weakest Event Viewer place
		- if freezes, unlikely event will be there - Event Viewer just as suprised as you are
	-> Control Panel -> Programs and Features ->
	- Application repair - available in some right-click menus on a case-by-case basis
	- Delete application and try again
		- bad spots on mass storage can cause issues
		- running chkdsk or maybe system file checker might be good ideas
		-  goal here is to move the application off the bad spot
	- Apply updates 
		- did I update something else? did I update Windows and now having problems?
		- do a search, likely to find answer

— 3. Problems with services - Services that fail to start
	- CompTIA says to restart the service
	- in reality, if a service fails to start, something else is causing it
	- sure, go into startups and make sure that its set up to start automatically, etc
	- but go into Event Viewer -> “Services” - 50% of time fails to start bc something else


Kernel Panic:
— When things go horribly wrong, the operating system doesn’t know how to deal with it, is crashing and can’t recover, and gives you one screen before dying - manefesting differently on each OS:
	- Spinning Pinwheel of Death (SPoD) - macOS
	- Blue Screen of Death (BSoD) - Windows
		- on older versions, would get technical detail
		- recently, a :( Something went wrong
		- sometimes a QR code that will point to a Windows site
	- will give some crazy screen of text on Linux

— Most BSoDs caused by hardware
	- shut down the system, pull out the new hardware you installed, research solution online
	- new video card or motherboard could be incompatible with your version of Windows
	- Update the hardware - drivers, firmware - might have to wait for manufacturer to give fix
	- Safe mode -> Event Viewer - look for clues
	- try a driver rollback, try an update



________________________________________________________________
Chapter 17: Display Technologies

Resolutions and Aspect Ratios:
(obj 1.6)
— 4x3 aspect ratio - used by first gen monitors
	- basically mimics television
	- VGA - 640x480
	- SVGA - 800x600
		- (most Windows versions having problems with video card will downgrade to this)
	- SXGA - 1280x1024
	- UXGA - 1600x1200
	- when monitors have “black bars” on sides, is bc adjusting to old 4x3 aspect ratio media

— 16x10 aspect ratio - popular for a long time because tied into…
	- 16:10 - golden ratio - has asthetic that people like, a lot of paintings use
	- WSXGA - 1440x900 (popular in laptops)
	- WUXGA - 1920x1200 (popular for a long time until HD TV came around)

— 720p - progressive scan - 
	- interlaced scanning - in the old days, to make a picture - scanned lines 1,3,5,7,9…2,4,6,8,…
	- 1280x720 - first common 720p resolution (was actually 1366x768)
	- QHD/WQHD - 2560x1440 - doubled - popular for gamers

— 1080p
	- 1920x1080 - classic HD TV - one of the most common monitor resolutions today

— 4K
	- 3840x2160 - “classic 4K” - 4x HD TV resolutions on one screen
	- 5120x2880 - 5K - especially seen in Mac world

**exam tip: must memorize these resolutions - helps to organize them by aspect ratio


Multiple Monitors:
— don’t need a special video card or have them plugged into the same video card
— don’t need to be the same resolution or size

— right-click on Desktop -> “Display settings”
	- will confirm whether or not it sees 2 monitors
	- by default, will only display to one
	-> “Identify” - will connect the other one
	- can choose to duplicate or extend display
	- important to know/set which monitor is #1 and #2
	- can orient left/right or top/bottom
	- can orient to portrait mode
	- “main display” show search and task bars


________________________________________________________________
Chapter 18: Essentials of Networking

Network Card Troubleshooting:
(obj 1.8)
— Network interface card (NIC) - snap into motherboard, use RJ-45 to connect to network
— most often to be built-in to motherboard these days (still called a NIC)

—> Device Manager -> “Network adapters”
	- can check if “!”, but in this case, not and know driver is up and running
	- if not working - first make sure that the NIC isn’t disabled
	- right-click on particular NIC -> “Properties”
	-> “Advanced”
	- different NICs will have different settings here
	- Speed & Duplex - most often just set to “Auto negotiate” and works great
		- Duplex 
			- Full-duplex - talking and listening at exact same time
			- Half-duplex - only situation he’s used is w/ cross-over cable connected laptops
	-> “Power Management”
	- Wake-on-LAN - wakes a computer from off if certain information comes in
		- Magic packet - used by admin when wanting to install an update on off computers
		- also a setting in System Setup to toggle this

— Link lights - anytime you have a device connected to a system (e.g. switch) - 3 lights to tell you:
	- 1. Connected - if connected properly, will be steady and on all the time
	- 2. Speed light - can be the same light as connected, but changes color
	- 3. Activity light - always flickering 
	- will be seen on the switch and connection on computers motherboard port


________________________________________________________________
Chapter 19: Local Area Networking

Working with Connections:
(obj 1.4)
— netstat - command that shows statistics for all network connections on system
	- TCP and UDP (shows ICM but goes quick) connections
	- shows Proto (protocol), Local Address (IP + port num), Foreign Address, State
	- netstat -n - gets rid of words and gives raw numbers
	- will show a bunch of stuff even if not on browser, skype call, etc.
	- is Windows telemetry - checking for updates, listening for Cortana to update voice file online
	- Windows folder sharing - (port 445) 
		- when connected to drive on local network, Foreign Address = your_ip:445
	- netstat -a -n - see everything (“all”) in numeric form (includes where things are listening)
		- State = LISTENING
			- on port 445, means you have folders shared on LAN
			- on port 80, computer acting as a web server
				- use loopback address in browser to see
		- State = ESTABLISHED - are ongoing connections
		- State = TIME_WAIT - pretty much done with connection, but waiting for certain time
		- State = CLOSE_WAIT - already sent out a close
			- waiting for response that “yes, we’re closed” or to timeout
	- will see that IPv6 connections available/shown in the same way
	- can be a sign of malware if things are listening on ports you don’t know
	- sometimes things like network card drivers will listen on Port 80

— TCPView - tool by sysinternals (Mark Russinovich)
	- basically a graphical netstat
	- green highlight - on new connections establishing (e.g. opening a browser)
	- red highlight - shows the CLOSE_WAIT that are disconnecting
	- can right-click -> “End Process…”


Working with Workgroups:
(obj 1.8)
— NetBIOS/NetBEUI - original methodology used by Microsoft to share stuff on a network
	- NetBIOS - the naming system - reduced you to ~15 characters
	- NetBEUI - what actually did the communication and created connection btwn systens
	- didn’t use TCP/IP - exclusively MAC addresses
	- useless for anything but small LANs

— NetBT (NetBIOS over TCP/IP) - released by Microsoft to keep up with the times
	- still used the same naming convention, but used IP addresses for connection
	- Microsoft wanted to be able to use NetBT to send files anywhere on Internet so came up w/:
	- CIFS (Common Internet File System) —> 
	- SMB (Server Message Block)
		- Samba - SMBs popularity caused other OSes to create SMB protocols like Samba

— In a Windows network, all you have to do is get everyone onto the same LAN, give them the same WORKGROUP name, and will start seeing eachother automatically (File Explorer -> Network) - can take a while
— right-click on folder/file -> “Share with” -> “Specific people…”
	- select “Everyone”
	- best practice: give read/write permissions here and use NTFS permissions for restrictions
	- will show UNC (\\WIN7PC\Mike)
	- “but on computer MIKEWIN10PC it’s asking for credientials!?”
	- each system may have Mike & Fred, but different accounts on different systems
	- in an enterprise environment, often workaround this with same user/pass for both system
	- bad practice! - this is where Active Directory logins come into play

— whoami - command to see who you’re logged in as


Working with Active Directory:
(obj 2.2- Explain logical security concepts)
— Moving from the world of Workgroups into Active Directory Domain is a big step
— Domain controller - special dedicated computer with Windows Server software installed
— No longer live on local user accounts like with Workgroups, now using domain accounts, but local accounts still exist
— Can set up a share to the domain account on any one given computer without having to worry about having one universal login account for every individual computer - now have real security
— Can now have the same desktop for a user when logging into any computer connected to the active directory domain
— Can set up Security Policies not as a Local Security Policy, but ones that propagate throughout the entire domain
— Can setup login scripts so that everytime someone logs in e.g. a message pops up saying “Be aware that the computers are shutting down at 5pm today, so be sure to get your work done before then”

— Organizational units - a container to organize all users and groups
	- in a large organization, maybe have multiple accounting departments
	- need some way to seperate these accounting departments
	- can use groups (work the same way in active directory domains as local workgroups)
	- but tend to use organization units instead

— Forest - one active directory can have lots of domains in it
	- can have different groups that we spread across a forest
	- e.g. can have totaltest.local, mike.local, fred.local, etc.

— No longer use the local computer name - can be FQDNs (e.g. totalseminars.com) - or an in-house local domain account (commonly <name>.local) - can be safer - not webservers, so people from the internet can’t get to then.

— Domain admin has the power to add any computer to the domain (don’t confuse w/ local admin)
— Control Panel -> System and Security
	-> System
		- “Computer Name: WinServer”
		- “Full computer name: WinServer.totaltest.local”
	-> Administrative Tools
	- running on the Windows Server operating system will provide different tools
	-> Active Directory Users and Computers
		-> right-click on Computers -> “New” -> “Computer”
			- give the computer’s name
			- atypical to set up this way - joining the Domain on individual systems
		-> right-click on Users -> “New” -> “User”
			- give name and “User logon name:”
				- e.g. michaelm [@totaltest.local]
			- give password
			- can right-click on michaelm -> “Add to group…”
				- type “Domain”
				- select “Domain Admin” - to make a domain admin
		- now, doing the same thing again, but giving some organization w/ a group:
		-> right-click on Builtin -> “New” -> “Group”
			- give a “Group Name:”
			- select “Group scope”
				- Domain local - only for this particular domain
				- Global - in general use this (more detail in Network+)
				- Universal
		- using groups as usual:
		-> right-click on new group created -> “Add to a group…”
			- type in a users name
		- using an organizational unit instead:
		-> right-click on domain (e.g. “totaltest.local”) -> “New” -> “Organizational Unit”
			- give it a name
			- drag and drop individual Users into it
		- more account features:
		-> right-click on a User account
			-> “Disable Account”
			-> “Reset Password…”
			-> “Open Home Page”
			-> “Properties”
				- can give Telephone number / Email - useful for sorting and looking for ppl
				-> “Account”
					- can set hours able to log in, etc.
				-> “Profile”
					- can define where their home folder exists
				-> “Environment”
					- Login script - can put a .bat file here

**exam tip: not expected to be an expert at configuring a Windows Server system - do expect you to understand that you’re going to have domain accounts for single sign-on (to login anywhere) and can share based on domain accounts.

— Control Panel -> System and Security
	-> System
		- “Computer Name: DESKTOP-SFPL527”
		- “Full computer name: DESKTOP-SFPL527.totalhome”
			- (“yeah, I didn’t use dot local, I probably should have”)
— right-click on file/folder desired to share -> “Give access to” -> “Specific people…”
	- brings up not only a list of locally logged in users
	- but can give access to any domain user there is
	-> “Find people…”
		- type “michalem”
		- gives you - “michaelm (michaelm@totalhome)

**quiz - Domain is a type of Windows firewall)

Windows Sharing with Mac and Linux:
(obj 1.9)
— all other primary operating systems follow along with the Windows developed system of using Active Directory and folder/printer sharing
— LAN manager - Microsoft’s way of doing file sharing developed in the 80’s that evolved into Server Message Blocks (SMB)

— SAMBA - emulation of the Windows folder and printer sharing tool built into macOS and Linux
	- depending on Linux distribution, may need to install
	- if have Linux systems that need to live in a Windows world, he recs distros w/ preinstalled
	- can be a challenge to install
	- have to dealing with file called “smb” (or samba.conf) to set domain/workgroup/comp name

On Linux:
— Settings -> Sharing
	- turn on
	- give a computer name (or leave one that was entered when installing)
		- to use SMBs, must give a name that Windows Server systems can understand
		- used to have stronger standards, but spaces, etc. can work fine now
		- he likes to use tight, 15 character names to keep compatability w/ older WS systems
— Files (“Nautilus”)
	-> Other Locations
		- can access other shares here
		- have to enter a Username, Domain, and Password
		- “Connect”

On macOS:
— it is actually Samba, but called “Windows File Sharing” here
— System Preferences
	-> Users & Groups
		- create users that match your domain
	-> Sharing
		- set/keep computer name
		- click checkbox to turn on “File Sharing”
		- add to “Shared Folders:” here
		-> “Options…”
			- check “Share files and folders using SMB”
			- can choose to share via Apple’s protocol AFP here too
				- (AFP is depreciated at this time)


Net Command:
(obj 1.4)
— net - a Windows command - by itself, gives an idea of the net commands you can type
— net view - shows all computers on your network
— net view mikewin10pc - shows shares on a particular system
— net share shareit=c:\stuff - make files/folders sharable to others
	- “shareit” - a selected share name
— net share - view everything shared from your system
— net use v: \\mikewin10pc\mike - connected to a shared item
	- “v:” - selected drive letter to map to

— net user - view users on the system
— net user tammy total /add - add a user to the system
	- “tammy” - selected username
	- “total” - selected password
— net user tammy /delete - remove a user from the system

— tons of other net commands exist (e.g. can set times users are able to log in) - do some research - different versons of Windows often have little tweaks to get the net command working right


Firewall Configuration:
(obj 2.10 - Given a scenario, configure security on SOHO wireless and wired networks)
— Firewall - more of a verb than a thing - means to block traffic based on whatever type of criteria you think is important
	- certain IP addresses, certain incoming port numbers
	- based on time of day, based on keywords of websites

— Access control list - defines what users can/cannot do in terms of access
	- e.g. don’t want anyone playing Steam games between 9am-5pm
	- principle of least privileage - only give people enough so they can do what they need to do
		- pretty much means unless given access specifically, user doesn’t have access
— Blacklist/whitelist
	- blacklist - e.g. set that any of these IP addresses is evil
	- whitelist - e.g. only these IP addresses are the ones that you can go to

— Stateless firewalls - “I don’t care whats going on, I am going to block this IP address / port number”
— Stateful firewalls - pretty much just turn them on - will look at the state of a situation
	- e.g. device comes in and asks for a webpage - “OK.”
		- device asks for a webpage 15x in 5s - “AHH, something going on that I don’t like”
	- SOHO routers will often come with this

SOHO router:
— Access router IP address through browser -> Web configuration
	-> Security
		-> “Access Control”
			- turn on/off
			- select access mode (“Blacklist”/“Whitelist”)
			- add devices to the Blacklist
				- any of these devices is incapable of getting out to Internet
			- or add devices to the Whitelist
				- only these devices can get out the the Internet
		-> “Settings”
			- turn on/off SPI firewall - nothing to configure
			- can have options for DOS (denial of service) protection here

More Advanced router:
— Access router IP address through browser -> Web configuration
	-> “Access Restrictions”
		- Access policy - can combine firewall settings to make unique to your situation
			- e.g. “I don’t want anyone accessing from this port number at this time of day”
			- found on more agressive firewalls
			- go online to find specific ports that specific things use that you want to block
	-> “NAT / QoS” -> “DMZ”
		- Demilitarized zone (DMZ) - sends all traffic into network to one particular system
			- choose to enable/disable
			- choose one IP address of a computer inside your network
			- can be dangerous
			(**quiz - A DMZ exposes a LAN host to the Internet)
		- Real DMZ 
			- on a network, one router is connected to file/web servers
			- this router is running a stateful firewall
			- want it to be pretty open to incomming connections for public access
			- a second router connected for use with internal computers, printers, etc
			- hidden behind NAT and router running more agressive firewalls
			- can rent a box and pay monthly fees for regularly updated firewalls
				- often done in places like schools


Windows Firewall:
(obj 1.5)
— Edge / network firewall - on router
	- can watch traffic based on port number, IP address, MAC address
— Host firewall - on individual systems vs on the router
	- can see what processes are trying to view/send data to/from the Internet
	- can now filter based on process ID or name of the program/application
	- all OSes have a built-in host-based firewall

— Windows Defender Firewall
	- accessible through Control Panel or Settings
	- Network discovery - Windows will query to find other computers, printers, video servers, etc.
		- when connecting to new networks can choose to be discoverable or not
	- can used Windows Defender Firewall to change firewall settings based on network type:
	- Domain networks - connected to an Active Directory Domain 
	- Private networks - home/office
	- Guest or public networks - logging in at airport/coffee shop
	- can turn Windows Defender Firewall on/off for each network type
		- “Block all incoming connections, including those in the list of allowed apps”
			- not going to stop outgoing connections e.g. browser connecting to a webpage
			- will stop anyone external from looking for you and asking for shared folders
		- “Notify me when Windows Defender Firewall blocks a new app”
			- good idea to always keep checked
	-> Advanced Settings
		- where all rules take place (“Inbound rules” and “Outbound rules”)
		- exception - allows things to “phone home”
		-> “New Rule…”
			- select Program, Port, Predefined, or Custom
			- pick specific Program
			- “Allow the connection” - essentially whitelisting it
			- select the firewall(s) it applies to (Domain, Private, Public)
			- give the rule (exception) a name
	- won’t often go to Advanced Setting to do this
	- will get notification that something was blocked and tell prompt to block/allow
	- be careful with what you allow through
	

Port Forwarding:
(obj 2.10)
— easy to view things like video streams through built in webservers on a webcamera in a browser by typing in IP address when you are connected to the local network (e.g. at office)
— but if you want to access one somewhere else (e.g. at home), where the network is NAT-ed (one real IP address and every other device is hidden by private IPs), you can, through…

— Port forwarding - simply means that your NAT-ed router is going to be watching for certain port numbers - normally, will allow outgoing port 80 requests (going to a website), but blocking incoming (don’t want; not a web server) - but port forewarding opens this, so when you connect to your WAN-ed IP address at your router through a browser, will send to your camera (door bell, thermostat, etc.).

— Access router IP address through browser -> Web configuration
	-> “NAT / QoS” -> “Port Forwarding”
		- “Application:” - give it a name
		- “Protocol:” - TCP/UDP/Both
			- (for carmera, using HTTP, which is a TCP protocol)
		- “Source Net:” - can give particular IP address from the outside world or leave blank
		- “Port from:” - 80
		- “IP Address:” - give internal address (can find through “Status” -> “WAN”)
		- “Port to:” - 80
		- “Enable” - check
	- can select to have router listen (“Port from:) to a non-standard port (e.g. 11461)
	- that way, to get to the camera someone has to type in your internal address and port
		- (e.g. 11.12.13.240:11461)
	- almost guaranteed your WAN IP address is DHCP (will change from time to time)
	- Dynamic DNS - software on router that gives you a DNS name
		- then, no matter what your IP address is, your router will call home and update
		- often charged services (ASUS routers are famous for providing free options)
	-> Setup -> “DDNS”
		- choose the service you want to use to create Dynamic DNS (e.g. DynDNS.org)
		- enter user/pass given by the company
		- enter the “Host Name” you’ve previously set up (e.g. mikecamera1)
	- then, to get to camera from a browser, type “mikecamera1.dyndns.org:11461”
		- it will automatically get to the WAN IP address of your system
	

________________________________________________________________
Chapter 20: Wireless Networking

Wireless Encryption:
(obj 2.3 - Compare and contrast wireless security protocols and authentication methods)
— Only downside to setting up your own SSID without encryption - anyone can intercept it - benefit of a wired network - only way to intercept traffic is if they can plug into your switch

— WEP (Wired Equivalent Privacy) - original security protocol of 802.11
	- modern advanced 802.11ac routers still often have a setting for it
	- “Key Value:” - enter 10 hexadecimal characters
	- needed to use word-of-mouth to give all connecting clients
	- RC-4 - ancient form of encryption - predictable, people were able to hack it mechanically

— 802.11i - Wifi Alliance worked with IEEE to attempt to come out with a new standard
	- was going to have authentication - username+password or smart card to get on network
	- TKIP (Temporal Key Integrity Protocol) - improved on predictability of RC-4
	- were going to use TKIP, but threw it out for:
	- AES (Advanced Encryption Standard) - primary encryption used today
		- for everything from secure webpages, voice over IP calls, etc.
		- difficult to get wireless network card to decrypt

— WPA (Wi-Fi Protected Access - IEEE predicted it would take 3+ years to release, so WAP manufacturers (e.g. Cisco, Linksys, …) came together to figure out what they could take and use from 802.11i immediately
	- added TKIP to RC-4 and two new ways to authenticate:
	- Personal/Pre-shared key - word-of-mouth passing of key to join network
	- RADIUS server - seperate box logged into w/ user+pass

— WPA2 - released by WAP manufacturers once hardware caught up to be able to decrypt AES, had basically the same security protocol of 802.11i (but it still hadn’t been released).
	- standard used today

— Access router IP address through browser -> Web configuration
	-> Wireless -> Wireless Settings -> “Advanced”
	- “Security:” - WPA/WPA2-Personal (Reccomended)
		- “Password:” - enter a robust key to share to access network
		- “Version:” - select Auto
			- WPA-PSK (personal/pre-shared key)
			- w/ Auto, chances are will choose WPA2-PSK
		- “Encryption:” - select Auto
			- TKIP - fixes you to WPA	
			- AES - fixes you to WPA2
		- rare to see/use WPA on a router today
	- “Security:” - WPA/WPA2-Enterprise
		- enter the RADIUS Server IP address
		- enter the password to get into the RADIUS server for configuration

— WPS (Wi-Fi Protected Setup) - designed as simpler way to set up WPA2-PSK
	- press “WPS” labeled button on back of router
	- press “WPS” labeled button on back of any WPS capable device (within earshot)
	- will automatically configure themselves
	- access router web settings and will see pin used
	- problem: WPS is incredibly easily hacked (option to turn off)
	- designed now to add increasing delays to incorrect pin guesses
		- (e.g. making 1000x pin guesses in a min by hackers)
		- still a weak choice - only use if need the convenience


Enterprise Wireless:
— tend to use lots of dedicated WAPs
— Power over Ethernet (PoE) - devices like WAPs get electricity through ethernet cables and don’t have AC adaptors
	- PoE (1st generation)
	- PoE+ - a lot more electricity provided to individual devices
	- must have a PoE switch or PoE injector - device to bridge PoE devices to switch

— WAP placement and antenna selection is important:
	- e.g. want coverage in hallway? - directional antennas on both ends of hallways
		- “give long football shape”
	- e.g. individual offices? - dipole in the middle or patches in each office
	- e.g. large, open office? - multiple dipoles or omni-directionals depending on space
	- with large enterprise environment tools, can just start placing and will produce a heat map
	- gives you a good idea of dead spots or where you might be shooting outside of desired area
		- expensive tools / hiring of professionals to set up

— AAA - authorization, authentication, accounting - using WPA2, but not PSK
	- RADIUS or TACACS+ - boxes to provide needed authentication
	- signing into network w/ user+pass
	- very agressive authentication - can add things like smart cards

— Access WAP IP address through browser -> Web configuration
	- won’t have firewall or DHCP settings here (as just a WAP)
	-> “Configuration”
		- “User Account Table” - add users
		- “Host Name:” - change to something to help you remember them
		- change IPv4 settings to be static - don’t want them to change
		- “Network Mode:” - select 802.11 protocols you need
		- Extended SSID (ESSID) - set up a single SSID name and will be same on all WAPs
			- devices connected will automatically be handed off to closest WAP
			- need to set up each WAP individually
			- nothing to configure, “it just works”
			- “Isolation:” - only comp on network wireless clients can talk to is the WAP
				- won’t be able to share files/folders or ping eachother
			- can set max number of clients
			- can set multiple SSIDs (e.g. guest)
		- “Rogue AP Detection” - 
			- all WAPs will be added to known list of MAC addresses
			- someone trying to add their own WAP will be blocked
			- “know your network ID for the networks you dwell upon!”
			- can log in and suddently see a non-APIPA address that isn’t yours
		- “Rate Limit” - can throttle speed of particular SSIDs upstream and downstream
		- “Captive portal” - screen that makes you type in a user/pass or room number
			- not a RADUIS/TACACUS+ user/pass
			- customize a page and add your own users to a list

— can have a specialty switch designed to work with WAPs - will automatically propagate the ESSID after setting up, can have a single place to set/manage users for a captive portal, etc.


________________________________________________________________
Chapter 21: The Internet

Telnet and SSH:
(obj 4.9 - Given a scenario, use remote access technologies)
— Telnet - port 23 - remote command-line tool - used to connect between computers before graphical operating systems were around - still around today

— PuTTY - a popular Telnet client (used to connect, comparable to browsers being web clients)
	- “Host Name (or IP addresss):” - give it a FQDN or IP address for a Telnet server
	- (can netstat -n to see the connection)
	- give username and password to make connection
	- will now have access to the command-line of the remote server

— Telnet lacks encryption and offers no security - anybody between you and Telnet server can intercept the data - including the username and password

— Secure Shell (SSH) - port 22 - “Telnet’s big brother”
	- automatic point-to-point encryption to remote server’s command-line
	- same entries in PuTTY, just specify connection type to SSH and port to 22
	- will send you a key (used to encrypt) and ask if you want to store it (“Yes”)
	- enter user and password as before and have same access

— Only time using Telnet/SSH is to get to command-line remotely (e.g. servers, routers, other “boxes”)


Remote Desktop Connections:
— Remote Desktop Protocol (RDP) - protocol unique Windows - port 3389

Setting up on computer you want to remote access:
— System Properties -> “Remote”
	- Remote Assistance - when someone connects, both have mice, keyboard, monitor access
	- Remote Desktop - when someone connects, noone else can connect to it
	- “Allow remote connections to this computer” - check
	- need IP address or computer name (ipconfig)

Setting up on computer that will gain access:
— search -> “Remote Desktop Connection”
	-> Options -> “General”
		- give name of computer you want to connect to
		- will disconnect the other person from their machine (gives warning)

— Virtual Network Computing (VNC) - most popular 3rd party protocol used by other OSes
	- built into most Linux and Mac machines, not built into Windows
	- TightVNC - free program that runs on top of VNC protocol
		- both a server and a client
		- just want to run the viewer to see people who are sharing their desktops
		- “Remote Host:” - give IP address or FQDN
		- “Connect”
		- give VNCs built-in password
		- works on every OS (even Windows-to-Windows)

**exam tip: only protocol you need to memorize is RDP uses port 3389


The World Wide Web:
(obj 2.2)
— predominant way most look at the Internet, always manifests as some type of web browser
— HTTP - port 80 - traditional protocol
	- HTTP is insecure - wide open for anybody to intercept anything you’re doing
	- fine for configuring a router you’re directly connected to, but never on real Internet

— HTTPS - port 443 - (HTTP secure)
	- HTTPS encrypts everything
	- Certificate - keys allowing to encrypt a connection, signed by a 3rd party that they’re good
		- SSH hands you a key when you connect, but you trust your own server
		- certificates will provide lots of info
		- key, date issued, serial # issued by authorizing body, name of exact website, etc.
		- two protocols used to encrypt HTTPS connections:
			- Secure Sockets Layer (SSL)
			- Transport Layer Security (TLS)


— neverssl.com - intentionally HTTP - browser will show connection “Not secure”
— badssl.com - gives great examples of all types of bad certificates

— browser will give you warning pages typically telling you whats wrong with the certificate
	- will all give you option to ignore the problem and enter
	- use your judgement to proceed or run away

examples of typical certificate errors:
— Expired certificate - NET:ERR_CERT_DATE_INVALID
	- people forget to renew
	- use your best judgement (can be ok if you trust org/company)
— Revoked certificate - NET:ERR_CERT_REVOKED
	- somebody has been caught doing something naughty or refuse to pay
	- has been taken from them by the issuing body
	- best to refuse to enter
— Self-signed certificate - NET:ERR_CERT_AUTHORITY_INVALID
	-  have an inhouse webpage, give a certificate to keep encrypted
	- only employees accessing, so don’t feel like paying for a full blown signed certificate
	- just confirm url is the one you want to access and proceed


Troubleshooting Internet Connections:
(obj 1.4)
**exam tip: will be “filled and I mean filled with big, long, hairy networking questions that will be pretty simple as long as you stick to basic networking rules. Understand how networks work and follow a couple rules that always work for me”.
— 1. Check your physical system first - don’t let the physical get you down
	- check link lights and actual connectivity via OS before blaming anything else

— Know your network! - know network ID, what your router is, and what your DNS server is
	- use ipconfig /all
	- document this long before touble comes along
— Know your Internet connectivity! - sometimes multiple layers of routers before actually getting out
	- Traceroute - command-line application to show each connection out
	- Windows: tracert, Linux/Mac: traceroute
		- tracert www.ibm.com - pick someplace to go out to on internet, doesn’t matter
	- run before things go bad, so when it does, you know what supposed to look like
	- running again in the future and only see one hop - never gets to gateway router
		- tells you something probably wrong between internal and gateway routers
	- Ping
		- ping myrouterip - run and get a reply?
			- automatically know you have a good IP address and router prob up and running
		- ping ftp.microsoft.com - picking some arbitrary FTP site
			- Request timed out. - “who cares!”
			- if pinging a FQDN and returns an IP address - your DNS server is working

**exam tip: lots of tools you can get for all kinds of things. 95% of the time can fix all network problems with ping, traceroute, and ipconfig - practice with them, will see on exam.


________________________________________________________________
Chapter 23: Portable Computing

Power Management:
(obj 1.6)
— AC adapter - plug in and chare laptop batteries
	- Vendor-specific power ports - often have own proprietary connection to computer
		- just because connection looks the same, doesn’t necessarily mean it’s right
		- going to have particular voltage, amperage, and polarity to match
			- polarity - center point and outside ring can have minus and plus switched

— If you have a good AC adapter but not getting power to your laptop
	- check the actual jack - other videos will show how to replace
— If laptop runs great when plugged in but dies as soon as unplugged
	- battery is dead or actual charging circuit inside laptop is bad
	- battery tester can verify if actually good/bad or just buy a new battery
	- vast majority of laptop batteries are lithium-ion - running for 2+ years, great.

— Advanced Configuration and Power Interface (ACPI) - functions built into CPU
	-> BIOS
		- can power on by keyboard/mouse, time of day
		- when comp is asleep, don’t have an OS, so waking up is a BIOS job
		- “Soft-Off by PWN-BTTN” - Instant Off / Delay by 4 sec / Hybernate
		- ACPI either enabled/disabled
		- ACPI level 0 - means it’s on
			- ACPI is enabled, but currently unused
		- ACPI level 3 - sleep mode 
			- CPU shuts off
			- RAM keeps running - holding whatever it was to be ready to power system
		- ACPI level 4 - hybernation mode
			- everything on RAM copied to a file on hard drive
			- then even RAM is shut off
			- uses a lot less power than sleep, but takes longer to come out of
			- (can see file RAM is copied to - on Windows, in root, hyberfile.sys)
		(**quiz - ACPI does not have an “off” setting; On, sleep, and hybernate are all of them)
	-> Control Panel -> Power Options (also available via Settings)
		- power plan
			- Balanced - at ACPI level 0 and running at full speed can
				- turn off monitor or hard drive w/out going into sleep mode
				- can say “turn off the monitor after 3 mins”
				- still wide awake, hit keyboard and right back to where you were
				- however, does cut down on a lot of power
				- hard drive + monitor uses more power than system itself (CPU + RAM)
		- “Choose what the power buttons do”
			- can choose sleep, hybernate, or shutdown
			- specific to on battery, connected to AC adapter, and lid close
		- “Create a power plan”
			- can create custom power plans or edit existing
			- gives setting options for time to turn off display or put to sleep
			-> “Change advanced power settings”
				- very detailed settings for hard disk, wireless network card, etc.


________________________________________________________________
Chapter 25: Care and Feeding of Mobile Devices

Mobile Device Security:
(obj 2.8 - Given a scenario, implement methods for securing mobile devices)
— Screen lock - always keep a password, pattern, PIN, face recognition, etc.
	- often have settings for time-outs or full device erase after certain num of incorrect attempts
— Multifactor authentication - using more than one system of security
	- e.g. particular app requiring login & code entered from sms/call
	- Authenticator apps - gives you code to use
		- downside: sometimes if losing phone (/device set up on) can be locked out
		- some give backup codes to save to get around this later
— Locator apps - Find My iPhone && Android Device Locator
	- play sound (e.g. lost phone behind couch, etc.)
	- device lockout
	- erase device
— Mobile Device Management (MDM) - different security options in enterprise environments
	- Bring Your Own Device (BYOD)
		- less security options
		- careful what company stuff kept on device
	- Corprate-Owned Personally Enabled (COPE)
		- can set up security policies, lockdowns, etc
		- can whitelist certain applications


Mobile Security Troubleshooting:
(obj 3.5 - Given a scenario, troubleshoot mobile OS and application security issues)
— Signal drop/weak signal - someone might be turning down your connectivity
	- classic example of first step of someone wanting to attack device
	- don’t want you connecting, updating, or anything being checked
	- going to be obvious
	- turn phone completely off and check later

— Power drain, Slow data speeds, High resource utilization
	- happening because someone grabbing a lot of things from system
	- will almost certainly be an Android device
	- must run an anti-malware (caveat: for Android, although good, is imperfect)
	- start checking accounts and changing passwords everywhere
	- factory reset and reinstall from scratch (“because I’m paranoid, that’s why.”)

— Unintended Wi-Fi/bluetooth connection
	- he avoids broad connections like ATT ones
	- too easy to connect to them when wanting to be on the coffee shop one
	- easy for people to mimic and get you connected to do whatever nefarious things
	- wipe device completely and install from scratch after agressively changing passwords

— Leaked personal files/data
— Unauthorized account access
— Unauthorized location tracking
— Unauthorized camera/microphone activation
— All above are not symptoms, but a result of a hack - time to go absolutely bananas
	- 1. wipe device completely
	- 2. change password to every single account
	- 3. “take solace in whatever entitity, spirits, or philosophy you choose and hope
		that person hasn’t caught one place with one password where you were doing
		something you probably shouldn’t have been doing in the first place.”

** Keep in mind that many security troubleshooting scenarios are simple misconfiguration

Mobile Device Troubleshooting:
(obj 3.4 - Given a scenario, troubleshoot mobile OS and application issues)
— Inaccurate/non-responsive touchscreen
	- often just system overload / too full of stuff vs actual touchscreen issue
	- restart the system to see if goes away - might just have too many apps
	- some devices have calibration capabilities (rare)

— Dim display 
	- turn up the brightness
	- if using auto-brightness, make sure turned on
	- on some devices can replace backlights (rare)
	- replace device

— Cannot display to external monitor
	- make sure you on the same wireless network as the monitor
	- make sure you are trying to connect to the right monitor
	- can’t assume all monitors will work with your device - check with manufacturer

— No sound from speakers
	- make sure sound is on/up
	- depair any bluetooth devices (sound going to wireless headphones)

— Intermittent/no wireless connectivity
	- check for interference issues more than anything else
	- might opt for a site survey
		- e.g. office next door might be eating up 802.11ac band spectrum w/ huge system
		- need to move
	- no wireless connectivity at all assumes you can connect to SSID
	- check distance, WAP itself
	- can’t log into the SSID? - delete profile and retry

— No bluetooth connectivity
	- make sure device you’re trying to connect to is in discoverable mode
	- make sure someone else isn’t already paired to the device
	- make sure your bluetooth is turned on

— Apps not loading/app log errors
	- apps can use cacheing - take steps for particular app and try again
	- do a force stop to shut app down and start up again
	- restart the entire phone
	- worst case: uninstall the app and try reloading
	- look online for solutions

— Slow performance - running too many apps

— Extremely short battery life
	- burning too much battery
		- GPS is a big eater of battery life
		- anything running in background or constantly syncing burns CPU cycles
	- use OS specific tools to list apps by amount of electricity it eats
	- remove the worst offenders

— Overheating
	- all smart devices have built in thermal trip switches to prevent from getting too hot
	- will fail sometimes if don’t give enough ventilation
	- lithium-ion batteries are dangerous

— Frozen system
	- most often problem with an app
	- streaming apps can eat a lot of CPU cycles waiting for something from the network
	- trace it to particular app, delete it, and wait for a patch release to fix problem

— System lockout
	- assuming not something malicious (which is more often)
	- maybe too many incorrect password attempts
	- factory reset and reinstall


________________________________________________________________
Chapter 27: Securing Computers

Threats:
(obj 2.5 - Compare and contrast social engineering, threats, and vulnerabilities)
— Host-based security - protecting the individual system
— Network-based security - router, switches, and other computers
— Physical security - e.g. locks on doors, security guards

— Man-in-the-Middle - something between sender and receiver (server and client) intercepting
	- can be done on email, wireless, webpages, etc.
	- main fix is encryption - while they might see traffic, is in a form they can’t read it

— Spoofing - to take on the look and feel of some other entity
	- can take place in email, etc. - any type of client-server situation
	- certificates on webpages, and other forms of authentification
		- verify encryption (preventing man-in-the-middle) and make sure noone is spoofing

— Denial of Service (DoS) - 
	- e.g. have a web server ready to respond to give out webpages
	- send malformed HTTP requests that make server sit and wait to figure out requests
	- someone legitimate making a request will get a 404 error (or other) saying server is busy
	- easily the #1 problem on the internet today

— Distributed Denial of Service (DDoS)
	- install some form of malware onto hundreds, thousands, tens of thousands, … computers
	- distributed through email or something like that
	- Zombie - term for computer infected with this
	- some server system in control of all zombies sits and waits
	- suddenly signal is sent, zombies broadcast malformed HTTP requests, and take down server

— Zero day - new type of threat that noone has seen before

Problems to recognize you may be victimized by these types of attacks on individual systems:
— Renamed system files - classic “hacker” move having gained root access to system
— Denied of things you normally want to do (e.g. can’t get to desktop)
— Disappearing files - points to root access hack as above
	- can manefest as permission changes
	- e.g. suddenly don’t even have read access to file previously had full permissions to
— these types of problems can usually be seen on some type of log
	- e.g. can see log that people are trying to SSH into your system through network


Physical Security:
(obj 2.1)
— Perimeter security - keep people off property (e.g.  security guards, mantrap, locking doors)
— Rooms - e.g. room locks, badges, biometric locks
— Individual devices - e.g. cable locks, server lock, usb lock, privacy screen

— Security guard 
	- passive protection - not even going to try to get in
	- check credentials and stop people
— Mantrap - a two-door scenario w/ guard, credential checking, security camera, etc.
— Locking doors - need a key
	- Entry control roster - some type of sign-in at door
	- Badge reader - for RFID-chips embedded in badges
	- Smart card - swiped/inserted read to grant entry
	- Biometric scanners/locks - rare
— Cable locks - physically hold down individual computer
— Server lock - physically locks sever into the rack
— USB lock - physical block for USB ports (vs BIOS on/off)
	- usually software on system to give warning that lock is pulled out
— Privacy screens - polarized screens on monitor limiting field-of-view
— Key fobs - getting into parking garages, etc
— Hardware tokens - physical devices giving changing code to get into a computer


Passwords and Authentication:
(obj 2.7 - Given a scenario, implement security best practices to secure a workstation)
— Hash - a one-way value of fixed length that varies dramatically based what you put into it
— When you create a password (e.g. on router), a hash is saved on mass storage rather than the password itself - when you enter a password to log in, it’s hashed and compared to the stored hash

— Biggest issues causing hacked passwords are the fixed length output and the fact that “mike” will always produce the same hash output. Massive hash lists exist that are used to look up found hashes and get the corresponding password. Hacker knows where hashes specifically stored on a system, copy them, and do this.

— Brute force - passwords have a certain length and complexity, once you generate a hash for it, try every possible combination of all these hashes until you get to the password.
	- amount of time it takes depends on the length
	- https://howsecureismypassword.net/
	- rarely used any more, easier to steal hashes, crack at home, then enter into your system
— Dictionary attack - list of known types of passwords that people commonly use
	- e.g. mike, mike1, password, password123, Password123
	- https://crackstation.net/ 
— Rainbow tables - like a dictionary attack, but have lots of tables that work together
	- e.g. common words table, numbers 1-1000 table, table putting * and ! at end and beginning
	- create a zillion different hashes that easily crack
	- 30% of passwords 8 characters or less crack instantly
	- given a few weeks to crack, chances of giving an 8 character password uncrackable is rare

** Kali Linux - Debian-derived Linux distribution designed for digital forensics and penetration testing.
	- ophcrack - rainbow table tool
(** quiz - reverse hashing is not a password cracking technique)

— 1. Set strong passwords - according to A+, always use upper and lower case, numbers, and extra characters - he recommends looooong passwords - create entrophy - longer it is, harder it is - use phrase that you can remember.
— 2. Password expiration - CompTIA says the best thing you can do is make passwords expire in 30-90 days - in reality, created an administrative nightmare of people forgetting passwords, sticky notes on monitors, wildly predictable passwords. He reccomends doing every ~6mo.
— 3. Screensaver - and force reentry of password - leave a system wide open, someone quickly comes in with thumb drive and takes password hash files
— 4. Lockscreen required passwords - critical on mobile devices - longer than 4-digit pins smart idea
— 5. BIOS/UEFI passwords - set administrator and user passwords
	- few places where extremely difficult for hackers to get to password files
	- are on firmware and almost impossible to get to them
— 6. Require passwords everywhere! - if you have something that will take a password, use it
— 7. Multifactor authentication - if something provides it, use it.
	- even with password files will be stopped cold


Malware:
(obj 2.4 - Given a scenario, detect, remove, and prevent malware using appropriate tools and methods)
— “Best Buy’s Geek Squad quotes that around 90% of all of their repair work is simply removing malware”

A - types of malware:
— Virus - old term - floppy disk containing malware passed among systems
	- job 1: replicate - make copies of itself
		- virus would put itself into RAM
		- anytime someone put in a floppy disk it would copy itself to it
	- job 2: activate - do something
		- started as harmless things like make letters fall on your screen
		- quickly evolved to malicious things (e.g. erase the boot sector of your hard drive)

— Worm - 1st gen of malware that used networking to replicate themselves
	- e.g. through email or use netview -> see what computers were out there -> connect to them
	- pretty much all malware today is a worm - uses the internet in some way to replicate

— Trojan horse - program that doesn’t replicate itself, rather by people not knowing what it is
	- e.g. cool game that people are passing around, actually a game
		- but also zombifying your computer for a future DDoS attack
	- running on purpose vs sneaking itself into system

— Rootkit - program that seats itself within the boot sector of drives and tries to hide itself from your operating system itself
	- nefarious years ago, but have learned to look in that place w/ anti-malware

B - how malware gets around / what it does:
— Ransomeware - people think they have malware, search online for “free anti-malware”
	- Rogue antivirus - software claiming can run anti-malware, but are a virus themselves
	- get a pop up to call a number and pay $x to unlock your system
	- biggest malware issue today (second to botnets of zombified computers)

— Botnet - bunch of zombified computers already under the control of somebody else
	- when computer is zombified, still running great, malware sitting and waiting while…
	- somebody (in some other country usually) goes to companies threatening DDoS for payment
	- then, at somepoint (middle of the night) your computer runs a little slower while it attacks

— Keylogger - software recording every keystroke you make
	- the way they work requires them to be somewhat visible
	- will try to hide itself as some well known program / service

— Spyware - a piece of malware that is spying on your system
	- “We can get into semantics here, and I might start arguing that 40% of the websites out there today are spyware. And just about anything that Google offers, I might argue is spyware; atleast Google is honest about it and tells you upfront they’re grabbing this type of information, and its not personalized, generic.”
	- more nefarious spyware is trying to grab very specific things you do
	- e.g. go to florist website and then get a pop up for a different one

C - symptoms of malware:
— Pop-ups - manefests as a separate window; can pop up or pop under your window
	- a pop-up can come from a good website, but for exam, are a sign of malware

— Browser redirection - sent to a different url (maybe slight change) than typed in

— Security alerts - all OSes today will give notification when noticing browser redirection, too many pop-ups, problems with system files being changed, etc.

— Application crashes - according to CompTIA objectives is a sign of malware (he argues not a common issue for malware)

— OS update failure - malware knows a patch has been applied to stop it and trying to stop you

— Spam - by itself, not a sign of malware, logged into too many sites and forgot to opt out
— Hijacked e-mail - going into your email client, grabbing e-mail addresses, and sending
	- start getting spam from a friends well known email address - sign of a problem
	- or friends start responding “I don’t want to buy this type of toothpaste…”
	- Automated replies - suddenly start getting instant responses from emails to friends

— Invalid certificates (Trusted Root CA)
	- can be tied into browser redirection
	- suddenly get certificate error screen from looking at “ebay” certificate for “eboy”
	- going back to deciding what to do based on error given


Anti-Malware:
(obj 3.3 - Given a scenario, use best practice procedures for malware removal)
— Anti-malware - the correct term (No such thing as antivirus program)
	- tons available, when in doubt use the one built into your OS
	- Recovery console - ancient malware program used on Windows XP
		- which isn’t on the exam anymore (“CompTIA, fix your objectives!”)

— Backup/Restore - if you get hit with some type of malware, you can always bail out and recover from a backup - can’t count on anti-malware tools to always clean your system 100% of the time.

— End-user education - teach users what to look for in terms of malware symptoms
	- can run anti-malware themselves or atleast call you and tell you what’s happening

— Software firewalls - make sure the host firewall is running on your individual systems
	- pretty much all malware these days like to “phone home”
	- nothing better than host firewall blocking this

— Secure DNS - most of the time you’re going to use the DNS provided by your ISP, who are nosey, often logging where you’re going and using that for redirection.
	- 1. Non-ISP DNS servers - his personal favorite is Google’s 8.8.8.8
		- does not log or use questionable redirections when you type in bad DNS names
		- just says “sorry, you messed up, try again.”
	- 2. Encrypt DNS requests - very secure, manefests as:
		- setting up a DNS server in your home/office
		- configure that to create an encrypted connection to public DNS server
		- can be overkill for home/office - but pays to use on phones
		- (he uses CloudFlare)
			- creates a VPN connection from his phone to just his DNS server
			- DNS requests being sent encrypted to public, non-logging, DNS server

CompTIA’s 7 step process:
— 1. Identify and research malware symptoms
— 2. Quarantine the infected systems
	- get it off the network - unplug cable, disable wireless
— 3. Disable System Restore (in Windows) - stop Windows from automatically firing up System Restore in certain situations (e.g. shutting system down will often create a restore point) so you don’t have automated restore points that are pre-infected.
— 4. Remediate the infected systems
	- 4.a. Update the anti-malware software
		- anti-malware needs definition files that have the signatures for malware
		- normally when updating OS, these updates take place as well
			- even 3rd party tools - either automatically or through a pop-up
	- 4.b. Scan and use removal techniques (safe mode, pre-installation environment)
		- goal should be to always have anti-malware running to stop from ever entering system
		- constantly running automatically; when getting symptoms, run scan
		- second way is to have some type of bootable media (vs booting into Windows)
		- then it goes into your system and does a check
— 5. Schedule scans and run updates 
	- he chooses ~1x/wk at 3am
	- use Task Scheduler to set up (if not already pre-set up)
	- zero day malware can be a pain
	- update comes along, scan catches it, and you don’t get anything but a log file telling you
— 6. (Re-)Enable System Restore and create a restore point (in Windows)
	- probably want to delete the previous week/month of restore points
— 7. Educate the end user

**He runs anti-malware all the time, but if really thinks he has a piece of malware on his system will use different tools that create Windows pre-installation environments, create a bootable media, and boot into it to clean his system - won’t name brands - choice in anti-malware tools “changes like the wind”

Social Engineering:
— the use of deception to get people to give away personal/confidential information that they wouldn’t normally give away - “It turns out we are the greatest threats to our networks… We all like to think that pale hackers typing away in basements pose the greates threat to our networks… It’s an evil we can understand, a threat that feels contained… but we live in a world where evil-doers prey on our virtues and turn them against us…”

— telephone scams - e.g. IT department calling to collect passwords for a company-wide change
— Phishing - emails (or websites) from malicious elements pretending to be authorities, hoping for users to hand over passwords - can also manefest as a website that comes up while in a coffee shop asking for login credentials to your bank account, etc.
— Spear Phishing - primarily emails; are directed towards a specific person vs phishing directed towards anybody. (e.g. “Dear Mike Meyers, were having problems with your bank account, please call this number or enter your username and password so we can correct this…”)
— Tailgating - malicious malcontents follow legitimate employees through locked doors, pretending they belong - after gaining access to a building all they have to do is wait for an employee to take a bathroom break to gain unauthorized access to an otherwise impenetrable network.
— Shoulder Surfing - just as easy to stand behind and watch you type passwords, access secure documents, and communicate with other employees.
— Dumpster Diving - even the most tightly controlled offices often have an achilles heel - compaines have toppled and individuals have had identities stolen all by being careless with their refuse - shred all trash you don’t want prying eyes to see, “after all, one man’s trash, is another man’s treasure…”


Licencing:
(obj 4.6 - Explain the process for addressing prohibited content/activity, and privacy, licencing, and policy concepts)
— Bill Gates invented the concept of software licencing - “An Open Letter to Hobbyists”
	- Required licensing fee for the BASIC programming language

— End-user license agreement (EULA)
	- grant you a licence, not ownership
	- defines who the owner is
	- defines how you can use the software

— Digital rights management (DRM) - attempt to protect the different types of copywrite associated with audio and vides (movies more than anything else)
	- HDMI - licencing given by the HDMI organization, done through the hardware itself

— Commercial licence - someone writes code, compiles it, turns it into an executable and puts it out to the world as such - you cannot reverse engineer it; only use within the specifications of the EULA
	- Personal licence - given licence on a per-user basis
	- Enterprise licence - number of copies licenced to a single organization
		- can licence to every computer, but not everybody using (e.g. MS Office) all the time
		- if can guarantee only certain num copies open at once
		- can have office with tons more copies downloaded
		- (Windows Server, etc.) have licencing controls that allow this to happen
— Open-source
	- GNU General Personal licence (GNU GPL)
		- specifies that if you compile something, have to provide the original source code
			- either with it, or when asked
		- if you add to something, have to attribute “upon who’s shoulders I have stood upon” 

— Don’t instantly assume open-source means free and commercial means you have to pay for it
	- release a piece of software and give away, but still propriatary (not gonna give source code)
	- have open-source software w/ commercial/sold features or sell services with it
		- (e.g. Red Hat releases Linux distro free, but sells online support)

— Per-processor licence for Windows - any workstation version of Windows (Home, Pro) can be used on any computer with up to 2 physical CPUs on it - been around for decades
	- a problem for Windows when one computer has 2 8-core CPUs - functionally 16 CPUs
	- also true for server systems, not uncommon for motherboards to have 2,4,8 physical CPUs with multiple cores in each - makes it more expensive to have a server w/ 4x 4-core CPUs vs buying one with 2x 8-core CPUs (**watch for questions like this)
	- Windows Server today has a per-core licencing agreement
	- can be required to buy multiple licences for a single system
	- installing a VM with a Windows OS counts against licence agreement (“Thanks Microsoft!”)
	- “consider Linux for your server needs”


Incident Response:
— an incident is defined by whatever your organization says an incident is
— Incident response
— 1. Know your responsibility - will often only have responsibility to report an incident to a hotline/desk, but if you have more…
— 2. Identify the problem - will often be the first to recognize an incident has taken place
	- Report Through Proper channels
	- Data / Device preservation (if you are the person supposed to)
		- document the device that whatever took place on
		- quarantine the device (e.g. take offline)
		- (some organizations will have policies like never unplug the computer)
	- Use of documentation
		- document the surroundings as specified by organization
		- (e.g. take pictures, note other people around, etc.)
	- Document changes
		- (e.g. currently running MS Word, something happens, and a change takes place)
		- must be specific (often using time stamps, employee serial numbers, etc.)
		- “sometimes you have to document your documentation changes”
— 3. Keep chain of custody
	- talking now more along the lines of issues of legality (vs simple malware found)
	- Tracking evidence - suddenly things like computers can become evidence
		- organization will define how you handle
		- (e.g. unplug device and take to server room)
	- Document process


Environmental Controls:
(obj 4.5 - Explain environmental impacts and appropriate controls)

— Compliance to government regulations 
	- OCEA, industry standards, best practices, traditions, etc.
	- (e.g. proper temperatures or acceptable humidities you can work at)

— Materials safety data sheet (MSDS)
	- check with for how to handle, environmental impacts, how to dispose of
	- will be general - tell you it’s poisionous/toxic, but not the number to call

— Temperature and humidity levels - be aware of them - good rule of thumb: if you’re uncomfortable working in your environment, your computer probably is too. If you’re comfortable, your computer would probably be happier if it were even colder and dryer.
	- AC going out can have a huge impact on printer, server not in a server room
	- turning them off can be really important
— Proper ventilation
	- even in a nice, cool room, can have hot spots under desks or in enclosures
	- Dust and debris - can create shorts and cause lots of problems
		- seen in construction sites, smokers, etc.
		- enclosures - can filter and protect
		- air filters / mask - protect yourself
		- compressed air - open system and blow dust away
		- vacuums - be careful, home vaccums generate tons of static charge
			- anti-static vacuum - can be expensive, but prevent static destroying system

— Battery backup - if a critical system
— Surge suppressor - always have - cheap and work well


________________________________________________________________
Chapter 28: Operational Procedures

Documents You Need to Know:
(obj 4.1 - Compare and contrast best practices associated with types of documentation)
— Network topology diagrams - documenting computers, switches, printer, routers, etc
	- Solar Winds - company that does inventory management through software
	- Logical diagrams - drawing of devices w/ network IDs / IP addresses of devices
	- Physical diagrams - drawing of floor plan w/ cable runs, types, distribution frame

— Knowledge Base / Articles - databases of organized knowledge of OSes, software, tools, etc.
	- Microsoft, Cisco, AWS, etc.
	- use these sites vs google if exist

— Regulatory and Compliance policy
	- Laws
	- Industry standards
	- Best practices
	- Traditions
	- Common sense

— Policies
	- Acceptable Use policy - defines what you can/can’t do with company equipment
		- certain websites, taking home company hardware
	- Password policy
		- minimum length, type of complexity, how often to chage, who’s in charge of this, where to store passwords

— Inventory management - 
	- asset tags - Barcodes on stickers used to identify devices


Data You Need to Know:
— Personally identifiable information (PII) - e.g. SSN, phone number, address
— Protected health information (PHI) - e.g. blood type, what doctor has been treating for, vaccines
	- strict laws protecting this information from getting out and into the wrong hands
	
— EU General Data Protection Regulation (GDPR) - rule that you as a person have the right to control the information people gather from you (maily web).

— Payment Card Industry Data Security Standard (PCI DSS) - from the different banks that issue credit cards - if you want to accept credit cards, you have a responsibility towards that data.
	- not a lot of responsibility as a small business
	- really comes into play in companies that produce card swipers
	- or large corperations that provide merchandising services for websites

— As an A+ certified technician, not expected to be the security expert, just need to be aware when doing things like putting info on thumb drives or file permissions. you have legal obligation to protect this data and there are civil and legal repercussions that come with the way you deal with it. When in doubt, talk to supervisors, and sometimes get it in writing because it might save you.


Change Management:
(obj 4.2 - Given a scenario, implement basic change management best practices)
— is the organized, smart, carefully set up system that allows changes to take place within enterprises that keeps them from losing money, equipment, people, etc.

— Change board - meets monthly/quartely to look at requests for changes and approve/disapprove

— Documented business processes - must document what change you want to make and how it will improve the way the business practices (best if you can put expected cost behind it).
	- e.g. putting new monitors on a business group
— Purpose of the change - generally “to improve productivity”
— Scope of the change - “is this going to effect just the accounting department? Dallas office? or European offices as well?”
— Risk analysis - what are the downsides to making the change? - e.g. how long will it take to make the change? training involved? possibility of incompatability?

— Plan for change - assuming tenative approval, how is the equipment going to be bought in? who’s loading dock is going to be picking it up? who is going to be assigned to install it? doing it over the weekend so the accounting department isn’t down? overnight? how are we going to handle training?

— End-user acceptance - don’t expect everyone in accounting dept will be happy with new monitors without giving some type of warning. Give the end-users a buy in so they understand it and their management is on board - that way when the change takes place, everybody is happy.

— Backout plan - okay, it didn’t work, we made a mistake, how can we get everyone in the accounting department back to where they were before? keep old monitors in a warehouse for 90 days? who will be the people to replace it? what costs are going to be absorbed by which department?

— Document changes - no matter what takes place, always go through the process after changes have taken place and document what has happened.
— Lessons learned - what was our real takeaway from this particular change?

(**quiz - “History of changes is not a major focus of the change management procedure. Documenting past practices, the purpose of the proposed changes, and associated risks are all elements of the change management process.”)


The Zen of Backup:
(obj 4.3 - Given a scenario, implement basic disaster prevention and recovery methods)
— Disaster recovery - what if we lose our servers (or something like that)?
	- not really what CompTIA is after with the A+ exam, more-so on individual system basis

— Backup and recovery - disaster recovery starts and ends with restorable backups
	- smart devices - use some kind of built-in backup tool (generally Cloud based)
	- desktop OSes:
	- Control Panel -> Backup and Restore (Windows 7)
		- can chooose to save locally or on a network
		- “Let Windows choose” - Image-level backup - entire drive - OS, apps, data
		- “Let me choose” - File-level backup - vs backing up OS or applications
			- old fashioned - problem with system? will still have to reinstall Windows
			- rather use thumb drive and backup personal info there

— Backup testing - a failed backup can be a big problem
	- not worried about if using a Cloud-level backup

— Cloud storage - 
	- Windows OneDrive -> Settings -> “Auto Save”
		- choose Desktop, Pictures, and/or Documents
	- convenient, but can eat up bandwith

— Account recovery options - be aware on an account-by-account basis
	- especially when using two-factor authentication
	- secondary phone numbers available, printed out backup codes, etc.


Recycling and Data Destruction:
(obj 4.4)
— more than just being a good denizen of the planet

— Batteries
	- alkaline batteries (e.g. AA) cannot be re-used or recycled.
	- lithium-ion batteries have very specific recycling procedures
		- have heavy metals and toxins that can be safely recycled
— Toner cartridges - can be refilled by recycler
— CRT monitors - metals can be taken out
— Cell phones and tablets - plenty of people who will buy - just make sure you delete accounts and do a factory reset beforehand.

— Hard drives
	- Low-level format - old technique - used on HDDs (not SSDs)
		- done at the factory - sectors are preassigned
		- you cannot low level format these, if told so, wrong (including A+ exam)	- Standard format - great way to remove data, but
		- doesn’t mean all info is deleted
		- got rid of cataloguing and indexing so difficult to get to the data
	- Drive wipe / overwrite - writing data over and over on the drive
		- gets rid of whatever was there before
		- “zero wipe” - write nothing but zeros
		- “military standard wiping rules” - write all zeros, then random 0/1 patterns
			- usually 7x
			- in theory, a drive rewritten on less than 7x can still be recovered
	- Degaussing machine - massive magnetic field goes through the drive and renders unusable
	- Shredder
	- Incineration
	- Certificate of Destruction
		- companies exist that will come to you with equipment to destroy and verify work
	- “just get an old drill, punch three holes in it, and nobody’s gonna ever read that data”



