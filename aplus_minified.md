1. Safety & Professionalism:

2. The Visible Computer:

3. Microprocessors:
CPU:
— Resource Monitor (Windows); Activity Monitor (macOS)

4. RAM:
— SPD Chip (serial presence detect) - allows system to querey the RAM chip for capacity, speed, technology, make/model
	- CPU-Z - tool for “timing table” used for overclocking

_________________________________________________________________
5. Firmware:

— Basic Input/Output Services (BIOS)
	- original BIOS (ancient) = 16-bit
	- Unified Extensible Firmware Interface (UEFI) BIOS = the updated BIOS

— firmware - means that code is burned onto a chip (nonvolatile media) vs software copied onto magnetic/electronic media
— m-BIOS & b-BIOS (backup) = 2 copies

— Power-On Selt-Test (POST routines)
	- when booting, the power-good wire (when recieving enough electricity) will signal to run
	- “if you can hear me, check yourself out” -> “I’m great” w/ little beep
	- beep codes - primitive POST error codes 
	- if POST gets successful video output will give display codes instead
	- POST cards - show 2-digit hexadecimal read out if video fails

— System Setup (CMOS Utility = complimentary metal-oxide-semiconductor)
	- interface to make changes to the changable part of the BIOS
	- CPU frequencies, RAM timings, BIOS passwords, boot drive options, overclocking, etc.
	- onboard devices configuration, disable USB connectors, disable network cards, serial port configuration 

— “flashing your BIOS” = check for update
— firmware is the last place you would check for problems - pretty safe as long as not abused
— flashing the ROM updates the firmware on flash chip - doing improperly can be the worst mistake
	- make sure good power
	- BIOS flash image - make sure have complete back up of flash file
	- know why you’re doing it (prepare for faster available tech, fix bugs, etc.
	- often comes with 2 bias chips in case of error
— Real-time Clock (RTC) = single, flash, ROM (Read Only Memory) chips that can be “flashed” to reprogram/update BIOS
	- RTCs in a network must be synchronized (milisecond closeness) or won’t even boot up
— CMOS battery - provides back up power to keep clock; losing time / slowing down can lead to system not recognizing setup instructions / passwords if dies ($2)

— Biggest problem in BIOS is people changing settings - choose default to reset

______
6. Motherboards:

form factors:
(industry defined standards of specific dimensions for motherboards, cases, holes/mounting, etc)
— ATX - 12x9.6in - biggest common form factor
— MicroATX - 9.6x9.6in
— Mini-ITX - smallest common form factor
— ITX form factor - larger mini-ITX; mostly unused

— I/O area - external connectors
— I/O shield - shape is extremely fixed

Chipsets:
(highly specialized single-purpose chips -> dedicated chips that take on specific jobs)
— chipset = most critical part in determining what a motherboard can do (define amount of RAM, speed, num USBs, etc.)
— Northbridge & Southbridge
	- N: CPU, RAM, video interface (faster stuff)
	- S: hard drives, keyboards, USB, etc. (slower stuff)
	- today’s CPUs take over all Northbridge functions
	- chipset = Southbridge

— SATA cables - connect HDDs, SSDs, and optical media to the motherboard
— power connectors
	- capacitors - voltage regulators (breaks down voltage) - hundreds of differing power needs
— USB connectors (via “dongles”)
	- serial port
— VGA connector
— 3- (continuous) or 4-pin (PMW) connectors for fans
	- PMW connectors allow CPU to tell fans when to turn on/off
	- SpeedFan - software to configure fans

— PCIe expansion slots - dominant type of expansion slot using serial connections (1 wire sends data, 1 wire receives) - offers multiple lanes
— PCI - PCIe precursor - 32-bit wide bus (slower to send 32 pieces of data on 32 wires vs 1)
— parallel vs serial - when recieving data has to check if have all (creating latency) vs serial
— 16 lane PCIe - graphics (video) cards (vs single lane or 4-lane)

case:
— pass throughs - holes in cases for cable management
— standout - standardized screws/holes to place motherboard

______
7. Power Supply:

— ATX style power supply = predominent used in PCs
— have massive capacitors that act as primary surge suppressors for system
— red slider - european (230v) vs US (110v)
	- rare today (autosensing)

— step-down transformer - convert AC -> DC power
— ATX power connector - 20-pin connector + 4 more pins
— ATX 12B power connector - provides power to the CPU

— Molex - general term for 2 piece pin + socket interconnection
— mini connector - used for floppy originally
— SATA power connector
— PCIe connector

— rule: get a PSU w/ a little more wattage (volts x amps) than your system needs
— 1500W = highest commonly found
— even 60% efficiency considered good (lost to heat, resistance, etc.)
	- e.g. 575W @ room temp and 300W otherwise
— 80+ ratings = high efficiency power supplies

— Modular Power Supply = less cable cluter (convenience vs potential efficiency reduction)

cooling your PC:
— heat sink - anything that can take heat from another device
	- on CPU: copper block w/ hollow tubes + cooling fins = heat -> fins -> dissipate to enviro
— fans = active cooling
	- small fans tend to be louder than large fans (spin faster to move same air)
— liquid cooling = quietest solution
— overheat = reboots

troubleshooting PSUs:
— PSUs are the #1 computer component most likely to die - either quickly (smoke, burning plastic smell) or slowly (intermittant problems like reboot) - swap out when symptoms present
— power supply tester = best way to tell
— bent paper clip green to black = test if fan turns on
— Multimeter (V~) = AC
— Multimeter (V—) = DC
	- set to lowest closest 12v
	- don’t need CPU installed in this case

troubleshooting core components:
— If new build (minus hard drive) and BIOS says nothing to boot from - means CPU is mounted properly
— If RAM in the wrong place - first boot gives beep code
— If CPU overheating - causes shutdowns and reboots
— If on initial setup and no noise, nothing on screen, but fans on - start over!
	- incorrectly installed CPU or RAM
— If system lock-ups (gone through System Setup, made a mistake, nothing is working) - clear CMOS jumper - use metal to short 2 small posts (on every motherboard) for ~30s to reset System Settings to default
— If loud noises - fans in contact w/ cables or obvious if from PSU
— If LEDs - system recognizes good RAM installed (no standardization of)
— If smoke - unplug system and use fire extinguisher if necessary

— System Setup - good place to check RAM
— WinRe live CD / thumbdrive - good place to confirm if good RAM

______
8. Mass Storage Technologies:

— all storage devices have some hundreds of thousands of “logical atoms”
— Optical media - tracks = ~1000 bytes
— Magnetic media - sectors = ~512 bytes
— Solid state - blocks = ~1000 bytes (blocks -> “pages”)

— Logical block addressing (LBA) = controller circuitry + OS -> allocating “blocks”
	- e.g. 4TB HD - each block = 4096 bytes (0-1 billion blocks)

— drive capacity?

physical size:
- 5.25-inch
- 3.5-inch - dominant form
- 2.5-inch - primarily laptops (/ large systems)
- 1.8-inch - popular w/ SSD, but shortlived
- m.2-format mass storage - dominant SSD today

— Hard disk drive (HDD) - spinning platters store data via magnetism and read/write heads + tiny arm  w/in nanometers of platter to read data.
— SSDs are much faster than HDDs

— Advanced Technology Attachment (ATA) - language to speak to drives

— Serial ATA (SATA) - all data moves in sequence (serial) over a single wire
	- small connector = data; large connector = power
	- eSATA - connection for SATA -> external case filled with drives (eSATA expansion card)

— Non-Volatile Memory Express (NVMe) - fastest drive interface; traditionally found in M.2
	- system takes the job of the hard drive controller (/ LBA)

old types of mass storage:
— Parallel ATA (PATA) was the old interface (rare today, not on exam…)
	- 2-4 hard drives in a system via ribbon cable
— Small Computer System Interface (SCSI) - “skuzzy”
	- sometimes 7, sometimes 15 drives in a system via wider ribbon
— Serial Attached SCSI (SAS) - similar to SATA, though not entirely compatable
— ISCSI - Internet SCSI (SCSI via ethernet cable) - only typical in server situations now


— Check System Setup to confirm correct connection when installing drives

______
9. Implementing Mass Storage:

— Redundant Array of Inexpensive Disks (RAID) - chaining drives together for speed and data redundancy - the OS sees a single drive letter / path for the multi-drive RAID.
— RAID 0 (striping) - each file saves in pieces, alternating between drives
	- advantage: speed
	- requires: minimum of 2 drives
	- disadvantage: no data safety - if either drive dies, lose everything
— RAID 1 (mirroring) - file saves in pieces, but completely on both (each) drive
	- advantage: redundancy (data safety)
	- requires: 2-4 drives
	- disadvantage: slow - complete data saved twice

— RAID 5 (striping w/ parity) - file is saved in pieces on the first 2 drives, then through “interesting binary math”, a parity file (that is the same size as the individual pieces combined is created. If either drive dies, can reverse the math and recreate the data.
	- requires: 3+ drives
	- advantage: pretty good speed & redundancy of data
	- disadvantage: can only lose exactly one drive; more and data won’t be rebuildable
— RAID 6 - file is saved in pieces on first 2 drives, then a parity file is created and stored on the other 2 drives.
	- requires: 4(+) drives
	- advantage: more redundancy - can lose up to 2 drives
	- downside: more expensive in drive real estate

— RAID 10 (striping mirrors) - 2 mirrored pairs that take alternating pieces of the files
	- requires: 4+ drives (2 pairs of drives)
	- advantage: can lose 1 drive from each side of the mirror
	- disadvantage: if lost a complete mirror side pair - lost half of the stripe - data lost
— RAID 0+1 (raiding stripes) - stripe on first pair of drives, then mirror on the other pair
	- requires: 4+ drives (2 pairs of drives)
	- advantage: can lose one complete striped pair on either side
	- disadvantage: if lost one drive on each side - cannot rebuild the mirror - data lost

— hardware RAID - dedicated controller built into motherboard (most top boards have) / expansion card - config through System Setup or optional BIOS
— software RAID - done through OS itself
— hot spare / swappable drive - sometimes have the option to keep blank drive waiting to automatically rebuild the array if a drive fails

mass storage troubleshooting:
— Rule 1: Back it up
— Rule 2: Mental re-install
— Rule 3: Triple check - most problems here are via technician error vs broken drives

______
10. Essential Peripherals:

optical media:
— Compact Disc (CD) - og designed for music - microscopic pits read by a laser allows storage/retrival of tons of 1’s & 0’s in a tiny space.
	- capacity: 74 min & 80 min
— CD-ROM (compact disc/read-only memory) - stores data in the CD File System (CDFS)
	- capacity: 650-700MB
— CD-R (CD-recordable) - 
	- capacity: 650-700MB
— CD-RW (CD-rewritable) - 
	- capacity: 650-700MB

— DVD (digital video/“versatile” disc) - og designed for movies
	- Dual-layer (DL) format - 2 lasers reading different layers
	- Double-sided (DS) format - silver on both sides
	- capacities:
		- DVD-5 (12cm; SS/SL) = 4.37GB (more than 2hrs of video)
		- DVD-9 (12cm; SS/DL) = 7.95GB (about 4hrs of video)
		- DVD-10 (12cm; DS/SL) = 8.74GB (about 4.5hrs of video)
		- DVD-18 (12cm; DS/DL) = 15.90GB (more than 8hrs of video)
— DVD-ROM (DVD/read-only memory) - mastered form of DVD - most common today
— DVD+R; DVD-R; DVD+RW; DVD-RW

— Blu-ray Disc - highest capacity read/write format - designed for High Def video
	- BD-ROM, BD-DS/SS; BD-DL/SL; BD-RE (recordable erasable)
	- capacities:
		- standard disc (12cm) = 25GB (SL) / 50 GB (DL)
		- mini disc (8cm) = 7.8GB (SL) / 15.6GB (DL)

— optical media drives use SATA cables (are ATA devices)


USB (Universal Serial Bus):
— USB 1.1 = 1.5 Mbps & 12 Mbps
	- color: white
— USB 2.0 = 480 Mbps (fast enough for file transfer on thumb drives)
	- color: black
— USB 3.0 = 5 Gbps (compatability issues)
	- color: blue
— USB 3.1 Gen 1 = 5 Gbps (fix)
	- color: blue
— USB 3.1 Gen 2 = 10 Gbps (current top speed)
	- color: teal (/green)
** Mbps = Megabits/sec; Gbps = Gigabits/sec

— USB Type-A connector - “famous, original”
— USB Type-B connector - plug into devices (scanners, etc.)

— USB mini-B - plug into smaller devices (cameras, etc.)
	 - shape: butterfly
— USB micro-B - popular in Android phones
— USB 3.0 micro-B - backwards compatable port
	- shape: has a notch, longer

— USB Type-C - capable of incredibly high-speed data transfer
	- shape: reversable design

— USB controller - built into motherboard to connect - each version has it’s own; are backwards compatable at the speed of the port.

— A connectors = downstream
— B connectors = upstream
** USB-C eliminates the concept of up/downstream

— With USB 3.1, can have up to 127 devices on one Root Hub
— “signed drivers” - released by Microsoft to say “I’m not carrying malware.”
— HID (human interface device) - core device drivers that exist on system to ensure keyboard+mouse always work
— USB can be a big security risk (keyloggers) - fix via USB port disabling / USB lock


— Thunderbolt - PCIe & DisplayPort combined into one port - can drive x6 monitors, charge, and data transfer
— Thunderbolt 1 = 10 Gbits/s (x2 channels = 20 Gbits/s) - mini DisplayPort
— Thunderbolt 2 = 20 Gbits/s - mini DisplayPort
— Thunderbolt 3 = 40 Gbits/s - USB-C (a lot of compatability w/ above)

— Lightening - Apple’s proprietary port for iOS charging + data transfer = 30 Gbits/s


keyboards and mice:
— USB 1.1, wireless (via dongle), or PS/2 connector (purple = keyboard; green = mouse)
— game controllers typically come w/ propriatary connector + dongle -> USB
— KVM switch (keyboard, video, mouse) - allows input devices and a monitor to share btwn multiple physical computers, toggled btwn via buttons

sight and sound:
— stereo - min x2 speakers
— 2.1 speaker system = 2 speakers + subwoofer (… 4.1, 5.1, 7.1)

— blue = aux in; green = front 2 stereo; pink = mic; silver = side speakers;
— black = rear speakers; orange = subwoofer / center channel (for dialog, etc.)

— S/PDIF (Sony/Philips Digital Interface) - optical audio
— 3.5mm jacks

— headsets w or w/out mic
— webcams

— better sound card = better sound

readers and scanners:
— smart cards - stores credentials that help authenticate (credit card RFID, pre-passcode, etc.)
— magnetic reader - “swipe” line on credit cards
— flash memory reader - SD, mini-SD, micro-SD cards - no difference other than physical size
	- Olympus xD Picture Card - used in Olympus cameras (**)
- scanners - scan physical documents
	- flatbed scanner
	- ADF (automatic document reader)
- barcode / QR scanners - printed B&W; stores numeric/alphanumeric info - used in inventory, etc.
	- all smart phones have apps that allow reading

using expansion cards:
— sound cards, network interface cards, USB expansion slots, eSATA cards, extra PCIe expansion slots, etc.
— usually identical steps - follow manual: install driver(s), check device manager, install additional software (if necessary/wanted); choose placement based on airflow and needed connections

______
11. Building a PC:

the right PC for the job:
— Thick Client - standard/basic office computer
	- meets recommended requirements for selected OS
	- middle of the road motherboard + matching CPU
	- desktop applications = Microsoft Office (or alternatives)
— Thin Client - rarely counts on internal storage
	** meets recommended requirements for selected OS (for him: go beyond)
	- motherboard: select for network connectivity (e.g. Gigabit)
	- basic applications = MS Word or specialized in house applications

— Graphic/CAD/CAM Design Workstation
	- good, powerful, multi-core processor (CPU) (e.g. i9)
	- high-end video (GPU)
	- maximum RAM

— Virtualization Workstation
	- maximum RAM and CPU cores - each VM needs RAM for OS + jobs that it performs
	- high-end motherboard & CPU
	- he adds: storage - VMs take up a lot of space - extra HDDs store them when not using

— NAS (network attached storage) - file sharing (media streaming / traditional files via NTFS permissions)
	- usually a “headless system” - no mouse/keyboard after everything is running
	- good, high speed network card (Gigabit NIC)
	- RAID array - to protect data (+ lots of storage)
	- good midrange motherboard & CPU

— Gaming PC
	- multi-core processor + motherboard that supports it
	- high-end power supply
	- high-end cooling
	- high-end video/specialized GPU - (features like SLI allows x2 GPUs to 1 monitor)
	- high-definition sound card
	- storage: SSDs + disk drives to hold games

— Audio & Video Editing Workstation 
	- specialized audio and video card
	- large, fast hard drive
	- dual monitors
	- “If you want to make your life easier in these types of situations just get a Mac”

— Concentrate on RAM, storage, and graphics needs

______
17. Display Technologies:

— pixel (picture element) - emit RGB light values
— resolution - # of pixels across and down (e.g. 1920x1080)
— brightness - Nit (nt) = measure of light
	- panels generally run between 200-500 nits
— response time - panel resets itself to keep persistance of vision (“refresh rate”)
	- panels generally run between 1ms-4ms

— Liquid Crystal Display (LCD) - electricity used to allow light to pass through
	- backlight via:
		- cold cathode flourescent lamp (CCFL) - old tech
			** only CCFL screens need inverters to convert DC back to AC **
		- light-emitting diodes (LEDs) - current tech
	- panel types:
		- twisted nematic (TN) - inexpensive + speed
		- in-plane switching (IPS) - wide range of view
	- 1. panel, 2. backlight unit, 3. connectors (“millions”), 4. input from data, 5. power connection

— Organic LED (OLED) - each RGB is an individual bulb vs backlit
	- benefit: for thin/flexible monitors (e.g. smart phones, tablets)

— Digital Light Processing (DLP) - grid of tiny mirrors vs individual pixels w/ color wheel that spins out RGB colors
	- popular for projectors (rare for monitors)

graphics cards and connections:
— Graphics Processing Unit (GPU) = video card
— Integrated GPU = graphics built-in to motherboard
— frame buffering - using some type of RAM to electronically keep track of what’s in each pixel and then pushing it out to the monitor
— scans back and forth rapidly (hopefully a min of 60x/s) to reset monitor to new image - today, icons, etc. stored in memory (8GB RAM on GPU itself is not uncommon)

— VGA (Video Graphics Array) - “granddaddy of them all” connection types
	- 15-pins on 3 rows
	- color: blue (usually)
	- disadvantage: is analog - monitor must convert to digital before updating (wasted step)

— Digital Video Interface (DVI) - first digital connector
	- DVI-I = digital & analog signal transmission capabilities
	- DVI-D = digital only

	- single-link DVI - has space betweeen pins
	- dual-link DVI - no space between pins - used to run 2 (or 1 high res) monitor(s)

— HDMI (High-Definition Multimedia Interface) - transmit video & sound
	- Digital Rights Management (DRM) support
	- mini-HDMI

— DisplayPort - dedicated connector for video; popular, HDMI competitor
	- mini DisplayPort

— GPUs often have various ports for flexability / multiple monitors (one is usually default)
— riser card - allows additional graphics card(s) from main expansion bus

projectors:
— technology: DLP & LCD (bulbs last a long time)
— lumens - defines brightness (small/dark area = 1000-1200 lumens; bright area = 2500+ lumens)
— throw - further projection = larger screen size; closer projection = smaller
— geometric adjustments:
	- pincushion - concave/convex edges
	- keystone - slanted edges (trapezoid-esque) - projecting from down/up from high/low
	- skew - tilted keystone

______
18. Essentials of Networking:

— Local Area Network (LAN)
— Ethernet - wiring standard to physically connect computers on a LAN
	- defined that no more than 1024 physical computers on a single/daisy-chained switch(es)
	- in reality, 30-40 computers is the standard max size
	- different versions:
		- 10BaseT = 10 Mbps baseband twisted pair
		- 1000BaseT
		- 10Gb Base T = 10 gigabit per second
		** may be copper/fiberoptic


— Wireless Access Point (WAP)

— Media Access Control (MAC) address - unique 48-bit address, always manefested as 12 hexadecimal characters, that identifies individual network cards on a LAN (e.g. 00-14-22-01-23-45)
	- aka “Physical Address” - is “burned in at the factory”
	- OEM ID = first 6 characters - given to manufacturer by the issuing body of the internet

— ethernet frame - (in order) destination MAC, source MAC, data payload, FCS (frame check sequence - ensures data coming in correct order)
	- chunk of 1500 bytes max (standard)

hubs vs switches:
— hub - a “repeater” - every frame sent from computers on a LAN is copied to each system
	- unintended recipients will erase the frame after not matching with destination MAC
	- max throughput of 10 Mb/s (5 Mb/s each computer A&B communicating)
	- more comps = slower
— switch - a “smart repeater” - box collects MACs of all connected devices and creates a direct link between communicating systems
	- A&B and C&D can each have 10 Mb/s conversations (provides full bandwith for all nodes)

WANs and routers:
— Wide Area Network (WAN) - hundreds/thousands/millions of interconnected LANs
— router - magic box that can differentiate between different computers and LANs
	- a device that forewards and filters traffic based on IP addresses
	- tool used to interconnect LANs
	- AKA “default gateway”

— logical addressing - addressing system to connect multiple LANs
— IP Address - another identifier (like MACs) - given unique to each device on a network
	- used to communicate outside of the LAN



— Dynamic Host Configuration Protocol (DHCP) - special type of server (built into home routers) that automatically serves connected devices to identifier information (IP address, Subnet mask, etc.)
— static IP address - manually entered identifier information - via administrator, “not out of thin air”
— APIPA (automatic private IP addressing) - alternate if DHCP server is down
	- always gives 169.254.x.x addresses (!)
	- no internet access, but can still access shared stuff (printers, files, etc.)

cables and connectors:
— Ethernet
— DOCSIS (Data Over Cable Service Interface Specification) - cabling type used for cable modems
— Coaxial cable - axial connectors - center piece + insulator + outer cladding (also a signaling tool)
	- RG ratings:
	- RG-58 - old type, thin cable; used in networking (w/ BNC connector - not threaded, push in)
	- RG-59 & RG-6 - used often in video and networking
	- F-type connectors - familiar type used for cable TV
— Twisted pair - predominant type used today - twisted together allows individual cables to run further (helps propagate the signal)
	- unshielded twisted pair (UTP) - no metalic foil inside
	- shielded twisted pair (STP) - metal on connector and through cable = robust protection
		- works better than UTP around interference (e.g. motors, flourescent lights)
	- RJ-11 - connector type (4 contacts) used in telephone cable
	- RJ-45 - has 4 twisted pairs (8 contacts)
	- CAT ratings:
		- CAT 5 = 100 Mbps
		- CAT 5e = 1 Gbps
		- CAT 6 = 1 Gbps (up to 100m) & 10 Gbps (up to 55m)
		- CAT 6a = 10 Gbps (in 100m segments)
— fiber optic (fiber) cable - uses light vs electricity to transmit = (popular w/) 10+ Gigabit ethernet
	- kevlar padding inside jacket
	- cladding w/ hair-thin strand of fiberglass to propogate light signal
	- multimode - uses LED
	- singlemode - uses lasers (propogates over many kilometers distance)

— PVC (non-plenum) - cheap; most capable to burn
— plenum rating - fire resistant
— riser rating - intermediate - used when running cables between floors

crimping cables:
— crimps - connector end (must match to needed CAT rating)
	- tool = cable crimper & cutter
	- cut off ~1-inch of jacket and move away kevlar
	- untwist and flatten out pairs into “broom shape”
— TIA 568A vs TIA 568B - standards to define where to match cable colors into crimp
— “if it starts w/ a B” - 4 wires go in exact same place
	- pin 8 = brown
	- pin 7 = brown/white
	- pin 3 = blue
	- pin 5 = blue/white
— TIA 568A (“alphabetical”)
	- pin 1 = green/white
	- pin 2 = green
	- pin 3 = orange/white
	- pin 6 = orange
— T568B (swap orange and green)
	- pin 1 = orange/white
	- pin 2 = orange
	- pin 3 = green/white
	- pin 6 = green
** In order to stay within any CAT rating, the distance from the last twist to where you actually punch down into the crimp must be 1/2”
— use cable checker -  for continuity (from end to end) and wire mapping (correct colors)
— straight-through cable - wired properly and the same on both sides 
— crossover cable - wired 568A and 568B on either side of the same cable
	- useful for direct computer-computer connection (depending on network card ability)

structured cabling:
— organized in the walls vs strung across floors (a hazard to people and data)
— Main Distribution Frame (MDF) - room/closet that stores the equipment
	- equipment racks are 19” horizontally (standard)
	- “u” = standard for vertical distance
— horizontal run - runs from different wall outlets throughout a LAN to the back of a patch panel
	** patch cables have a boot (extra piece of rubber on the crimp)
	- patch cable from switch -> patch panel
	- patch cable from patch panel -> walls/ceiling -> wall outlet
	- cable from outlet -> individual computer (all = 1 horizontal run)
	- TIA rule: max length of a run = 90m
		(vs 100m ethernet runs; compensates for length of patch cables up to 10m)

— 110 punchdown tool - connects cables to the back of the patch panel
	- place according to diagram (T568A vs T568B)
— cable tester - tool used to determine if making a good connection
	- some come w/ a remote to allow 1 connection in patch panel and 1 connection at wall
— fox (tone generator) and hound (tone probe) - tool used to locate “homeless” cables
— time domain reflectometer (TDR) - tool that can determine how long a cable is via speed of light

— solid core - type of twisted pair put into walls - each (of 8) wire is a solid piece of copper
	- carries electricity well; inflexible
— stranded - type of twisted pair used for patch cables
	- not as good/fast; flexible (won’t break)

______
19. Local Area Networking:

origins of the internet:
— thousands of individual LANs existed (military bases, universities, etc.) with the idea to connect so that any LAN could communicate with any other LAN
	- multiple connections to each individual node so info could be rerouted if any went down
— TCP/IP adopted as protocol for ARPANET / the internet (originally via telephone poles)
— IP addressing (e.g. 192.168.5.10) was the numbering system used to identify nodes; given to you by the Internet Authorized Numbering Authority (IANA) allows you to ge information from any computer on the internet.
	- used to 1. identify your LAN, 2. give you a unique host ID
	- each of the 4 dot separated values (called an octet) can go from 0-255
	- built w/ idea that you’ll always be within 4 routers from the top of the internet
	- combined total addressing space = 4 billion addresses (nowhere near enough…)

— “TIER 1 of the internet”
	- e.g. Rice University = 12
		- University of Houston = 12.1
			- Parallel Processing Center = 12.1.44
			- College of Arts = 12.1.27
			- College of Engineering = 12.1.28
			(each a separate LAN)
				- individul system(s) = 12.1.28.1(-254)
— Class C = 210.11.12.x (first 3 numbers locked in, “x” open to anything)
	- 254 hosts
— Class B = 172.16.x.x
	- 65,534 hosts
— Class A = 6.x.x.x
	- millions of hosts

— 1.x.x.x = “experimental”; 255.x.x = noone can use either
— addresses can never end in .0 or .255 (x.x.x.0 identifies the entire LAN)

— Subnet mask - identifier that allows computer to see if making a local vs long-distance call
	- 255.255.255.0
	- each 255 octet is part of the network address (numbers must match for local)
	- by comparing destination w/ source (own) IP address, can send direct (via MAC addresses)
	- if found to be outside of LAN, computer sends traffic -> router (e.g. 10.11.12.44 -> 10.11.12.1)

special IP addresses:
— Class A addresses = from 1.0.0.0-126.0.0.0
— Class B addresses = from 128.x.0.0-191.x.0.0 (“x” are assigned)
— Class C addresses = from 192.x.x.0-223.x.x.0
— Class D address = 224.x.x.x
— Class E address = 240.x.x.x
— Class D-multicast - used e.g. in video presentations; users are given a temp 2nd IP address (224.x.x.x) only for the duration of the video
— Class E-Reserved - nobody ever touches

— private IP address - not connected to the big “Internet”, but like the TCP/IP protocol used within private networks (if a router that is part of “Internet” sees, will erase packets)
	- Class A = 10.x.x.x
	- Class B = 172.16.x.x-172.31.x.x (“x” can be anything desired)
	- Class C = 192.168.x.x (1st “x” assigned/given; 2nd “x” can be anything desired)
— loopback IP address - 127.0.0.1

NAT:
— NAT (Network Address Translation)
	- an IP address is provided by ISP (on WAN side) to the router
	- all devices inside network are given a private IP address
	- the router replaces the private IP address to/back with own IP address
	- allows that not everyone need their own unique IP address
	- benefit: security - devices on network no longer have public, easy to find IP addresses
	- downside: slower and anything inside network is invisible to the internet

IPv6:
— ran out of all 4 billion IPv4 addresses
— has a 128-bit addressing scheme, using hexadecimal notation (8 groups, 7 colons)
	- example: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
	- 340,282,366,920,938,463,374,607,431,768,211,456 total addresses!
	- “IPv6 has a prefix length fixed at /64”
— shorthand = remove all leading zeros & compress 3 zero’s in a row to 2 colons
	- 2001:0000:0000:0001:0000:0000:0000:8a2e —> 2001:0:0:1:0:0:0:8a2e
	- 2001:0:0:1:0:0:0:8a2e —> 2001:0:0:1::8a2e
— IPv4 requires an IP address & a Subnet Mask
— IPv6 requires a Link-local address & an Internet address:
	- link-local address - used for local connections
		- fe80:0000:0000:000: + [second 1/2 auto generated]
	- internet address (global unicast address) - used to connect to the Internet
		- router broadcasts the first 1/2
		- computer auto generates the second 1/2
— “As a security feature - a computer will have one main IPv6 address, and (depending on OS) can have multiple temporary IP addresses to communicate with different servers.”

ports:
— Port number - a number ranging from 0-65535 sent/recieved in a frame to point incoming/outgoing data/requests to the correct application.
	- well-known ports = 0-1023
		- applications like the web, etc.
	- registered ports = 1024-49151
		- applications that “came out after well-known ports that want their own ports”
		- e.g. Steam games
	- dynamic/ephemeral ports = 49152-65535
		- “the 2nd port number”
		- spun up by your system on every connection to give a return port number to the server

COMMON PORT NUMBERS: 
21-FTP
File Transfer Protocol (“ftp://“)
22-SSH
Secure Shell
23-TELNET

25-SMTP
Simple Main Transfer Protocol
53-DNS
Domain Name System
80-HTTP
Hypertext Transfer Protocol
110-POP3
Post Office Protocol
161/162-SNMP
Simple Network Management Protocol
143-IMAP
Internet Message Access Protocol
334-HTTPS
HTTP Secure
3389-RDP
Remote Desktop Protocol (Windows exclusive)
137-139-NETBIOS/NETBT
Network Basic Input/Output System (MS c-c)
445-SMB/CIFS
Server Message Block / Commin Internet File System (=Windows’ folder sharing)
427-SLP

548-AFD

67/68-DHCP

389-LDAP



995-POP3 (encrypted)

993-IMAP (encrypted)

465/587-SMTP (encrypted)

(**note: almost all of them are a well-known port)

— Transmission Control Protocol / Internet Protocol (TCP/IP) - 
	- TCP - connection oriented protocol - create a “handshake” with the server as a client first		- send multiple packets
	- UDP - connectionless protocol - no handshake; assume the server is always on the job
		- request data outright
	- ICMP - single packet only (e.g. ping)

— protocol data unit (PDU) - the individual, organized pieces of an ethernet frame
	- destination/source MACs, destination/source IPs, Ports, Data, PCS
— IP packet - part of the frame containing:  destination/source MACs & IPs + the Data
— TCP segment / UDP datagram - part of the frame containing: destination/source Ports + the Data

understanding DNS:
— Hosts file - primary way to resolve names in the 90s via a daily 3am host file update (still exists)
	- used to give the Internet your IP address and assign it a name
— Domain Name System (DNS) - retrives the actual IP address to send the data/webpage request to when entering a url into a browser.
	- a “speed dialer” or “contact list for the Internet”

— Root Servers - control one fully qualified domain name called a dot (“.”)
— First Level Domains - hundreds of thousands of servers in charge of (e.g. “.edu”)
— Second Level Domains - hundreds of thousands of servers that control  (e.g. “google dot com”)
— computer’s request to  “this url” -> DNS -> root server -> .com server -> “this url” server -> DNS -> computer that made the request
— cacheing - a copy of the IP address for “this url” is saved by the computer & DNS server (for a certain amount of time) - future requests by others on your DNS server move quicker

— fully qualified domain name (FQDN) - a registered, verified, (and paid for) unique name - once a DNS server is set up, can point “www”s towards.
	- FQDNs have a 256-character limit (including all “.”)

workgroup vs domain:
— NetBIOS/NetBT - convention to give computers on a LAN a human-readable name for sharing
	- NetBT = NetBIOS over TCP/IP
— a Workgroup - most basic networking organization type
	- no security; central administration
	- works fine for small networks (e.g. share printer, folder, etc.)
— a Domain - convention w/ substantial security - can disperse all kinds of security stuff to a bunch of computers at the same time
	- requires a Windows Server system (hardware(s) + software(s) = expensive)
— a Homegroup (dumped in Windows 10) - convention w/ security of domain + convenience of workgroups (e.g. automatically share Doc, Music, etc. folders when joining)

routers:
— SOHO routers are commonly a 2 port router + 4 port switch + WAP in one box
— routing table - tells the router where to send requests/data (IP address & port number)

— DOCSIS - connection to router via cable modem vs ethernet
— Console port - a serial port using the RS-232 language to act as a connection
	- must connect on a computer via a terminal program (e.g. putty) to talk to router on init config
	- yost/rollover cable = DB-9 connector (on comp side) + otherside looks like RJ-45

— Quality of Service (QoS) - toolset on routers that allows to meter bandwith on individual devices
	- can meter based on: IP addresses, MAC addresses, port numbers, etc.

— Universal Plug and Play (UPnP) - makes a device “noisy” (shows up in networking) 
— Link Layer Discovery Protocol - a protocol (on Windows) for advertising identity/capability over LANs
— Simple Network Management Protocol (SNMP) - tool that goes beyond simple discovery, used by network administrators to:
	- know there is a switch attached AND how much bandwith is moving through it
	- know there is a router AND have an idea of what it’s filtering right now

— managed switch - gets an IP address (normally only accessable via MAC) and can be communicated with for advanced set up through a browser interface (e.g. port security)
— Virtual Local Area Network (VLAN) - 1 physical switch electronically separated into multiple LANs

______
20. Wireless Networking:

— IEEE 802.11 = primary wireless standard
— \ (infrastructure mode) - common; uses WAPs (e.g. school, coffee shop, etc.) to connect using the device’s wireless network card
— Ad hoc mode - one computer’s NIC is treated by others as a WAP

— service set identifier (SSID)
** “Hide/disable SSID broadcast” - CompTIA obsessed w/ as a security protocol

antennas:
— omni-directional - single piece of metal sticking up
	- radiation pattern: “big fuzzy ball”
	- doesn’t work well in multi-floor office situations
	- more power to antenna = bigger “fuzzy ball”
— patch - flat, rectangular
	- radiation pattern: 1/2 “big fuzzy ball”
	- use: propogate signal in a direction (e.g. against a wall)
— highly directional
	- Yagi = antenna on old TVs
	- Parabolic = like a satellite dish
	- radiation pattern: long, stretched out “football pattern”
	- often have an opposite second antenna pointing back
	- use: popular for long throws

wifi standards:
— Industrial, scientific, and medical (ISM) radio bands - the unlicenced standards that 802.11 uses
	- band = range of frequencies
	- 2.4 GHz band = 2.412-2.4884
	- 5 GHz band = 5.150-5.875

802.11a
54Mbps
5GHz


802.11b
11Mbps
2.4GHz


802.11g
54Mbps
2.4GHz 
(backwards compatible to b, not a)

802.11n
100Mbps
2.4GHz / 5GHz
(backwards compatible to any)
Wi-Fi 4
802.11ac


(used today. Has multi-user MIMO)
Wi-Fi 5

— MIMO (multiple in / multiple out) - allows to use multiple antennae on a single WAP to narrow the signal to a single device

Wireless Mesh Network (WMN):
— 1 basestation is connected to the network itself + configure SSID & password
— plug external stations (beacon devices) wherever better coverage desired
— “like Ad hoc mode on steroids” - won’t have the throughput of a large, robust network w/ tons of WAPs, but easy to config and great for SOHO
— “use robust 3rd party encryption vs WPA2, etc.”

Near Field Communication (NFC):
— Radio Frequency Identification (RFID) - a reader uses radio frequency to power stickers and transmit data - popular in warehouses - doesn’t transmit very quickly
— Bluetooth - single device-device connection - “looks like 802.11 from a signal level” - 
	- Class 1: power = 100 mW; range = 100 m
	- Class 2: power = 2.5 mW; range = 10 m
	- Class 3: power = 1 mW; range = 1 m
	* devices have a class that makes sense for it
— Infrared (IR) - a line-of-sight, low speed connection (e.g. TV remote)

________
21. The Internet:

— Personal Area Network (PAN) - direct connection btwn two bluetooth capable devices
— Local Area Network (LAN) - group of computers all connected to a switch in such a way they can easily communicate, all sharing an identical network ID
— Wide Area Network (WAN) - a bunch of interconnected LANs via routers, each with a unique network ID
— Metropolitan Area Network (MAN) - large WAN; limited to a local municipal area (“across a town”)
— The Internet - connected MANs across the world - is the largest (/all inclusive) WAN

(network) tiers of the internet:
— Tier 1 - a large network that can reach every other network on the Internet via settlement-free interconnection (peering agreements).
	- btwn 10 companies that cover the entire US - must work together
— Tier 2 - smaller entities; decent coverage area, but not entire US
	- pay for certain connections to Tier 1 (no peering agreements)
— Tier 3 - the big ISPs (e.g. Comcast, AT&T, Cox, …) that sell the internet to us
	- they pay Tier 1 & 2 for their internet connections (no peering agreements)

— Network Operation Centers (NOCs) - physical (3rd party) connection point between networks - outside companies set up routers here and all connected


dial-up connections:
— “Dial up” = POTS (Plain Old Telephone Service) or PSTN (Public Switched Telephone Network) - taking a system designed to transmit analog voice and getting it to send digital data.
	- modems convert POTS (analog) to “COM port” (digital)
	- speed = 56 kbps max
	- phone/computer direct connect to modem via RJ-11
	- available on even latest versions of every OS

— ISDN (Integrated Services Device) - transition technology from dial up to broadband via “terminal adaptors” - is a completely digital line that allowed to keep telephone line 
	- voiceover actors established and still use an ISDN network

broadband connections:
— Broadband Connection is typical way we connect - always on connection vs dial-up call ins

— Digital Subscriber Line (DSL) - piggybacked telephone lines and added a digital signal
— Asymmetric DSL (ADSL) - upload speed slower than download speed
	- upload = 768 Kbps - 3 Mbps
	- download = 1.5 - 7+ Mbps
— Symmetric DSL (SDSL) - equal upload & download speed (rare today)
— Point-to-Point Protocol Over Ethernet (PPPoE) - DSL that allows multiple computers on a single connection where previously companies could charge for each (multiple phone lines for dial-up)
		- PPPoE allowed to get around this multiple user/password

— “Cable” = Data Over Cable Service Interface Specification (DOCSIS) 
	- similar to ethernet, but allowed internet use + cable TV watching
	- old speed = 1.5/10Mbps
	- today’s speed = 50/100Mbps or better (upload/download)
	- “MAC Clone” - setting that allows you to buy your own cable modem vs renting from cable company - today, cable companies allow you to just call and register your device

— Satellite - good for people not near cable or DSL opportunities (e.g. rural areas, open ocean)
	- speeds = 3Mbps/25 or better
	- latency issues = stalls / slow speeds
	- uses a modem like anything else

— 802.11 - given a Yagi/parabolic antenna has much greater range than normal 802.11


firewalls and servers:
— firewalls - one of primary functions is to block ports on an incoming/outgoing basis
— all servers have firewalls - host based firewalls (computers and routers) allow outgoing connections on Port 80, but block incoming (router swaps in/out port num) - public facing servers (e.g. web servers) must allow incoming Port 80 connections, but will use a stateful firewall (e.g. block people from pinging) 


FTP:
— file transfer protocol (FTP) - a way to transfer files before the web was popular (“cloud storage before cloud storage was cool.”)
	- passive mode = everything done over Port 21
	- active mode = outgoing on Port 21; incoming (from server) on Port 20
	- requires an FTP client - every web browser (“ftp://“) and robust options (e.g. FileZilla)
— port triggering - allowing/pushing incoming traffic from a different port based on the outgoing port number (a setting on routers)


email:
— Simple Main Transfer Protocol (SMTP) = send mail to SMTP server

— Post Office Protocol (POP / POP3) = bring emails down from server to client
	- simplistic; have to set up folders on client itself
— Internet Message Access Protocol (IMAP / IMAP4) = bring emails down from server to client
	- stores folders/organization wherever your client is

— If required to set up manually - will need/have someone giving you this information
** know the port numbers for the exam, BUT - in reality (today) all email is secure and uses different ports…


proxy servers:
— proxy server - an additional computer (between it and the router) that web traffic is rerouted through - used to block specific connections (vs firewall on router) - bad URLs, check for malware, filter information (e.g. watch for SSNs)
	- popular in schools
	- are application specific - e.g. web broswers require a settings change
	- can be set up do caching for webpages that clients visit often
	- on webpages that update often - will cache static and only grab updating stuff
	- on router - unless coming from a proxy server all outgoing Port 80 should be blocked

VPNs:
— virtual private networking (VPN) -  taking the Internet (most public of all networks) and turning it into a “fake” private network - allows remote access to printers, folders, file servers, etc.
	- VPN tunnel - the name for the connection
	- VPN client - software that takes the given (remote) IP address of the router and connects
	- the connection manefests as a new network card on the system	
	- given an IP address (by DHCP) as if on the remote network
	- PPTP; L2TP; IPsec = different VPN connection protocols (require 3rd party software)

— split tunneling - a problem where webpage connections are routed through the remote network when connected via VPN (-> home network -> web server -> home network -> your system) 
	- fixed by more advanced 3rd party VPN clients


IoT:
— internet of things (IoT) - 	giving internet connectivity to devices (not traditionally associated with the internet) for the purposes of remote control
	- e.g. home automation - thermostats, light bulbs, fridge, door locks,
	- require a “hub”
	- smart phone apps often for set-up/settings

— 802.11 - common communication method
— Zigbee - method exclusive to IoT (commonly home automation) that runs on the 2.4 GHz band as they doesn’t need a lot of bandwith (e.g. turn on/off dryer)
— Z-Wave - runs on 900MHz band

________
22: Virtualization

— virtual machine (VM) - a guest OS running within a host OS - a completely self contained computer
— “virtualization” - actual (real) hardware allocated to a seperate (virtual) system
— “emulation” - using hardware you don’t actually have (pretend) to run the OS (e.g. N64)

— hypervisor - name for the softwate that runs the virtual machines
	- type 1 = installed like an OS (nothing between it and the VM)
	- type 2 = installed like an application on an existing OS (Linux/Mac/Windows) 
		- less efficient than 1
		- VMs don’t see the host OS

cloud computing
— “the cloud” - virtual machines (in a server farm) with remote access - technically anytime you don’t know where the computer is but you can access via it’s IP address

— rapid elasticity - take copy of VM to different markets (e.g. want better access in Japan)
— on-demand - clone VMs based on demand (e.g. NFL spins up tons of VMs for superbowl traffic)
— resource pooling - billions of VMs w/ shared resources for effeciency (e.g. storage, electrical needs, HVAC, etc.)

— Infrastructure as a Service (IaaS) - rather than buying your own hardware (e.g. AWS), move network tasks into the Cloud (e.g. firewalls)
— Platform as a Service (Paas) - IaaS used just run code (e.g. Heroku) - moves the machines into the Cloud so that you can concentrate on the app
— Software as a Service (SaaS) - moving apps to the Cloud (e.g. Google Docs)	

— Private Cloud - owned/self-hosted VMs generated within an organization
— Public Cloud - open for business uses (e.g. Amazon S3, Microsoft Azure)
— Hybrid Cloud - a large cloud that is segerated into private/public
— Community Cloud - shared by multiple organizations (pooling to reduce high set up costs)

________
23: Portable Computing

— desktops and laptops run the exact same OS (often) and troubleshooting issues are (often) the same

— physical laptop lock and cable lock -> locking port

— “docking station” - snap into a proprietary connector for added ports/periphrials (e.g. monitor)
— “port replicator” - a big USB hub

laptop hardware:
— battery
— hard drive = 2.5-inch
— memory = SODIMM RAM
— mini PCIe (express) slot(s)
— wireless card, bluetooth module
— Wi-Fi antenna + wiring - typically built into the display bezel
— real-time clock battery
— optical drive

— monitor/screen - tend to be sealed systems = in general, replace entire monitor
— keyboard - special function keys (Fn + key) - e.g. dual displays, touchpad (on/off), economy mode, camera (on/off), airplane mode, bluetooth (on/off), wireless (on/off), volume, screen brightness, keyboard backlight, …
—touchpad
— smart card reader
— fan
— DC jack

— motherboard
— CPU - soldered on most modern laptops = can’t replace

________
24. Understanding Mobile Devices:

— 1. a single, sealed unit
— 2. running a specific mobile OS
— 3. wireless connectivity - all have 802.11 (at a minimum) + bluetooth, cellular, Zigby, etc.

— “embedded system” = the OS is intrinsic to the device - stored on firmware
— often not designed to support different drivers

smart phones & tablets:
— Android or iOS
— GPS, acceletometers, etc.
— battery chargers, battery packs, screen protectors, cases/bumpers, etc.

wearable technology:
— e.g. FitBit, Wahoo - accelerometer, HR monitor, etc
— often sync w/ smart phones

e-readers:
— no backlight, color, etc. - minimal power needs

global positioning system (GPS) devices:
— OS is typically some cut down version of Linux

credit card readers:
— swipe/chip

micro/mini SD cards


— wired connections - mini/micro-USB, Apple Lightning, USB-C, Thunderbolt
— wireless connections - NFC (tap-to-print/pay), bluetooth, infrared, 802.11, cellular
	- “tethering” - requires a physical connection
	- “hotspot” - device passes out an SSID

— Airplane mode - turns off “anything that produces radio waves” (802.11, bluetooth, NFC, )


virtual reality (VR):
— complete virtualized environment
— real-world applications (military, medical, engineering) & gaming
— 2 OLED monitors make 3D effect
— infrared transmitters detect/track movement

augmented reality (AR):
— virtual objects are placed in the real world (e.g. on-the-fly text translations)

________
28. Care and Feeding of Mobile Devices:

— (code division multiple access) CDMA phones - don’t come with SIM card - drivers, OS, etc stored on ROM (firmware)
	- require updates: baseband (cellular), broadband, radio firmware, perferred roaming list (PRL)
	- “PRI” = product release information
— (global system for mobile communications) GSM phones - come with SIM card - all updates sent to you (automatic/manual) 

— International Mobile Subscriber Identity (IMSI) - built into SIM - defines subscriber info
— International Mobile Equipment Identity (IMEI) - defines phone itself
— “activating” a phone is just  connecting IMSI and IMEI


— “synchronization” - updating two or more data stores so information is identical (** predates the Cloud)
	- synchronize to the desktop - with cable to computer (e.g. iTunes)
	- synchronize to an automobile - via bluetooth (on Android or iOS)
	- synchronize to the Cloud - dominant form (e.g. Google Drive or iCloud “remote backups”)
— e.g. bookmarks, contacts, location data, e-books, health data, applications, social media data, …

— antivirus/anti-malware - on both iOS and Android (iOS less necessary)
	- general concensus is iOS doesn’t need because of tight app lockdown
	- on Android, download from Google Play Store (Trusted source)
	- can download apps outside of store on Android (Untrusted source)

— firewalls - Android has 3rd party firewalls; iOS less necessary
— if downloading via store on Android, less likely to need (“trusted” vs “untrusted” source)
— apps may have software requirements


mobile devices and e-mail:
— corporate e-mail configuration - manually set up with: FQDN of SMTP server, username & password, SMTP & IMAP port numbers, 
— commercial e-mail providers (e.g. Google, Yahoo, etc.) - only need email/username & password

— point-to-point encryption (P2PE) from phone to mail server is encrypted
— SSL, STARTTLS
— S/MIME (Secure/Multi-purpose Internet Mail Extensions) - method to encrypt attachments - mostly made obsolete by full e-mail encryption
	- MIME - turns a binary file into ASCII code (text) - reconverted on reciept

________
26. Printers and Multifunction Devices:

laser printers:
— photosensitive drum - holds a static electrical charge - more light at a particular spot causes less light to be able to be held 

— 1. Processing - print jobs are stored in local memory on the laser printer 
— 2. Charging - primary corona - puts a uniform negative charge (-440—600v charge)
— 3. Exposing - laser writes image onto photosensitive drum, reducing charge (-150v)
— 4. Developing - toner is @ -300v charge - negatives avoid negatives - is repulsed from area not exposed to laser - is less charge than -150v so toner sticks to these areas
— 5. Transfer - pick up rollers: draw in paper; separation pads: keep only 1 piece going in at a time; transfer corona: puts +150v on paper - as paper rotates, goes past photosensitive drum, and toner slams into it
— 6. Fusing - user assembly - heat and pressure to melt and fuse toner to paper
— 7. Cleaning - rubber scraper removes residual toner from roller
— All happening at the same time in a continuous process until print job is done

— color printers have CMYK (cyan, magenta, yellow, and black) toner cartridges.
— 4 different rollers add color toner to the transfer belt before

maintenance:
- replace toner - new photosentive drum & toner
- cleaning - read documentation - sometimes an antistatic vacuum
- maintenance kits - new pick up rollers, transfer roller, etc
- “maintenance mode” - print vital statistics
- calibration - fixes toner placement


inkjet printers:
— ink cartridges connected to jet heated up, boiled, shot
— metal deflectors point ink in different directions
— print head - stores jets and moves back and forth on carriage allows to put ink across all paper
— feeding mechanisms to bring in/out paper

— cost less to run
— less heat & voltages = safer
— ink cartridges (MCYK) are individually replacable

— multifunction devices (MFDs) = printers, scanner, copiers, fax

maintenance: 
- “maintenance mode”
- maintenance area - plugs ink jet when not in use (off to side)
- 1. Clean heads
- 2. Calibration
- 3. Replace cartridges
- 4. Clear jams


impact printers:
— ink ribbon
— print head - has tiny pins that push through ink ribbon and onto paper
— platin - push paper against ink ribbon

— “tractor feed” paper - holes on either side & perforated
— impact paper - multiple copies that can be punched through
— used in industrial / shipping for multipart forms

maintenance:
- replacing the ribbon (they wear out)
- keeping it clean
- platins run out of adjustment, use screws to realign


thermal printers:
— thermally sensitive paper - changes colors w/ heat
— feed assembly
— heating element
— special thermal paper - multipart forms - white+yellow sheet
	- left in hot room will cause to change color (not a long term solution)

— reciepts from point-of-sales systems

maintenance:
- replace paper
- clean heating element - wipe dander w/ cloth
- remove debris - accumulates paper dander - use air gun



installing a local printer:
 — connecting to a workstation via: USB (majority) or serial (point-of-sales systems)
— OSes generally have drivers - otherwise use manufacturers site
— firmware updates
— download utility software to see issues

— “spooler” - software that holds the print jobs - prints queue in supplied orders
— collate - prints to multiple trays (123,123,123 vs 111,222,333)
— duplex - prints to both sides of paper (odd -> even)
** exam tip: can’t stop the printer? spooler requires admin permissions

— wired device - requires to have a network card in printer (RJ-45)
— wireless device - requires wireless NIC in printer
— are DHCP clients (will grab IP autimatically)

protocol to get IP from DHCP and broadcast existance:
- mac: SLP
- windows: LLDP

- windows: Zeroconf (zero configuration)
- mac: Bonjour (wireless = Airprint)

— Cloud printing (e.g. Google Cloud Print) - set up printer via company and then can print from any network (must be wireless capable)/

virtual printers: 
- Print to PDF
- Print to XPS
- Print to image


3D printing:
— filament = unmelted raw material - melt and harden quickly (thermal plastic)
— heating element and table that moves around - heated thermal plastic -> shape
— the printing process requires preheating the various print elements, such as the filament, extruder, and bed

— take image into tool to prepare for printing (Blender, etc)
— 3D image is sliced to produce the layers that are printed
— select slice file on printer

________
27. Securing Computers:

dealing with threats:
— if you want to avoid threats you need to keep your shells from being vulnerable - protect host and network (+ physical security)

— Patch your system! - all OSes generally automatically patch
	- applications need patching, servers applications need updating as well
— Run anti-malware
— Run a host-based firewall


— intrusion detection systems (IDS) - a box or software in network that monitors and gives notification (not often used)
	- downside: must physically go to firewall after
— intrusion prevention systems (IPS) - “agents” = software installed on individual machines or centrally - talks to firewall to turn off individual ports, urls, or whatever necessary
— tend to be expensive and need central administration
— Endpoint Management - central system that watches for these intrusions, keeps everything up to date, software patching, etc. (great in enterprise environments)

— Unified Threat Management (UTM) - included IDS/IPS, firewalls, anti-malware; available on the Cloud



START-1002


1. Safety and Professionalism:

- professional communication:
	— Be on time - if going to be late, contact the customer
	— Actively listening - allow to describe problem in great detail; take notes if necessary
	— Clarify customer statements - ask open ended questions to narrow scope of problems
	— Maintain positive attitude / project confidence
	— Use proper language and avoid jargon, acronyms, and slang
	— Set and meet expectations/timeline and communicate status with customer
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


- physical safety:
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

— Radio Frequency Interference (RFI) can interfere with wireless signals.
— “Which is not a good way to prevent or reduce ESD?“ Antistatic Toolkit - no such thing

________________________________________________________________
2. The Visible Computer:

— operating system (OS) = “a program to run all of the programs”
— OSes know how to talk to a specific type of CPU (64-bit/32-bit) - have specific wiring on bottom designated to talk to memory

— kernel - core part of OS that handles primary memory management
	- Resource Monitor (on Windows)
	- Process ID - every program gets unique


— device drivers - software used by the OS to control computer components (hardware)
	- Device Manager (on Windows)

— storage - a heirarchial organization of data (folders & files)
	- File Explorer (on Windows)

users:
— user account - Database of names/passwords
— Super user or administrator account - account that allows higher levels of control

— every computer in existance has a user system + some type of super user account(s):
	- Windows = Administrator
	- Linux/macOS = Root


Microsoft Windows:
— Per Processor Agreement - Bill Gates gave copy of Windows to every Intel processor purchase

— Networking - accessing resources from a different computer on your network requires your user/password on the other computer to access
— Domain (Active Directory) - Windows Server - an OS that sets up a:
— Domain Controller - allows Single sign-on (SSO) - login to any computer (concept owned by Windows) - is important in enterprise environments
	- SSO features on other OSes:
	- macOS = File Sharing and Print Sharing
	- Linux = Samba

— UAC (User Account Control) - prevents usage of powerful programs by users with limited permissions

Windows editions:
—  Home edition - homes and small offices
	- can’t join a windows domain
	- often come with media tools, etc
— Pro versions
	- basic tools to do whatever need to do
	- always have ability to join Domain
	- ability to take advantage of CPU power
— Enterprise edition 
	- can’t buy from local stores
	- volume discounting
	- features to take control of tens to thousands of computers

Windows versions:
— Windows 7
	- Media Center - don’t confuse with Media Player (last version to have this)
	- Control Panel - single source to change things
	- start button and task bar
— Windows 8
	- unveiled to be used on more devices (smart phones, tablets)
	- has task bar, no start button
	- Microsoft Store
	- Charms bar - introduced new Settings function (splits with Control Panel)
	- OneDrive - Cloud storage
— Windows 8.1
	- adds back start button
	- still no one was a huge fan of Windows 8
— Windows 10
	- Charms bar is gone
	- Start menu - tiles are now here
	- Settings button - more complicated settings, Control Panel almost unnecessary


macOS:
— Apple menu - far left on top bar - changes based on application open
— Status menu - far right on top bar
— Dock - programs you use the most
— Finder - folder contents on system
— System Preferences - equivelent to Settings/Control Panel
— Terminal - Unix commands
— Command-q used to fully quit application

Linux:
— Linux =  the kernel of the OS

— Distro = packaged Linux distributions (e.g. Raspian for RaspberryPi)
— Ubuntu - most commonly used distro
	- Dash - equivalent to Windows Task Bar
	- can open multiple desktops
	- Terminal - everything critical done through command prompt
	- not a lot of penetration from the desktop
— Fedora Linux distro - runs the KDE desktop environment (where GNOME is the only real desktop alternative)
— Linux Mint Distro - runs the Cinnamon environment - gives look and feel of Windows

— GNU licence - freeware - allows people to write linux kernel(s) to connect to a hard drive or desktop environment
— Linux is often found in routers, raspberry PIs, Android Phones

________________________________________________________________
3. CPUs:

32-bit vs. 64-bit processing:

— CPU must grab lines of code from RAM
— motherboard’s job is to connect external data bus to everything (via thousands of wires/contacts)
— 8-bit allows 8 lines of binary code

— MCC (memory contoller chip) - additional chip or built into CPU these days
— Address bus - direct connection between MCC and CPU to allow CPU to ask for specific line of code from memory needed - not used to move data
	- 16-bit = 00000000000000000-1111111111111111; 2^16 = 65,536 bytes of RAM accessible
	- 32-bit = 2^32 = 4,294,967,296 bytes = ~4GB RAM
	- 64-bit = 2^64 = 1.844x10^19 bytes
	- 32-bit processors (and applications) won’t see / can’t use more than 4GB RAM
	- 64 bit gives more memory

— make sure to use correct version of OS:
	- x86 denotes 32-bit CPU
	- x64 denotes 64-bit CPU
— software comes in 32/64-bit versions - can install 32-bit versions of software on 64-bit Windows

— 32-bit is alive and well, but more specialized 

________________________________________________________________
4. RAM:

virtual memory:
— allows OS to use part of hard drive as memory; always better to have the RAM you need (vs getting an “out of memory error”) - should only be used when physical memory is exhausted as causes computer to slow down
— paging file - the part of the hard drive that the OS thinks is RAM (**exam tip: automatically manage paging file size for all drives)
— (on Windows) a file “swapfile.sys” is created
— (on Linux) a swap partition is created 

— 2GB for OS (Windows)

________________________________________________________________
7. Power Supply:


— power over time from power company is a (120V) sine wave @ 60 cycles/sec = 60Hz (US standard)

power protection:
— sag - short term voltage dip - will often get <120V (e.g. transformer down)
— brownout - an intentional or unintentional drop in voltage - can keep the computer from running or cause reboots (synonym to sag)

— spikes = more voltage provided than expected - can get 300V suddenly - may destroy your computer (synonym = surge)

— surge suppressor/protector - device catches surge and eats higher power before getting to device
	- “trip alert” - shuts off power
	- downside (to cheap ones): will be a good surge supressor once - then becomes a power strip
	- don’t worry about UL ratings
	- variations exist for: ethernet cabling, landline, and USB
	- use with: anything cheap (e.g. flatbed scanners, printers, etc.)

— UPS (uninterruptible power supply) - device that protects from spikes/surges AND sags/brownouts via a UPS battery that picks up where the power company isn’t providing.
	- will often have seperate UPS & simple surge protector sides
	- APS website will show total time a system can be powered down (& tools exist to show available power)
	- use with: any other system

— power supplies have built-in surge suppresssors, but don’t protect from sags or brownouts

________________________________________________________________
9. Implementing Mass Storage:

partioning:
— turning a physical hard drive into a logical electronic device readable by an operating system with given “rooms” (partitions) available.

— OSes themselves make partitions via a tool/utility - after creation they must be mounted - they manefest as:
	- (on Windows) drive letters with a colon (e.g. C:, D:, E:, …)
	- (on macOS/Linux) a directory tree, aka folders (e.g. /, /cdrom, …)
— recovery partition - holds OS back ups


— master boot record (MBR) - defines partitions and shows computer where to find OS (oldest type of partition still used today).
	- LBA 0 - specific sector of a hard disk read first in boot order (assuming drive is first)
	- boot loader - the first code read off of mass storage
		- points to the beginning of a particular partition from the partition table(s)
	- 2TB max per partition
	- 4 partitions max per drive (aka primary partitions)
	- extended partitions - allows (logical drives) letters beyond (on Windows: different colors)

— GUID partition table (GPT) - designed to take advantage of the power of UEFI BIOSes to provide a broad cross section of advanced features
— (GUID) Global Unique Idenfitier - 128-bit value that defines your unique partitioning table
	- 128 partitions per/drive max - term “volumes” - term now vs primary/extended partitions
	- 18.8 million terabytes/partition max

— “Protective MBR” - piece of info part of MBR that says “I’m a GPT!” - as warning that cannot read LBA partitions so doesn’t instantly erase it - used when plugged into older systems so a GPT capable system will ignore the first part and go to partitions themselves
	-> LBA 1 - Primary GPT Header
	-> LBA 2 - Secondary GPT Header - back up of primary



— File Allocation Table - keeps track of things LBA by LBA basis where things are on a partition (FAT16, FAT32)
— part of format process queries each LBA block to see if can read/write data and replaces value on bad block with hexadecimal value to denote to not use
— large files fill up multiple blocks and reference down the table to others that reference different pieces of same file. Last block ends in “FFFF” to denote end of file.

— “fragmentation”
	- occurs when file is deleted 
	- file allocation stays the same
	- in directory where file was saved, first letter of file name changed to a lower case sigma
	- denotes blocks available to be written over
	- writing a new file, overwrites
	- if larger than the old file, allocation jumps from writing to these to new blocks
	- in order to get to file, will need to go all over hard drive to get it
	- especially a problem with HDDs


popular file systems:
— FAT32 - old
	- supports up to 8TiB volumes
	- each file can be up to 4TiB
	- best on small drives

— NTFS - “new technology file system”
	- Massive volumes up to 16 EiB
 	- Individual files up to 256 TiB
	- MFT (Master File Table) vs FAT -sits in middle of volume - impossible to erase
	- u.c. Compression
	- u.c. Encryption
	- Security - has the de facto standard for individual and network system security on all OSes

— ExFAT - between FAT32 and NTFS - better for smaller drives
	- supports the same NTFS sizes
	- less overhead, BUT not really compressable/encryptable

— CDFS (Compact Disc File System)
	- works on CDs, Blu-rays, DVDs etc.
	- u.c. Optical
	- individual files up to 4 GiB

Linux has vast file systems available.
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

dynamic disks
— unique to Windows - allows features like shrink or expand - happens automatically if selecting to use advanced features
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

— 1. Keep the boot drive basic (not dynamic)
— 2. Set boot drive to GPT - gives more features/flexability
— 3. Easy to create dynamic drives - but if you switch back to basic you lose data 


software RAID:
— Windows allows easy RAID 0 (striped volume) and RAID 1 (mirrored volume) through software in Disk Management (“Storage Spaces”) - sees end result of array as a single drive
	- downside: can slow down system vs hardware RAID


encrypting mass storage:
— file-based encryption - software feature of OS to encrypt particular file or folder
	- Encrypting File System (EFS) - on Windows, built-in to NTFS
		- right click on file/folder -> Properties -> Advanced -> “Encrypt contents to secure data”
		- anytime you log in will decrypt for you
		- even law inforcement (as far as known) can’t crack
	- No built-in tool in macOS; tons of options for Linux

— disk-based encryption - software feature of OS to encrypt entire drives
	- BitLocker - used in Windows
	- FileVault - macOS
	- Linux has tons available

— Trusted Platform Module (TPM) - manefests as a chip on motherboard - robust key built-in

________________________________________________________________
11. Building a PC:

boot from everything:

— ISO images - perfect copy of OS that was originally optical media
	- burning = the process of getting an ISO onto a device (USB thumbdrive, optical media, SD)
— make sure to change boot order


— 


pre/post-installation:
- check minimum hardware requirements for OS
- 8 GB RAM (reccomended)
- 250 GB hard drive (reccomended)
- Hardware compatability list - research online
- Enterprise - hardware manufacturers will work with you to verify

— Know your network
— Know your domain name
— Know the local account names
— Know your Microsoft account

— recovery disk - personal copy of Windows installation media (flash drive - 16GB minimum) - preserves applications, drivers, the registry, and other critical system files (not user files)
— restore point - snapshot of system as it currently is
— file history - allows you to keep back up copies of any changes on a file-by-file basis


installation options (Windows):
— Clean install - blank storage, put in installation media, and install
— Upgrade install - keeps applications, sign-on, desktop setup
	- version specific only (on Windows) - home -> home, pro -> pro

— multiboot - support multiple OSes on a single drive - need extra hard drive or unpartitioned space on primary drive - given a choice at boot


— unattended installation - used when setting up a ton of computers at once, but allowing some flexibility to users on certain things depending on needs (e.g. choosing user/password)
	- answer file - generated to answer installation questions; only pops up whats necessary
	- Windows System image Manager - free tool to generate answer file
		- creates “autounattend.xml”
		- drag and drop into installation media (root)

— image deployment - distribute a single system image to multiple identical systems (e.g. applications, Domain, firewall settings, etc.) over a network
	- Windows - User State Migration Tool (USMT) - Windows’ tool
	- 3rd party tools - (e.g. Ghost)

________________________________________________________________
12. Windows Under the Hood:

— the Registry - stores Windows settings (internet address, users & passwords, desktop, software installed, etc.) - cannot boot without it - files stored in C:\\Windows\System32\config
— Registry Editor (regedit.exe) - application to manipulate binary Registry files (Linux stores this in billions of text files)
	- 5 root keys = 
	- HKEY_CLASSES_ROOT - what everything in computer defined to be able to do
		- application used to open file extension types & info on what type of info
		- manually change icons here
		- is the area least often entered (complicated)
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


processes:
— Applications - windowed stuff, running in the lower right corner; can see and deal with
— Services - stuff running in the background (program to manage on Windows =  “Services”)
— Apps + services = processes (all take up memory)

— dependancy heirarchy
— PID = Process ID

— “background processes” are services

Windows toolset:
— Right-click on an object to view its context menu
— Control Panel (**exams uses Large icons view)
	-> Administrative Tools 
		-> System Configuration - boot up configuration stuff
			- can uncheck certain services and applications from starting up
— Settings - a lot of overlap with Control Panel (often pushes to)

— Tons of ways to get to the same things.
— Can always just use search bar, type in name of tool you’re looking for, and pops right up.

**exam tip: not going to test you on which buttons to click to get to where (some hotkeys)

Windows 7 Task Manager:
= “the thermometer / blood pressure meter of your system”
— hotkey = “Ctrl + alt + del” or “Ctrl + Shift + Esc”
— 6 tabs:
	- Applications
	- Processes
	- Services
	- Performance - overview of how system is running (memory)
		- Resource Monitor - tool for more granular view (only place to get PIDs on WIN7)
		- “hard fault” - program uses hard drive as memory when RAM out of pages
	- Networking - rough idea of how hard network is using
	- Users - who is currently logged in

Windows 10 Task Manager:
— added right-click on Windows key -> “Task Manager”
— 7 tabs: Processes, Performance, App History, Startup, Users, Details, and Services

— shows percentage of CPU usage overall and by process - right-click on individual service for properties, file location, etc.
— Performance - shows typical Resource Monitor stuff
— Resource Monitor - still more granular stuff (e.g. what individual cores are doing)


information and configuration tools:
— System Information (msinfo32) - old - use to get a quick snapshot (“System Summary”)
	- shows BIOS version, processor info, RAM amount, etc.

— System Configuration (msconfig) - 
	- General - startup selection
		- Selective startup - useful when diagnosing issue from background service vs item
	- Boot - Safe boot - turns off complex device drivers, virtual memory, high-end video, etc
		- Network - same as Minimal (above), but allows network card for internet access
		- Active Directory repair - reestablish connection to server (**exam)
	- Tools - directs you to other stuff

— (Control Panel ->) System - important place for info and configuration
	- see Windows version
	- change name, input product key
	-> System protection - create/edit restore points
	-> Advanced System settings = same window as System protection, gives differen tab
		- virtual memory settings
		- Data Execution Prevention (DEP)
			- programs require memory allocations (called pages)
			- unless specifically need to, don’t let programs stomp on others
			- stops exploit that might crash system
			- by default, leave DEP as is and don’t mess with

— Microsoft Management Console (MMC) - allows creation of custom tools/utilities
	- “Add or Remove Snap-ins”
	- e.g. make a utility to open Disk Management & Device Manager at the same time
	- file, save as, “ “.mcc


— Performance Monitor - tool to get a “performance baseline” - gives an idea of how well computer runs before installing stuff (e.g. Steam games) that slows a system down
	- realtime mode - see how it’s doing at the moment
	- Counter - show/record info (e.g. %Processor Time, %User Time, LogicalDisk)
		** exam won’t ask you what counters show what
	- Data Collector Sets - user defined set of counters to create data logs (at chosen intervals)
		- cyclic logs - write over old stuff at a certain size
		- “Reports” - shows results
		- preset data collector sets via System Diagnostics & System Performance

— Event Viewer - shows default events that Windows logs:
	- 1. Applications - anything happening within an application itself that may be of interest
	- 2. Security - log on/off
	- 3. Setup - initial set up of Windows and updates that take place
	- 4. System - Windows core system itself - often where you go when things “blow up”
	- Event Log Online Help - to give you information about errors (cut+paste -> search = better)

— Local Security Policy - MS software to set up and adjust an audit policy (custom event logging for the system) - using a domain policy - administrator of domain can overwrite local security policies applied to groups
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


tools for programmers:
—  Structured Query Language (SQL) - type of computer communication allowing apps to talk to databases

— Open Database Connectivity (ODBC) - allows application to link to the database via a standard linkage format
	- e.g. local & remote sales computers accessing database of Inventory, Pricing, etc.
	- ODBC Data Source Administrator = tool comes standard on Windows

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
	- “programmer on the phone” - some comfort w/ interface

________________________________________________________________
13: Users, Groups, and Permissions

NTFS permissions:
— allow granular control of shared drives, folders, documents (right-click on items -> “Properties” -> “Security”)
— don’t care if you’re logging into the system locally or on a network (but requires second step of network sharing)
— right-click on item (files, folder, etc.) -> “Properties” -> “Security”

— Full Control:
- on folders - Enables you to do anything you want. (e.g. change name, read, write, delete)
- on files - Enables you to do anything you want to the file.
— Modify:
- on folders - Enables you to read, write, and delete both files and subfolders.
- on files - Enables you to read, write, and delete the file.
— Read and Execute:
- on folders - Enables you to see the contents of the folder and any subfolders as well as run any executable programs or associations in that folder.
- on files - Enables you to open and run the file.
— List folder contents: Enables you to see the contents of the folder and any subfolders
— Read: Enables you to view a folder’s contents and open any file in the folder.
— Write :
	- on folders - Enables you to write to files and create new files and folders.
	- on files - Enables you to open and write to the file.

— best to apply permissions to a group (container) vs individual user accounts (of which one can belong to many groups
— inheritance - a file/subfolder -> folder will take on same default NTFS permissions


Users and Groups on Windows (3 places):
— Settings -> Accounts -> Other people 
		- create a new account
		- change account type

— Control Panel -> User Accounts
	- provides more account control
	- change (your) account name/type (admin vs standard), add new users

— Local Users and Groups
	- Control Panel -> Administrative Tools -> Computer Management
	- provides the most control over users and groups
	- one of oldest applications in Windows
	- Guest account
	- Power Users - one click beneath Administrator account (can’t control other user accounts)
	- Performance Log Users, Performance Monitor Users, Backup Operators, etc. 
		- groups used by programs
		- e.g. running Performance Monitor allows users to view info for whole system

Linux and macOS permissions:
— R W X = read, write, and execute privleges
	- execute allows you to run script files (no need/want for things like word processing docs)

— owner - person that created and saved the file
— group - owner can set specific R W X for people in specific group
— everyone - owner can set specific R W X permission to everyone

— (on Linux:) right-click on file/folder -> “Properties” -> “Permissions”
— (on Mac:) right-click on file/folder -> “Get Info” -> “Sharing & Permissions”


File Explorer:
— primary tool to look at files and folders on a system
— quick launch from task bar or type “file explorer” into search
— customize icons, details, etc. 

— Navigation pane = left
	- Quick access - Desktop, Downloads, Documents, and stuff you’ve clicked on a lot
		- right-click on file/folder to put into quick access
		- pinned items will always be there
	- This PC - computer itself
		- right-click on This PC -> “Properties” = great way to get to system information
		- Drives
	- Cloud services - e.g. OneDrive account will always be here
	- Network - access shared folders/files on network
— Preview pane = right
— Details pane = right


sharing resources:

— Microsoft LAN Manager - tool used in “operating systems of your forefathers” (e.g. DOS), installed to look at other peoples hard drives - predates Windows (still on it today)

— NTFS vs. share permissions - 
	- Network shares - advertise out to network that particular folder is available
		- then have access based on NTFS permissions
	- Universal Naming Convention (UNC) - \\nameOfServingMachine\thing_shared
	- network shares doesn’t care what file system is (NTFS, exFAT, etc.)

— right-click on file/folder -> “Give access to” -> “Specific people…”
	- Microsoft best practices says: if you’re going to share something leave it wide open and use good NTFS permission control to limit what people can do.

— File Explorer -> Network
	-> an individual system will show network shared folders
	- mapping drives = right-click -> “Map network drive…” (give a drive letter)

________________________________________________________________
14. Maintaining and Optimizing Operating Systems:

patch management:
— updating built-in software to ensure they are the safest and most stable they can be
— enterprise environments often requires a form and committee

Windows Update (in Windows 7)
- Control Panel -> System and Security -> Windows Update
- 2 categories of updates: Important and Optional - Important = critical updates
	-> Change settings
	- automatically? when? check but let me choose? never? 
		- install updates automatically, choose when to install, check but let me choose, never
		- choose when to install
		- can choose Give me reccomended updates the same way I recieve important updates
		- can choose Allow users to install updates on this computer
		- MS products (Office, etc) can choose here
		- 3rd party tools (e.g. Adobe) sometimes have their own update utility
		- device drivers - have to go to site to see if update
		- Firmware - Update the System Setup BIOS

Windows Update (in Windows 10)
- Settings -> Windows Update
- choose active hours, see update history, uninstall, …
- no option to choose updates - can pause to delay, but can’t stop updates (unless Windows Enterprise)

patch management in Ubuntu Linux
- Software & Updates - manual updates
- Livepatch - slick interface

patch management in macOS
	- through App Store - pretty much automated too
	- Mojave has seperate Update appplication


working with disks:
— error checking - check for errors on HHDs and SDDs
— optimization - way to organize HDDs (lesser extent in SSDs) to run more efficiently

— chkdsk
— right-click on drive -> “Properties” -> “Tools”
	-> “Error checking” - click to run - details shows Event Viewer
		- checks file table for the partition and verifies each LBA block can read & write data
	-> “Optimize and defragment drive” -> Optimize (= disk defragment/defrag)
		- “trim” (on SSDs) - runs to identify AFU (“available for use”) pages and marks as such to start allowing rewrites/reuse of


working with applications:
— Control Panel -> Programs and Features
- tool used to find programs, see info, and uninstall
- applications don’t always uninstall nicely (leave Registry settings, temporary files, etc.)
- check website to see what it’s leaving behind (if gives message)


System Restore:
— focuses on applications, the Registry, and a few critical system files
— comes into play when adding/changing applications and device drivers - even if Windows doesn’t boot, can access restore points from Windows Recovery Environment

— System Properties -> System Protection ->
	-> “Configure…”
	-> “Create…”
	(-> “System Restore…”)


— system repair disk - a bootable media that helps with recovery (different from a backup) - requires an external mass storage device

Windows Backup and Restore (Windows 7)
- Control Panel -> Backup and Restore
	- Create a system image
		- Image-level backup - system itself, not applications
	- File-level backup 
		- Set up backup
		- choose external disk
		- Let Windows choose - everything + create a system image
		- Let me choose - select individual drives and y/n for system image

— Pretty much saved your entire system with: System Restore, System Image, and a traditional Backup

File History (Windows)
 - Control Panel -> File History - turn on - everything automatically saved
Time Machine (Mac)


Task Scheduler:
— Enables users to schedule repetitious tasks - MS Windows does a good job of maintaining and optimizing it’s OS so not often necessary
— many tasks are prescheduled by Windows (by default)
	- (e.g. Windows 10 automatically defragments hard drives every week)
	- Some driver updates may happen automatically, but not on a scheduled basis

— Control Panel -> Administrative Tools -> Task Scheduler
	-> Task Scheduler Libary -> Windows (choose a task)
	- “Triggers” - what actually sets off the task (e.g. Sunday @ 7pm)
	- “Conditions” - e.g. Wake system for task if off
	- “Settings” - e.g. Run task as soon as possible after a scheduled start is missed
	- “History” - listing of how many times task has been run
	- right-click on Task Scheduler Library -> “Create Basic Task…”
	- give task a name and description
	- select Trigger (e.g. Daily, Weekly, Monthly, One time, When the computer starts, …)
	- select Action (e.g. Start a program, Send an email, Display a message (last 2 depreciated))
	- select Finish


________________________________________________________________
15. Working with the Command-Line Interface:

— Command-line Interface (CLI) - alternative to GUI that runs in shells (e.g. Command Prompt PowerShell, Bash shell) that all store/share common functions - every command can be integrated into scripts

intro to scripting:
— batch file - a (“.bat”) text file where each line makes up a series of commands
— bash script - a (“.sh”) text file for scripting on Linux - provides powerful functions

— PowerShell - (right-click start -> “Windows PowerShell (Admin)) - allows easier ability to more advanced scripting functions (e.g. delete only logs that are 15+ days old)
	- extension = “.ps1” (a script is called a cmdlet)

— Notepad = a simple text editor on Windows
— integrated scripting environment (ISE) - color-coded text editor; highlights errors

— environment variable - certain phrases that point to certain places or things that work for anything throughout the operating system. (e.g. HOMEPATH=\Users\michaelm) - cd %HomePath%\Desktop\Logs


interpreted languages:
— executable files - have preset list of commands designed to talk to Windows & your CPU
	- compiled = code written in some language, and then compiled (by a compiler) -> a “.exe”
	- downside: different compilers for different OSes and CPUs (must program for Win/Mac env)
	- compiled languages = C, C#, …

— interpreted programs - don’t convert to a .exe; run code through interpreter and does what it needs to do
	- interpreters are built into OSes and (most of the time) work the same in all
	- interpreted (/“scripting”) languages = Visual Basic, Python, JavaScript, …

— variables - have values that can change based on how we manipulate them (types = integers, strings, etc.)
— comment syntax (objective term)

— conditional loop - for statement
— conditional - if statement
— functions - chunks of code that can run over and over again


— Visual Basic:
	 - extension = “.vbs”
	- comments = ‘
	- by setting variable types, can use less memory and have better controls on it
	- Dim - declares variables
	- pretty specific to Windows

— Python:
	- extension = “.py”
	- popular, runs on every operating system; known to be easy to read
	- will see a lot particularly in a Linux environment

— Javascript:
	 - “.js” - tool built into every browser to allow “web applications” vs static web pages
	- is interpreted in real-time on browser when you access a web app
	- Client-side applications - js is the tool
	- Server-side applications - accessing a database, etc.

________________________________________________________________
Chapter 16: Troubleshooting Operating Systems

Windows Recovery Environment:

— Windows pre-installation environment (WinPE) - mini operating system used to start the installation process
— Windows Recovery Environment (WinRE) - added utilities to WinPE - provides access to essential troubleshooting tools
— both loadable from a self-created boot drive or Windows Installation media (WinPE “Install now” vs “Repair your computer”)


advanced startup options:
— give you some very agressive ways to granularly start up your computer in just the way you want in order to get certain things done.  (on Windows -> )

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

—> System Configuration (Windows)
—> Settings -> Recovery -> “Advanced Startup” Restart now


kernel panic:
— things going horribly wrong - the OS doesn’t know how to deal with it - is crashing and can’t recover, and gives you one screen before dying:
	- macOS = Spinning Pinwheel of Death (SPoD)
	- Windows = Blue Screen of Death (BSoD)
	- Linux = some crazy screen of text

— most BSoDs are caused by hardware issues

________________________________________________________________
17. Display Technologies:

aspect ratios & resolutions:
— 4x3 - used by first gen monitors - basically mimics television - “black bars” on side is an adjustment to this
	- VGA - 640x480
	- SVGA - 800x600 (**Windows (most versions) downgrade to w/ video card issues)
	- SXGA - 1280x1024
	- UXGA - 1600x1200

— 16x10 - ties into the  “golden ratio” (16:10) - has asthetic that people like (used in paintings)
	- WSXGA - 1440x900 (popular in laptops)
	- WUXGA - 1920x1200 (popular for a long time until HD TV came around)

— 720p - “progressive scan” - makes picture all at once vs interlaced scanning (1,3,5,7,9… -> 2,4,6,8,…)
	- 1280x720 = first common 720p resolution (technically 1366x768 …)
	- QHD/WQHD - 2560x1440 (doubled res - popular for gamers)

— 1080p - classic HD TV - 1920x1080 - one of the most common monitor resolutions today

— 4K
	- 3840x2160 - “classic 4K” - x4 HD TV resolutions on one screen
	- 5120x2880 - 5K (especially seen in Mac world)


multiple monitors:
— don’t need a special video card, have them plugged into the same video card, or same resolution/size
— can duplicate or extend display(s)
— can orient L/R, top/bottom, portrait mode

— right-click on Desktop -> “Display settings”

________________________________________________________________
18. Essentials of Networking:

— network interface card (NIC) - snap into motherboard / (now, most often) built-in to motherboard - use RJ-45 to connect to network

—> Device Manager -> “Network adapters”
-> “Advanced”
- Duplex
	- full-duplex = talking and listening at exact same time
	- half-duplex = used e.g. cross-over cable connected systems

-> “Power Management”
- Wake-on-LAN - wakes a computer from off if certain information comes in
	- magic packet - used by admin when wanting to install an update on off computers (also via System Setup)

— link lights - seen on: the switch & connected computer(’s motherboard port)
	- 1. Connected - if connected properly - remain on & steady
	- 2. Speed light - changes color - can be the same light as “Connected”
	- 3. Activity light - always flickering

________________________________________________________________
Chapter 19: Local Area Networking

— netstat - command to view statistics for all network connections on system
	- shows: Proto (protocol), Local Address (IP + port num), Foreign Address, State
	- State
		= LISTENING (e.g. port 445? have LAN shared folders - port 80? - acting as web server)
		= ESTABLISHED - ongoing connections
		= TIME_WAIT - done w/ connection, waiting certain time to disconnect
		= CLOSE_WAIT - have already sent out a close and waiting for response/timeout
	- (note: IPv6 connections avail and shown too…)
	- can be a sign of malware if things are listening on ports you don’t know

— TCPView - a graphical netstat tool (by Mark Russinovich @sysinternals)
	- green highlight - on new connections establishing (e.g. opening a browser)
	- red highlight - shows the CLOSE_WAIT that are disconnecting
	- can right-click -> “End Process…”


working with Workgroups:
— NetBIOS/NetBEUI - original Microsoft methodology for network sharing - used MAC addressess exclusively (no TCP/IP) - useless outside of small LANs 
	- NetBIOS = the naming system (reduced you to ~15 characters)
	- NetBEUI = actually does the connection+communication between systems

— NetBT (NetBIOS over TCP/IP) - same naming convention, but now used IP addresses for connection (still MS)
	- Microsoft wanted to be able to use NetBT to send files anywhere on Internet so came up w/:
	- CIFS (Common Internet File System) —> 
	- SMB (Server Message Block)
		- Samba - SMBs popularity caused other OSes to create SMB protocols like Samba

— WORKGROUP - on a Windows network: on the same LAN + same WORKGROUP name = start seeing eachother automatically (File Explorer -> Network)
	- right-click on folder/file -> “Share with” -> “Specific people…” (-> select “Everyone”)
	- shows UNC (e.g. \\WIN7PC\Mike)
— — each system (on a network in an enterprise environment) may have same account names (e.g. “Mike”, “Fred”), BUT are really different accounts on different systems - often workaround using the same user+pass for both systems (bad practice!) - moving from Workgroups -> an Active Directory Domain fixes


working with Active Directory:
— domain controller - special dedicated (Windows Server installed) computer
— domain accounts - used (vs local user accounts like Workgroups) to share an account(s) on multiple computers without needing to set up a universal login account for every individual computer (now have real security)

— domain - a logical group of network objects (computers, users, devices) that share the same Active Directory database
— tree - a collection of one or more domains and domain trees (sharing a namespace) linked heirarchically in transitive trust
— forest - a collection of trees (sharing a common gobal catelog, directory schema/config, logical structure) - is the accessability/security border for users, groups, etc.

— Organizational Units - a container option (vs Groups) to organize all users & groups in an Active Directory Domain (e.g. separate multiple accounting departments in a large organization)

— a user can now have the same desktop when logged into any computer connected to the Active Directory
— an admin can now set up Security Policies that propagate through the entire domain (vs Local Security Policy)
— an admin can set up login scripts (e.g. pop-up message: “Be aware that computers will shut down automatically at 5pm today.”)
— a Domain admin has the power to add any computer to the domain (vs local admin)

— No longer use the local computer name - can be FQDNs (e.g. totalseminars.com) - or an in-house local domain account (commonly <name>.local) - can be safer - not webservers, so people from the internet can’t get to then.

— Control Panel -> System and Security
— right-click on file/folder -> “Give access to” -> “Specific people…”

** a Domain is a type of Windows firewall


Windows Sharing with Mac and Linux:
— all other primary OSes follow along with (the Windows developed system of using) Active Directory and folder/printer sharing

— LAN manager (old MS file sharing) —> Server Message Blocks (SMB)
— SAMBA - emulation of the Windows sharing tool built into macOS and (most) Linux
	- “smb” (or samba.conf) - a file used to set domain/workgroup/comp name
	- called “Windows File Sharing” on macOS

— net - a command (on Windows) to view/alter network sharing


firewall configuration:
— Firewall - to block traffic based on whatever type of criteria you think is important (more verb vs a thing) 
	- e.g. certain IP addresses, certain incoming port numbers - e.g. based on time of day, website keywords

— edge/network firewall - on router
— host firewall - on individual systems - can see/filter processes requesting/sending to/from internet

— Access control list - defines what users can/cannot do in terms of access (e.g. don’t want anyone playing Steam games between 9am-5pm)
— principle of least privileage - to only give people enough so they can do what they need to do (unless given accesses specifically, pretty much don’t have)
— blacklist - e.g. deny access to any of these listed IP addresses
— whitelist - e.g. only allow access to these specific IP addresses


— stateless firewalls - “block this IP address / port number no matter what is going on”
— stateful firewalls - allow/block based on the state/context of the situation (e.g. device askes for a webpage? OK. device asks for a webpage 15x in 5 seconds? NO. (often on SOHO routers - pretty much just turn on)

— access policy - ability to combine firewall settings to make unique to your situation (e.g. “I don’t want anyone accessing from this port number at this time of day”) - available on more agressive firewalls

— demilitarized zone (DMZ) - setting to send all traffic into network to one particular system (via IP address) - can be dangerous (** a DMZ exposes a LAN host to the Internet)
— Real DMZ - two routers on a network for DMZ (popular in schools)…
- (on a network) router #1 is connected to file/web servers and is running a stateful firewall - public access needs requires it to be pretty open to incoming connections (can rent for a /mo fee - regularly updated firewalls)
- router #2 is connected for internal use (computers, printers, etc. hidden behind NAT) and is running more a more agressive firewall


— Windows Defender Firewall
	- via Control Panel or Settings
	- Network discovery - Windows will query to find other computers, printers, video servers, etc.
	- change firewall settings based on connected network type:
		- Domain networks = to an Active Directory Domain 
		- Private networks = home/office
		- Guest or public networks =  airport/coffee shop
	

port forwarding:
(obj 2.10)
— simply means that your NAT-ed router is watching for certain port numbers to give remote access to (e.g. normally blocking incoming port 80, but want to view door bell, cameras, thermostat, etc.) devices typically hidden behind private IPs (NAT-ed) that cannot be access to by a browser outside of the LAN.
— tell router (via settings) to listen to a non-standard por (e.g. 11461) and direct traffic accordingly (e.g. 80)


— Dynamic DNS - software on routers to give you a DNS name, then, no matter what your IP address is, your router will call home and update — (via settings) choose a service (e.g. dyndns.org) -> give hostname (e.g. mikecamera1) -> browser access (“mikecamera1.dyndns.org:11461”)

________________________________________________________________
 20: Wireless Networking

wireless encryption:
— on a wired network - the only way to intercept traffic is if they can plus into your switch - a wireless network requires blocking with an SSID

— WEP (Wired Equivalent Privacy) - original 802.11 security protocol (modern 802.11ac routers still have setting) - required word-of-mouth to give out key (10 hexadecimal characters) to all connecting clients
	- RC-4 = ancient encryption form - predictable, able to hack it mechanically

— 802.11i - the “Wifi Alliance” decided to worked with “IEEE” to attempt to come out with a new standard - was going to have authentication (username+password or smart card) to get on network - was predicted by IEEE to take 3+ years to release.
	- TKIP (Temporal Key Integrity Protocol) = encryption form improving on predictablilty of RC-4
	- AES (Advanced Encryption Standard) = primary encryption used today (TKIP thrown out for)
		- difficult to get wireless network card to decrypt
		- used for: everything from secure webpages, voice over IP calls, etc.

— WPA (Wi-Fi Protected Access) - WAP manufacturers (e.g. Cisco, Linksys, …) came together to figure out what they could take from 802.11i concept and use immediately - used TKIP + RC-4 for (2) new authentication methods:
	- personal/pre-shared key - word-of-mouth passing of key to join network
	- RADIUS server - logging in w/ user+pass to this seperate box

— WPA2 - standard used today - released by WAP manufacturers once hardware caught up to be able to decrypt AES - has basically the same security protocol of 802.11i concept (still hadn’t released).


— WPS (Wi-Fi Protected Setup) - a method for devices to configure themselves onto a network (using “WPS” buttons on router & device + pin -> WPA2-PSK) - is quick/easy, but incredibly easy to hack (designed now for increasing delays on incorrect pin guesses, but still a weak choice)


enterprise wireless:
— tend to use lots of dedicated WAPs - placement and antenna selection is important
— tools exist to allow placement -> view heat map - shows dead spots / projecting outside desired area (expensive)
- e.g. want coverage in hallway? - directional antennas on both ends (“give long football shape”)
- e.g. individual offices? - dipole in the middle or patches in each office
- e.g. large, open office? - multiple dipoles or omni-directionals depending on space

— access WAP IP address through browser -> Web configuration
- “Extended SSID” - used to set up a single SSID name to use on all WAPs (must connect individually or have a specialty switch - automatically propagates ESSID and gives single place to manage e.g. users/captive portal)
- “Isolation” - wireless client(s) on network are only allowed to connect to WAP (no ping-ing, sharing, etc.)
- “Rouge AP Detection” - blocks any external WAPs from connecting without MAC address on list of known
- Rate Limit” - used to throttle up/downstream speeds of a particular SSID
- “Captive portal” - add a customized screen for network login via self-defined users (not a RADIUS/TACACUS+ user&password)

— WAPs don’t have firewall or DHCP settings (are not routers)
— want to set IPv4 as static


— power over ethernet (PoE) - allows devices (e.g. WAPs) getting electricity through ethernet cable (vs AC adaptors) via a PoE switch or PoE injector (device to bridge -> switch)
	- PoE (1st generation)
	- PoE+ - a lot more electricity provided to individual devices

— AAA (authorization, authentication, accounting) - using WPA2, but not PSK
	- RADIUS or TACACS+ (AAA protocols) - require an additional box to provide authentication
	- very agressive authentication (can add smart cards, etc.)

________________________________________________________________
21. The Internet:

Telnet and SSH:

— Telnet - an entirely unencrypted remote command-line tool over Port 23 - used to connect between computers before graphical OSes
— Secure Shell (SSH) - automatic point-to-point encrypted access to remote server command-lines
	- on initial connect: sends an encryption key (store locally? = “Yes”)

— PuTTY - popular Telnet client (comparable to browser = “web client”) over Port 22
	- Host Name or IP address = a FQDN or IP address for a Telnet server
	+ username and password
	-> CLI access on remote server

— e.g. servers, routers, “other boxes”


remote desktop connections:

— Remote Desktop Protocol (RDP) - protocol unique Windows over Port 3389
— System Properties -> “Remote”
	- Remote Assistance - when someone connects, both have mice, keyboard, monitor access
	- Remote Desktop - when someone connects, noone else can connect to it (will give warning on connect)
	- need IP address or computer name (ipconfig)
— remote accessing: search -> “Remote Desktop Connection” -> Options -> “General” -> input remote name / IP


— Virtual Network Computing (VNC) - a 3rd party remote desktop protocol bulit-in to other main OSes (Linux and macOS, not Windows)
— TightVNC - free (server + client) program that runs on top of VNC protocol
	- works on every OS (even Windows-to-Windows)
	- built into most Linux and Mac machines, not Windows
	- need to give IP address or FQDN
	- give VNC’s built-in password
	- “just want to run the viewer to see people who are sharing their desktops”
		


the World Wide Web:
— predominant method of viewing the Internet
— always manifests as a web browser (“of some type”)

— HTTP - traditional www protocol over Port 80 - insecure - wide open for anybody to intercept anything you’re doing 	- ok: direct connect to router for configuration
	- not ok: “real Internet”

— HTTPS (HTTP secure) - fully encrypted
	- Certificate - 3rd party signed (verified) keys allowing encrypted connections
		- Trusted Root CA
		- SSH hands you a key when you connect
		- you trust your own server
		- certificates provide lots of info:
			key, date issued, serial # (issued by authorizing body), name of exact website, etc.
	- HTTPS encryption protocols = Secure Sockets Layer (SSL) & Transport Layer Security (TLS)

typical certificate errors (given by browsers):
— expired certificate = NET:ERR_CERT_DATE_INVALID
	- people forget to renew
	- can be ok if you trust org/company - use best judgement
— revoked certificate = NET:ERR_CERT_REVOKED
	- taken away by issuing body for being caught doing something naughty / refusing to pay
	- best to refuse to enter
— self-signed certificate = NET:ERR_CERT_AUTHORITY_INVALID
	- used for inhouse webpages for encryption
	- for employee access (why pay for full-blown/signed?)
	- confirm url you entered is the one you want access to and proceed

basic network troubleshooting rules:
— 1. Check physical system first - link lights and connectivity via OS

— 2. Know your network! - document: network ID, router, DNS (ipconfig /all)

— 3. Know your Internet connectivity!
- use CLI applications to watch the router path your requests make:
	- Linux/Mac=traceroute
	- Windows=tracert www.ibm.com
	- multiple layers of routers before your request actually exits network? - could be bad
	- seeing only one server hop? - issue (likely) btwn the internal & gateway routers
- ping ftp.microsoft.com # ping FQDN and returns an IP = working DNS server
- ping myrouterip - reply = have good IP address & router running
- “ping, traceroute, and ipconfig”

________________________________________________________________
23. Portable Computing:

power management:
— AC adapter - plug->chare laptop batteries (lithium-ion, run great 2+ years)
— Vendor-specific ports - voltage, amperage, polarity (center point & outside ring +/-)
— laptop runs on AC, but dies when unplugged? - prob dead battery bruh
— not getting power? - check/replace the jack

## NOTECARD
advanced configuration and power interface (ACPI): 
- power config functions built into CPU
- sleeping computer = no OS = need BIOS to wake
- ACPI level 0 = enabled, but currently unused
- ACPI level 3 - sleep mode 
	- CPU shuts off
	- RAM keeps running - holds memory
- ACPI level 4 - hybernation mode
	- RAM -> file on HDD
	- (on Windows: “hyberfile.sys”)
####

power plans:
— HDD + monitor uses more power than CPU & RAM
-> Control Panel -> Power Options (also available via Settings)
 Balanced - at ACPI level 0 and running at full speed can: 
			- turn off monitor or hard drive w/out going into sleep mode
			- “turn off the monitor after 3 mins”
- “Choose what the power buttons do” = sleep, hybernate, or shutdown
- “Create a power plan”

________________________________________________________________
25. Care and Feeding of Mobile Devices:

mobile device security:
— Screen lock - always keep password, pattern, PIN, face recognition, etc.
	- time-outs
	- full device erase after certain num of incorrect attempts

— Multifactor authentication
	- e.g. particular app requiring login & code entered from sms/call
	- code from sms/call/“authenticator apps” - lost device = locked out without backup codes

— Locator apps
	- Find My iPhone
	- Android Device Locator
	- play sound (e.g. lost phone behind couch, etc.), device lockout, erase device

Mobile Device Management (MDM)
- security options available to enterprise environments
— Bring Your Own Device (BYOD) - less security options - careful what company stuff kept on device
— Corprate-Owned Personally Enabled (COPE) - security policies, lockdowns, app whitelist, …

________________________________________________________________
27. Securing Computers:

— “Host-based security” - protecting the individual system
— “Network-based security” - router, switches, and other computers
— “Physical security” - e.g. locks on doors, security guards

threats:
— Man-in-the-Middle - something between a sender and receiver (server and client) that is intercepting (email, wireless, webpages, etc.)
	- fix=encryption - outside sees traffic, can’t read
— Spoofing - to take on the look and feel of some other entity on any type of client-server situatation (email, webpage certificates, … other authentification forms)
		- fix=verify encryption to prevent mitm attacks and verify no spoofing
— Denial of Service (DoS) - ex: web server ready to respond and return pages - someone sends malformed HTTP requests that make server “sit and wait to figure out requests”
	-current/future requests =  “server is busy” (404 error, etc.)
	- #1 problem on the internet today
— Distributed Denial of Service (DDoS) - install/distribute malware onto “zombie” computers (hundreds, thousands, …) via email, etc. —> wait for evil server broadcast -> concurrent malformed HTTP requests

— Zero day = any new emerging threat type

“Things to watch out for”:
— Renamed system files = classic “hacker” root access move
— Denied of things you normally want to do (e.g. can’t get to desktop)
— Disappearing files, permission changes = root access
— fix: logs are available (e.g. people trying to SSH into your system through network)

physical security:
— 1. “Perimeter security” = keeping people off property
— 2. “Room security” = (e.g. room locks, badges, biometric locks)
- security guard = passive protection (=“not even going to try to get in”) - credential check
- “mantrap” - two-door airlock + guard, security camera, etc.
- “entry control roster” - sign-in via:
	- Badge reader - RFID-chip embedded badges
	- Smart card - swipe/insert for entry
	- Biometric scanners/locks (rare)
	- list…
— 3. “Individual device security” =
- cable locks - hold individual systems
- server lock - locks sever -> rack
- USB lock - physical block of USB ports (**software unplug warning/log)
- privacy screens - limit field-of-view (via polatization)
- key fobs - getting into parking garages, etc
- hardware tokens - device giving changing access code

passwords & authentication:
— hash = the result of a one-way algorythm - a value of fixed length (=bad) that varies dramaticaly based on the input, but always produces the same output (“mikeshashword” = “mikeshashword”)
	- on password creation: a hash is saved on mass storage (not the password itself)
	- on password entry: the input is hashed and compared to the stored hash

password recs:
— 1. Set strong passwords
	- (compTIA) always use upper and lower case, numbers, and extra characters (**CompTIA)
	- passphrase = loooooong passwords = creates entropy = harder to crack
	- use a phrase you can remember
— 2. Password expiration
	- (compTIA) best thing you can do is make passwords expire in 30-90 days
	- (reality) every ~6mo to avoid “administrative nightmare” (predictable/forgotten passwords, sticky notes, etc.)
— 3. Screensaver (+ password re-entry)
	- leave a system wide open? = easy access to password hash files -> thumb drive
— 4. Lockscreen required passwords
	- critical on mobile devices
	- longer than 4-digit pins smart idea
— 5. BIOS/UEFI passwords (admin and user)
	- these hashes are on firmware = almost impossible to get to them
— 6. Require passwords everywhere!
— 7. Multifactor authentication (!)
	- even with password files will be stopped cold

password cracking:
— Brute force - try every possible combination of all these hashes (once generated) until you get to the password.
	- rarely used any more, easier to steal hashes and crack at home
	- time to crack depends on the password(s) (have a certain length and complexity)
	- https://howsecureismypassword.net/
	** “reverse hashing” is not a password cracking technique

— Dictionary attack - using list(s) of known passwords/types that people commonly use (e.g. mike, mike1, password123, Password123,…)
	- https://crackstation.net/ 
— Rainbow tables - a dictionary attack using lots of (common/available) tables working together to create (“a zillion”) different hashes that easily crack.
	- passwords 8 characters or less = 30% crack instantly; given a few weeks, rare to find uncrackable


malware types:
— Virus - (old term) malware on a floppy disk, passed among systems
	- 1. replicate =
		- make copies of itself onto RAM
		- copy onto any floppy disk entered into system —> next system, etc.
	- 2. activate
		- (in the beginning) harmless, e.g. letters fall across desktop
		- (quickly evolved to) malicious things, e.g. erase the boot sector of hard drive
— Worm - malware using networking for replication (1st gen —> most malware today = over Internet)
	- e.g. email, netview fishing
— Trojan horse - a malware program that replicates (hidden) via purposeful downloads e.g. real game, making zombies
— Rootkit - (nefarious) malware that seats itself within the boot sector of drives, attempting to hide from the OS - modern anti-malware software sees

malware issues (“biggest today”):
— 1. Ransomeware -
	- “rogue anti-virus” = software claiming can run anti-malware, but are a virus themselves
		- search “free anti-malware” online thinking you think you have malware —> 
		- get a pop up to call a number and pay $x to unlock your system
— 2. Botnet(s) - bunch of zombified computers already under the control of somebody else
	- when computer is zombified, still running great, malware sitting and waiting while…
	- somebody (in some other country usually) goes to companies threatening DDoS for payment
	- then, at somepoint (middle of the night) your computer runs a little slower while it attacks
— Keyloggers - software recording keystrokes
	- must be somewhat visible to work; hide as some well-known program/service
— “Spyware” - any piece of malware that is spying on your system
	- basic/normalized = e.g. go to florist webpage, get a pop-up later (generic vs personalized)
	- more nefarious = trying to grab/transmit very specific things you do

“We can get into semantics here, and I might start arguing that 40% of the websites out there today are spyware. Just about anything that Google offers, I might argue, is spyware; atleast they’re honest and telling upfront they’re grabbing this type of information, and its ‘generic’, not personalized.”

malware symptoms:
— Pop-ups - manefest as separate windows; on-top/under yours (used for good)
— Browser redirection - sent to a different url than typed in (“ebay”—> “eboy”)
— Invalid certificates (Trusted Root CA)
— Security alerts - OS notification when noticing problems (e.g. above 2, system files changing, …)
— Application crashes - according to CompTIA objectives
— OS update failure - malware attempts to stop you from applying a known patch
— Spam - too many site logins and haven’t opted out
— Hijacked e-mail - stealing contact lists, using address for spamming (automated replies)

anti-malware types/efforts:
— Anti-malware (objective term) - “there’s no such thing as antivirus program” 
	- goal = always have running (preventative measure)
	- tons available, when in doubt, use OS built-ins
— Software firewalls - host firewalls on on your individual systems (“pretty much all malware these days like to phone home”)
— Backup/Restore - bail out and recover
	- “can’t count on anti-malware tools to always clean your system 100% of the time.”
— Secure DNS - the DNS provided by your ISP often logs where you’re going (used for redirection)
	- 1. Non-ISP DNS servers - “does not log” or make questionable redirects
		- e.g. Google’s 8.8.8.8
	- 2. Encrypt DNS requests (very secure)
		- a. set up a DNS server in your home/office
			- configure to create an encrypted connection to public DNS server
		- b. use services (CloudFlare on phone) to use VPN for encrypted DNS requests (only)
			- public, non-logging
— End-user education - teach malware symptoms

CompTIA’s 7 step malware process:
— 1. Identify and research malware symptoms
— 2. Quarantine the infected systems (take off network)
— 3. Disable System Restore (on Windows: stop from creating automated, pre-infected restore points)
— 4. Remediate the infected systems
	- 4.a. Update the anti-malware software
		- “definition files” - files containing the signatures of malware varieties
	- 4.b. Scan and use removal techniques (safe mode, pre-installation environment, bootable media)
— 5. Schedule scans and run updates (Task Scheduler if not preset)
— 6. Re-enable System Restore and create a restore point (on Windows)
— 7. Educate the end user


social engineering:
— the use of deception to get people to give away personal/confidential information that they wouldn’t normally give away
— telephone scams = e.g. IT department calling to collect passwords for a company-wide change
— phishing = malicious emails (/websites) pretending to be authorities, hoping for passwords/money/info
— “spear phishing” = directed towards a specific person vs anybody (“Were having problems with your bank account, please call this number or enter your username and password so we can correct this…”)
— tailgating
“malicious malcontents follow legitimate employees through locked doors, pretending they belong - after gaining access to a building all they have to do is wait for an employee to take a bathroom break to gain unauthorized access to an otherwise impenetrable network.”
— “shoulder surfing” = standing behind and watching passwords, secure documents, communications, etc.
—dumpster diving
“even the most tightly controlled offices often have an achilles heel - compaines have toppled and individuals have had identities stolen all by being careless with their refuse - shred all trash you don’t want prying eyes to see; after all,… one man’s trash, is another man’s treasure…”

 “It turns out we are the greatest threats to our networks… We all like to think that pale hackers typing away in basements pose the greates threat to our networks… It’s an evil we can understand, a threat that feels contained… but we live in a world where evil-doers prey on our virtues and turn them against us…”


Licencing:
— Bill Gates invented the concept of software licencing in “An Open Letter to Hobbyists” - he required licensing fee for the BASIC programming language
— End-user license agreement (EULA) - defines who the owner is, and how the software may be used (“sgranted a licence, not ownership”)
— Digital rights management (DRM) - attempts to help copywrite protect audio and video
— Commercial licence = code -> compiled -> executable -> world (as such - can’t reverse engineer, EULA)
	- Personal licence - on per-user basis
	- Enterprise licence - needed copies to a single organization
		- can licence every computer, but account for usage (e.g. MS Office for 100 active users)
		- Windows Server has licensing controls

— Open-source (licence) = 
— GNU General Personal licence (GNU GPL) - if you compile something, you have to provide the original source code (either with it or when asked) - if you add to something, you have to attribute “upon who

		- specifies that if you compile something, have to provide the original source code
			- either with it, or when asked
		- if you add to something, have to attribute (“standing on the shoulders of giants”)

— Commercial =/= $$ - can release software and give away (free), but keep propriatary (not gonna give source code)
— open-source software w/ commercial features - e.g. portions for sale, services/support sold alongside,

Windows’ per-processor licence
— “any workstation version of Windows (Home, Pro, Server) can be used on any computer with up to 2 physical CPUs on it”
- been around for decades
- was a problem for Windows when one computer has 2 8-core CPUs “=16 CPUs (functionally)”
- 4x 4-core CPUs = more expensive than 2x 8-core CPUs (in a server)
- (today) Windows Server has a per-core licencing agreement
- can be required to buy multiple licences for a single system
- installing a Windows OS on a VM counts against licence agreement (“Thanks Microsoft!”)
- “consider Linux for your server needs”


incident response:
— “an incident” = defined by organization
— “never unplug the computer”, “unplug device and take to server room”
—  take pictures, note other people around, time stamps, employee serial numbers, etc.

— 1. “Know your responsibility”
— 2. “Identify the problem”
	- Report Through Proper channels
	- Data/Device preservation (if you dat dude)
		- document the device
		- quarantine the device
	- Use of documentation (as specified)
	- Document changes (under “D:”)
— 3. “Keep chain of custody”
	- Tracking evidence
	- Document process

environmental controls:
— “Compliance to government regulations” = OCEA, industry standards, best practices, traditions, etc.
— Materials safety data sheet (MSDS)
	- check with for how to handle, environmental impacts, how to dispose of
	- will be general - tell you it’s poisionous/toxic, but not the number to call

— Temperature and humidity levels
	- “If you’re comfortable, your computer would probably be happier if it were even colder and dryer.”
— Proper ventilation
	- hotspots under desks / in enclosures
	- Dust and debris (construction sites, smokers,) - can cause shorts, etc.
		- filters on enclosures
		- air filters, maskes (protect you)
		- compressed air
		- home vaccums - generate tons of static charge
		- anti-static vacuum - can be expensive
— Battery backup (critical systems)
— Surge suppressor

________________________________________________________________
Chapter 28: Operational Procedures

“Documents You Need to Know”:
— Network topology diagrams (computers, switches, printer, routers, etc)
	- Logical diagrams = drawing of devices, network IDs, IPs
	- Physical diagrams = drawing of floor plan, cable runs, types, distribution frame

— Knowledge Base - databases/articles of organized info of OSes, software, tools, etc.

— Regulatory and Compliance policy
	- Laws, Industry standards. Best practices. Traditions, Common sense

— Policies
- Acceptable Use policy - what you can/can’t do with company equipment (certain sites, no company hardware home)
- Password policy - minimum length, type of complexity, how often to chage, who’s in charge of this, where to store passwords

— Inventory management
	- “asset tags” = barcodes on stickers used to identify devices

Data You Need to Know:
— Personally identifiable information (PII) = e.g. SSN, phone number, address
— Protected health information (PHI) = e.g. blood type, what doctor has been treating for, vaccines (strict laws)
	
— EU General Data Protection Regulation (GDPR) - rules that you as a person have the right to control the information people gather from you (maily web)

— Payment Card Industry Data Security Standard (PCI DSS) - if you want to accept credit cards, you have a responsibility towards that data (via banks that issue credit cards)
- more a responsibility for companies that produce card swipers & mecrchendising services for sites vs small businesses

— “As an A+ certified technician be aware of putting info on thumb drives & file permissions.”

Change Management:
— organized, smart, carefully set up system to allow changes within enterprises (save from loss of $$, equipment, people, etc.)

— Change board - approve/disapprove change requests (monthly/quartely)

— “Documented business processes” - change you want to make and how it will improve the way the business practices (expected costs, etc.).
— Purpose of the change - “to improve productivity”
— Scope of the change - who is effected
— Risk analysis - downsides? time to make the change? training involved? chance of incompatability?
— Plan for change - e.g. how is the equipment going to be bought in? who’s loading dock is going to be picking it up? who is going to be assigned to install it? doing it over the weekend so the accounting department isn’t down? overnight? how are we going to handle training?
— End-user acceptance
— Backout plan - keep old monitors in a warehouse for 90 days?
— Document changes
— Lessons learned


The Zen of Backup:
— “Disaster recovery starts and ends with restorable backups”
— Backup and recovery - 
	- Image-level backup = entire drive: OS, apps, data
	- File-level backup
— Backup testing
— Cloud storage
— Account recovery options


recycling:
— “more than just being a good denizen of the planet… just get an old drill, punch three holes in it, and nobody’s gonna ever read that data”

— Batteries
	- alkaline batteries - (e.g. AA) cannot be re-used or recycled.
	- lithium-ion batteries - heavy metals and toxins that can be safely recycled
— Toner cartridges - can be refilled by recycler
— CRT monitors - metals
— Cell phones and tablets - delete accounts & factory reset

data destruction:
— Low-level format (old) - HDDs only - sectors being preassigned at factory
— Standard format - remove cataloguing and indexing (“difficult to get to the data”)
— “Drive wipe”/overwrite - writing data over and over
	- “zero wipe”
	- “military standard wiping rules” = zeros -> random 01 patterns x7
	- Degaussing machine = destroy via massive magnetic field
	- Shredder
	- Incineration
	- “Certificate of Destruction”



