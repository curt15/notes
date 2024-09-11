
In Linux:
- \# - comments (bash scripting)
- echo - put something up on the screen
- sudo - command to run command as superuser
	- can’t right-click to “Run as Administrator” in Linux
	- su - allows you to type password once and run everythin as a superuser (considered a bad idea)

- ls - shows directories and files - equivalent to dir
	- ls -l - shows all files and folders w/ permissions and owner name
		- switches use a dash in the Linux world
- clear - clears screen
- man commandname - shows manual of command including available switches


Navigating the CLI:
In Windows:
- starts you in the home directory (of your individual user)
- Directories denoted by a backslash (“\”)
- . - dot - where you are right now
- .. - double dot - previous folder upstream
- cd - change directory
	- cd .. - move one dir back
	- cd \ - moves you to the root directory - holds core files 
	- cd\windows - moves you to this windows folder, from the root directory
		- can include a space or not
		- is a shortcut for cd c:\Windows - because you’re already in the C drive
	- cd \Users\michaelm - moving multiple levels of dirs in one command
	- cd Temp - don’t need the “\” if you’re in the dir that “Temp” exists in
- d: - to get to a different drive, type drive letter followed by a colon
	- you don’t use cd here
	- command prompt will take you back to the dir you were in when you left the previous drive

	
On Linux:
- Linux doesn’t use a drive letter concept - volumes are mounted as folders under root directory “/“
- Directories denoted by a foreward slash (“/“)
- Tab - on both systems autocompletes
- cd - same command, but Linux cares about capitalization
	- cd ~ - takes you back to home directory
	- cd / - takes you to root directory
- pwd - print working directory - shows where you are

Working with Folders:
On Windows:
- md foldername - make directory with desired name
	- use command in dir you want it to be
	- Windows does not look at capitalization
	- cannot have “Mike” and “mike” directories in the same folder
	- can have a dir called “Mike” and a sub-dir called “mike”
- rd foldername - remove directory (if empty)
	- rd /s - use this switch to remove directories and its contents

On Linux:
- mkdir foldername - make directory with desired name
	- Bash cares about capitalization; can make dir “Mike” and “mike”
- rmdir foldername - remove directory (if empty)
- rm -r foldername -remove directory and its contents


Working with Files:
On Windows:
- \*.ext - asterisk is a wild-card - means anything with extension type
- \*.\* - star-dot-star - everything

- del filename.txt - delete a file
	- not going to a recycle bin - must be careful
	- del *.txt - delete everything in current dir with extension
- copy filename.txt k:\  - copy a file to destination path
- move filename.txt k:\ - moves file - deletes the original after copying
- important to look in the destination to make sure everything copied/moved correctly
- If copy or move sees a file that exists already with the same name in destination path will give a warning and ask to confirm (Y/N/All)

On Linux:
- rm filename.txt - remove file
	- linux uses the same asterick wildcard…
	- rm * - remove everything in directory
	- rm M* - remove everything beginning with “M” from directory
- cp filename.txt Path/to/destination - copy file to destination
- mv filename.txt Path/to/destination - move file to destination

	
Working with Drives:
On Windows:
- format e: /FS:NTFS - format drive with selected format type
	- format e: /FS:NTFS /Q - quick format
	- format command is only available with administrative privileges
	- Commands available with standard privileges vs. administrative privileges (objective term)
	** be careful - can format c: drive and wipe Windows

- chkdsk - “check disk” - does error correction by checking file table and anything marked as bad is skipped over, and anything marked as good says it’s good
	- not helpful by itself
	- chkdsk /f - this switch actually “fixes”

- sfc /scannow - System File Checker - looks at backup store vs working files
	- if finds any bad copies, will write over them from the store

- dism /online /cleanup-image /restorehealth - Deployment Image Servicing & Management - goes online to Microsoft, finds version you’re running, and compares to your system store - and if any problems found, fixes them.

- always run sfc /scannow & dism as a pair - run sfc, run dism - now we assume everything ok, but run sfc a second time to make sure everything is happy - “you literally cannot have bad system files unless there’s some horrible corruption on your hard drive by using this methodology; it will fix everything, everytime, and it’s absolutely amazing.”

- diskpart - command-line tool - ability to do anything to mass storage
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
- xcopy - heavy-lifting copy - designed to copy files, directories,
	- features like verify the copy as it copies
	- xcopy c:\backup x: /s /v /h
		- xcopy dir_to_move move_to_loc /switches
		- /s - copy everything in sub-directories
		- /v - verify every copy
		- /h - don’t move hidden files
- robocopy - nearly identical to xcopy - designed to handle more verification and speed
	- robocopy c:\backup x: /s /xa:h
		- /s - same as xcopy
		- /xa:h - don’t move hidden
	- both xcopy and robocopy are network aware, e.g.:
	- robocopy D:\VMs “\\Server\vmbackup” - change destination to UNC value

On Linux:
- dd - Linux’s heavy-lifting copy - a bit-by-bit copier
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
- shutdown - shuts down computer
	- /s - just shut it down
	- /r - shut down and restart the system
	- can use switches to time when you want the shutdown to take place, etc.

- tasklist - lists all processes running on system
- taskkill process - kill process by name or process ID
	- taskkill /PID 2704
- a group policy (set by domain administrator) trumps local security policies
- gpupdate - queries server and forces updates to system from group policies
- gpresult /R - outputs applied group policies from the gpupdate
	- /R - smallest output that can generated

Advanced Linux Commands:
(obj 1.9)
- shutdown - shuts down computer - give you one minute by default
	- shutdown -c - cancels shutdown
	- shutdown -r - shuts down computer in one minute and reboots
	- shutdown now
- apt-get - repository to get almost any program available to do anything you want
 	- used in Debian based Linux distros (e.g. Ubuntu)
	- sudo apt-get update - update onboard repository to knows current versions of avail programs
		- whenever you install Debian based Linux, run this
	- sudo apt-get install joe - downloads and installs program “joe”
	- sudo apt-get upgrade - upgrades every application on system
		- can specific specific program by adding name to the end
	- sudo apt-get remove joe - delete/uninstall specific progra
	- apt-get is fairly depreciated at this point, but still works 99% of the time
	- apt - more commoly used tool for this now (**but know apt-get for exam)

- ps - check running processes and displays all of current logged in user
	- gives you process ID and name of the program
	- ps aux - show all processes from system, all users, and with details
		- shows USER, PID, %CPU, terminal/moniter using, START, COMMAND running it
	- ps aux | grep “libre” - 
		- “|” - pipe - funnel output to the next command
		- “grep” - global regular expression print the string given
	- kill 13482 - kill the process at the process ID given
		- can kill multiple processes depending on dependancy
	
- vi - text editor - ancient
	- (**on the exam, but 1000 better text editors out there)
	- i - switch to input mode
	- … - tons of other commands to move cursor, etc.

Command-Line Permissions:
(obj 1.4)
On Windows:
- icacls - program to change NTFS permissions
	- icacls folderorfiletoapplyto /grant Mike:F - give full control to the user Mike
	- (** not on the exam)

On Linux:
- chmod - Linux command to change permission
	- ls -l - to check permissions
		- -rwxrwxrwx 1 fred mike
		- RWX for User, Group, Other; owner username; filename
		- if off, letter will be replaced with a “-“ (dash)
		- 421 - 4+2+1 = 7
	- chmod 777 filename - gives User, Group, and Other RWX permissions
	- chmod 664 filename - gives User and Group RX, and Other R permissions
- chown - change owner
	- ls -l
		-  -rw-rw-r-- 1 mike timmy
	- sudo chown fred timmy - change owner to fred
	- ls -l
		- -rw-rw-r-- 1 fred timmy
- passwd - change password on account currently logged into
	- sudo passwd
		- “Enter new UNIX password:”
		- “Retype new UNIX password:”
		- “passwd: password updated successfully”
** Need to know Linux permission commands for exam


Chapter 19: Local Area Networking
- netstat - command that shows statistics for all network connections on system
	- columns = Proto (protocol), Local Address (IP + port num), Foreign Address, State
	- shows TCP and UDP (shows ICM but goes quick) connections
	- netstat -n - gets rid of words and gives raw numbers
	- netstat -a -n - see everything (“all”) in numeric form (includes where things are listening)
	- will show a bunch of stuff even if not on browser, skype call, etc.
	- is Windows telemetry - checking for updates, listening for Cortana to update voice file online
	- when connected to drive on local network, Foreign Address = your_ip:445 (??)
	- can be a sign of malware if things are listening on ports you don’t know
	- sometimes things like network card drivers will listen on Port 80
	
- TCPView - a graphical netstat tool (by Mark Russinovich @sysinternals)
	- green highlight - on new connections establishing (e.g. opening a browser)
	- red highlight - shows the CLOSE_WAIT that are disconnecting
	- can right-click -> “End Process…”


working with Workgroups:
- whoami - command to see who you’re logged in as

Net Command:
(obj 1.4)
- net - a Windows command - by itself, gives an idea of the net commands you can type
- net view - shows all computers on your network
- net view mikewin10pc - shows shares on a particular system
- net share shareit=c:\stuff - make files/folders sharable to others
	- “shareit” - a selected share name
- net share - view everything shared from your system
- net use v: \\mikewin10pc\mike - connected to a shared item
	- “v:” - selected drive letter to map to
- net user - view users on the system
- net user tammy total /add - add a user to the system
	- “tammy” - selected username
	- “total” - selected password
- net user tammy /delete - remove a user from the system

— tons of other net commands exist (e.g. can set times users are able to log in) - do some research - different versons of Windows often have little tweaks to get the net command working right

- netstat -n - Telnet (port 29) connections visible
	
- ifconfig /all - “know your network” - document your network ID, router, DNS, 

- traceroute (Linux/Mac)

- tracert www.ibm.com “run before things go bad, so when it does, you know what supposed to look like”

watch for multiple layers of routers before your request actually exits network.

seeing only one server hop in the future = issue probably between the internal & gateway routers

**exam tip: lots of tools you can get for all kinds of things. 95% of the time can fix all network problems with ping, traceroute, and  ipconfig - practice with them, will see on exam.

** Kali Linux = Debian-derived distro designed for digital forensics and penetration testing.
	- ophcrack = rainbow table tool