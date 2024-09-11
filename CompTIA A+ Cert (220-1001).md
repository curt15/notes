Links: [[TECHNOLOGY]]

--- 

CompTIA — Computing Technology Industry Association

michaelm@totalsem.com

A+ Certification
— De facto, entry-level certification

Core 1 (220-1001)

Mobile (iOS, Android, tablets, e-readers, 
Networking (cabling, switches, routers, firewalls, wireless access points)
Hardware (motherboards, CPUs, mass storage, RAM, monitors)
Cloud (virtualization - AWS, )
Troubleshooting

home.pearsonvue.com

https://www.totalsem.com/blog/testing-strategies-for-comptia-exams/


— His comptia A+ certification book
— total seminars online practice test
— “First, schedule the exam.”

Tools of the Trade
— phone
— #2 philips head screwdriver

— nut driver w/ bits, hemostat (foreceps for screws), tweezers, spudgers (pry open mobile devices), pry bars (similar to spudges, plastic), voltage tester (volt/ohm meter aka multimeter), thumb drives (personal stack of software - tools, anti-malware,)
— [Old, but showing: IC inserter (designed to plug in integrated circuits)]

__________________________________________________
Chapter 1: Safety and Professionalism

Troubleshooting Theory

— Always consider corporate policies, procedures, impacts before implementing changes.

Step 1: Identify the Problem
— Question the user
— Inquire regarding environmental or infrastructure changes
“Not saying ‘what’s broken’, identifying the problem”
— Review system and application logs

Step 2: Establish a theory of probable cause (question the obvious)

Step 3: Test the theory to determine cause
— If theory isn’t confirmed, re-establish new theory
— Escalate the issue, if necessary

Step 4: Establish a plan of action to resolve the problem and implement the solution

Step 5: Verify full system functionality and, if applicable, implement preventative measures

Step 6: Document findings, actions, and outcomes

[** exam tip: Comptia loves their troubleshooting theory. Need to understand these steps and their order.]

___________________________________________
Chapter 2: The Visible Computer

Primary PC Connections:
— System unit: the computer. (contains the motherboard, CPU, RAM, and hard drives; everything other device is a periphrial)
— Monitor: the output interface (visual output)
— Keyboard and mouse (input)
— Printer (paper output)
— Speakers (audio output)
— Game controller (input)
— Webcam (visual output)
— External hard drive
— Headset (audio output)
— Microphone


External Connections:
(obj 3.2 - identify common connector types)
— connection, connections, jack, port - interchangable terms

— Universal Serial Bus (USB)
— network cable connections (RJ-45)
— sound connectors
— video connectors: Digital Video Interface (DVI), DisplayPort, HDMI (High-Definition Multimedia Interface)
— power connectors

older, less common:
— mini-DIN (PS/2) - keyboard & mouse - making a resurgance for pc gamers
— parallel port (LTP port) - printers
— Serial port
— Video Graphics Array (VGA) - monitors
— S-Video connector

laptops:
— Anti-theft connector
— Mini DisplayPort
— USB C connection
— SD card slot
— optical media


Inside the PC:
(obj 3.5 Given a scenario, install an docnfigure motherboards, CPUs, and add-on cards)
— Power supply
— Video card
— Motherboard - primary device to connect the innards together
— RAM stick
— Central processing (CPU) (Intel Core i9)
— M.2 SSD (mass storage)
— Expansion slots (PCIe)
— Chipset - defines the different features (allowable supported ports/expansion)
— Front panel connectors
— 


What is a Computer?:
(obj 3.5)
— CPU - computes “programs” that manipulate pariphrials and create files to get stuff done
— mass storage (M.2 SSD) - static storage hard drive - store data when not using it
— running a program: CPU asks mass storage to take a copy of program, moving it to RAM (random access memory), running the program, CPU instructs data written to RAM, copied to mass storage
— operating system
— PC, laptop, tablet, phones, raspberry pi, ip camera, washer/dryer, routers / wireless access points all contain everything to be considered a complete computer (CPU, RAM, mass storage, operating system)


___________________________________
Chapter 3: Microprocessors

What is a CPU (central processing unit)?:
— brain of the computer itself; incredibly powerful calculator
— “a man in a box” analogy - external data bus (8 lights in, 8 outside) 
	- 8 bits = 1 byte
	- binary (0/1) on/off
	- Machine language (code book) - every CPU runs code based on a specific machine language
	- 4 registers of 16 lightbulbs (AX, CX, BX, DX) “general purpose registers”
	- Intel 8088 code:
		- 10000000 The next line is a number; put in the AX register
		- 10010000 The next line is a number; put it in the BX register
		- 10110000 Add AX to BX and put the result in AX
		- 11000000 Put the value of AX on the External Data Bus
	- Clock - tell the CPU to do something; resets registers

		- 10000000
		- clock
		- 00000010 (binary “2”)
		- clock
		- 10010000
		- clock
		- 00000011 (binary “3)
		- 10110000 —> (AX becomes the result of “2+3”)
		- 11000000 —> 00000101 (binary “5” on external bus)
	
— Different functions inside CPU (interger math, long numbers, cache) - modern CPUs have more than the simplified 4 register example above
— “Pipeline” - lots of stuff running simultaneously (aka a core) to optimize the processing command
	- prefetch - decides what to do with command —> interger math / long numbers —> cache
— The external data bus is the set of wires that carry data and instructions between the CPU (register is a memory location within) and the RAM.

CPU Speeds and Cores:
(obj 3.5)
— Gigahertz (GHz) = 1 billion cycles per second — common measurement of CPU clock speed
— 1 Hertz = 1 cycle per second 
— maximum speed that the CPU can go
— 2 predominant companies: Intel or AMD (speak the same machine language)
	- AMD Ryzen (+ some number = generation, speed)
— System crystal - quartz oscillators - act like a metronome and push the system foreward
— 400 Mhz max speed of motherboard
— 1 MHz = 1 million cycles per second
— Clock multiplying - takes beat from the system crystal and multiplies it (x10, x30, ) built into the CPU itself. Used to reach the Max CPU speed

— CPUID CPU-Z = freeware to view 
— Microarchitecture - design of the internals of the system itself
— Wattage
— BUS Speed 100 MHz, multiplier x33 (8-36) - slow down and speed up based on temperature
— Make sure when buying a motherboard it is designed to work with a particular make, model, and model number of a CPU
— Overclocking - makes systems unstable, but allowing the CPU to perform above reccomended top speeds

— Multiple cores - multiple pipelines to deal with more than one “thread” at a time
— Hyper-threading - 1 super smart pipeline that can handle 2 pieces of code at one time
— Each core acts like a CPU
— Resource Monitor (Activity Monitor - MacOS)


Caching:
(obj 3.5)
— CPU caching works between RAM and the CPU:
	- Harddrive —> RAM (individual lines of code) —> CPU 
— CPU has SRAM (faster RAM) for the pre-fetch to move code -> cache
— Pipeline stall - when code isn’t there when it’s needed. Use a few hundered ticks of the clock to go and get the lines of code we need; something we want to avoid at all costs.
— Every CPU comes with 3 caches:
	- Level 1 cache - 64k of RAM - so fast it runs at the multiplied speed of the CPU
	- Level 2 cache - 128-256k RAM - feeds the Level 1 cache - runs at ~1/2 the CPU speed
	- L3 cache - megabite size RAM - runs at motherboard speed
— Set association - defines how the different types of caches are efficient at being able to hand the right piece of code up to the CPU itself.
— AMD - really really big caches
— Intel - really small caches, really really smart


CPU Sockets:
(obj 3.5)
— As things get faster, busses get wider, and processing power becomes stronger, the physical CPU must change a lot. “Sockets” can be used in defining the size/shape of the socket, or the socket itself.
— Microarchitecture - the system diagram on the inside of the CPU. Not done through sodering, actually a “photolithographic process” (silkscreening a t-shirt) - etching away silicon to create millions-billions of microscopic transistors that creates the CPU itself.
— Family names - (“Coffee Lake”) - with same microarchitecture, but different (i3, i5, i7, i9) models
	  Intel: (generations of i3, i5, i7, i9)
	- Nehalem (1st Gen)
	- Sandy Bridge (2nd Gen)
	- Ivy Bridge (3rd Gen)
	- Haswell (4th Gen)
	- Broadwell (5th Gen)
	- Skylake (6th Gen)
	- Kaby Lake (7th Gen)
	- Coffee Lake (8th Gen)

	— Intel Core i7-5820k
		- 5 (2-9, for generation)
		- 820 (SKU)
		- K (or U, low power)
	** Doesn’t tell us about speed, catching, etc. Can have multiple i7s that span multiple microarchitectures. Must research. 

— PGA (pin grid array) vs LGA (land grid array) - pins to fit into little sockets on chip vs land grid that connects to pins on the chip

— Intel vs. AMD:
— Intel:
	- LGA 1151 (number of pins) - middle of road / mainstream
	- LGA 2066 - “enthusiast”
— AMD:
	- AMA4 - middle of road / mainstream
	- TR4 - “enthusiast” / high end work stations


Installing A CPU:
(obj 3.5)
— Choosing a motherboard to match the CPU you want (socket type & speed)
— AM4 socket (AMD in this case)
— “Zero insertion force socket” - has a little bar/arm to lock it in
— Antistatic wristband - protects chips and electronics from electrostatic discharge
— Don’t touch pins on CPU
— Orientation notch - shows specific placement orientation
— OEM CPU (comes with an OEM fan)
— Thermal paste - pulls heat from CPU into the cooling system
— Connect fan to specific 4-pin connector on motherboard
— RGB LED lights have specific connectors


Liquid Cooling:
(obj 3.5)
— Alternatives to OEM fans that come with the CPU (third-party fans) to:
	- 1. Overclock (pulls added heat)
	- 2. Quiet fans (low rate of speed)
— 2 hoses: 1 to pull away hot fluid, 1 to return cold fluid from cooling block in radiator using a pump

______________________________________________
Chapter 4: RAM

Ram Technology
(obj 3.3 - Given a scenario, install RAM types)
— SDRAM (synchronous DRAM) - original RAM type - “synchronous” meaning, synchronized to the same crystal. 168-pins. 2 notches. Runs whatever speed the motherboard runs. 
— DDR SDRAM (double data rate) - for every 1 given click of the clock, gives us 2 bits of information - huge breakthrough - 184-pins, 2-notches—  ClockSpeed (100 MHz, 133, 166); DDR Speed Ratings (DDR-200, -266, ) = double clock speed; PC Speed Rating (PC-1600, -2100, -2700) = DDR speed rating in bytes (x8)
— DDR2 - 240-pins, 2-notches (offset from others to differentiate when installing correct RAM) — CoreRAM Clock Speed (100 MHz); DDR I/O Speed (200 MHz); DDR2 Speed Rating (DDR2-400) = 4x clock speed; PC Speed Rating (PC2-3200) = x8 ** always multiply by 8, will be on exam
— DDR3 - 240-pins, 2-notches (again, offset) - doubles I/O speed again; short-lived — CoreRAM Clock Speed (100 MHz); DDR I/O Speed (400 MHz) = x4; DDR3 Speed Rating (DDR3-800)=x2; PC Speed Rating (PC3-6400)=x8
— DDR4 - 288-pins, 2-notches (offset) - fastest ram and most common — Clock Speed (200 MHz); Bandwith (1600 MT/s) - Megatransfers vs just ticks of the clock; DDR4 Speed Rating (DDR4-1600); PC Speed Rating (PC4-12800)

Ram Capacity
— RAM is based on a square - each side is doubled (4x bigger) 265mb -> 1G -> 4G -> 16G
— Double sided RAM (vs single-sided RAM) - organized into 4-bits (vs 8-bits) - only downside is certian motherboards may not support
— RAM sold in pairs
— Channels - slots to place RAM sticks. 
— Dual-channel memory - need to place 2 RAM sticks of identical size and speed into specific slots determined by motherboard book. Will work w/ one, but generally requires in pairs.
	- provides simultaneous access to two RAM modules while reading or writing
— Different speed RAM 
	- empty + 8GB + empty + 8GB = 16GB total RAM
	- 4GB + 8GB + 4GB + 8GB = 24GB total RAM
	- 4GB + 16GB + 4GB + 16GB = 40GB total RAM


RAM Features:
— Parity vs ECC (error correction code)
—ECC RAM and Parity RAM can function with a failed memory chip
— Parity / ECC RAM - still DDR ram - adds an extra chip (“parity chip”)
	- w/ Parity 1 can be bad; w/ ECC 2 can be bad
— Must be supported by motherboard
— ECC RAM usually found in server-grade computers

— SO-DIMM (small outline) - laptops - designed for where long sticks don’t work - nothing functionally changes

— SPD Chip (serial presence detect) - allows system to querey the RAM chip for capacity, speed, technology, make/model - need tool (CPU-Z — “timing table” used for overclocking)


Installing RAM:
— Make sure have correct RAM via motherboard book (size max, speed)
— Line up notch w/ notch on the RAM stick itself; drop directly in; push until tab clicks
— Boot-up screen will show RAM - if lower than installed, re-check installation process
— If already has memory installed: snap in, boot up Windows, and check system for amount of RAM.

______________________________________________________
Chapter 5: Firmware

What is the BIOS?:
(obj 3.5)
— motherboard assumes connections to certain types of hardware
— sometimes needs to communicate even before booting into the OS
— known as our Basic input/output services (BIOS)
— BIOS programs are code. 
— Firmware means that code is burned onto a chip (nonvolatile media) vs software copied onto magnetic/electronic media
— m-BIOS & b-BIOS - two copies (Backup BIOS)
— ability to talk to mass storage devices w/o Windows (to test it)
	- Power-On Self-Test (POST routines)
	- System Setup (CMOS - complementary metal–oxide–semiconductor) Utility

POST:
— When booting, the power-good wire (when recieving enough electricity), will signal to run POST.
— simple program - “If you can hear me, check yourself out.”; responds: “I’m great.” w/ little beep
— Beep codes - primitive POST error codes
	- “No RAM” beep code will repeat until you power down system
	- If POST gets atleast to successful video output - will give information there (display codes)
— POST cards - hexidecimal (2-digit) read-out that shows POST error if system doesn’t get to sucessful video (testing of “dead” computers). Motherboard book will show the different error codes (e.g. 2b-2f = memory initialization - “maybe there’s a problem with RAM” -> reseat it)
	- Can be sold and installed ~$30


System Setup:
— Original BIOS (ancient) 16-bit
— Unified Extensible Firmware Interface (UEFI) BIOS - the updated BIOS
— System Setup - interface to make changes to the changable part of our BIOS. (CPU frequencies, RAM timings, BIOS passwords, boot options, and more…)
	- Hold down particular key (typically DEL or F2)

— Main - utility to show what is happening to system
	- Security - allows setting passwords for admin system setup password, user password that won’t boot without
— Ai Tweaker - overclocking
— Advanced
	- Onboard Devices Configuration
	- Disable Front USB connectior
	- Disable network cards
	- Serial Port Configurations
— Boot
	- anti-malware
	- set boot drive options
— Tool
	- “flashing your BIOS” - check update for BIOS

Troubleshooting Firmware:
— Last place you would check for problems. As long as not abused, pretty safe stuff.
— Real-time Clock (RTC) - single, flash, ROM chips - Read Only Memory that can be “flashed” to reprogram/update BIOS
— (vs old type where double-e prom - programable read-only memory - done once in factory && real time clock w/ built in CMOS - actually programmable via System Setup 64-bites)
— RTCs in a network must be synchronized (milisecond closeness) or they wont even boot up.
— Chips need electricity - CMOS battery (e.g. CR2032 is standard) used to provide back up power to keep clock 
	- lose time (or time slows down - clock 20 mins behind) - can lead to system not recognizing setup instructions / passwords if ($2) battery dies.

— Biggest problem in BIOS is people changing settings - “mess with it, but don’t save”
— Choose EZ-tuning to “normal”/base/default to reset 
— Flashing the ROM updates the firmware on flash chip - doing impropely can be worst error to make.
	- Good power - make sure you aren’t going to run out of electricity while this process takes place. 
	- Bios Flash image - make sure you have a complete back up of the flash files
	- know why you’re doing it - e.g. prepare for faster available tech (i9 CPU), fix bugs, 
— Often come with 2 bias chips in case of error

quiz:
1.) BIOS programs that enable hardware to function are called what?
— CMOS: is a type of memory chip (ANSWER)
— POST: is a testing program
— Services: are BIOS programs that make hardware functional
— Device Drivers: make hardware function in an operating system

2.) For which failures would you expect POST to issue beep codes (choose 2):
— Video Card (ANSWER)
— Missing keyboard, No printer found, No network connected - can be shown on screen
** The POST program will not run at all without a CPU installed (and thus, would not generate a beep code)

_____________________________________________________
Chapter 6: Motherboards

Form Factors:
(obj 3.5)
— Form factors - broad standards in the industry that define very specific physical dimensions for motherboards, cases, holes/mounting, etc.
— I/O area - fit in the same space - external connectors 
— Exam tip (motherboard form factors): 
	- ATX - biggest common form factor (12x9.6in)
	- MicroATX form factor - (9.6x9.6in)
	- Mini-ITX - smallest common form factor 
	- ITX form factor - larger mini-ITX - mostly unused
— Particular power connectors can be used in all above motherboards because of standardization of form factors.
— I/O shield - shape is extremely fixed


Chipsets:
— highly specialized single purpose chips —> dedicated chips that take on jobs
— Northbridge, Southbridge - designed to work together N: CPU, RAM, video interface - faster stuff; S: harddrives, keyboards, USB, etc. - slower stuff
— Today’s CPUs take over all Northbridge functions (chipset = Southbridge)
— Chipset = most critical part to determining what a motherboard can do (define amount of RAM, speed, num USBs, etc.)


Touring the Motherboard:
— Motherboards come with cables, standard connectors, and more.
— The motherboard manual provides essential setup information
— keeping on anti-static bag
— SATA cables - connects HDs or SSDs to the
— SATA HDD connectors 
— power connnectors
	- voltage regulators or capacitors - breaks down voltage (hundreds of differing needs)
	- Pro Tip: capacitors bubble up when breaking, time to get a new one unless master sautering
— I/O area

— PCIe expansion slots - dominant type of expansion slot using serial connections (sends data on 1 wire, recieves data on 1 wire) that offers multiple lanes.
— PCI was the precursor - 32-bit wide bus - but faster to send 32 pieces of data on 1 wire vs 32 wires (parallel vs. serial) - receiving device has to check for recieving of all data (creating latency) that doesn’t need to happen with serial. 
	- 16 lane PCIe (x16) - graphics cards
	- single lane (1x) 
	- 4-lane PCIe (x4) - 

— usb connectors:  “dongles”
	- serial port
	- vga connector
— ssd drive


Touring the Case:
— Tower case - designed to store a ton of drives
— Front connectors: on/off switch, USB connectors, harddrive activity light, audio connections
— Standout - screws/holes that we place the motherboard on (standardized)
— Fans
— Pass throughs - Holes for Cable management
— Hard drive mounts (drive bays)
— Power supply
— Optical drive


Installing a Motherboard:
— mike tip: connect CPU+fan+ram+power supply ahead of time and test that can get to boot screen before installing into the case.
— snap I/O shield into place
— pull out all cables
— dry fit to make sure it all fits correctly (onto standoffs and I/O area into I/O shield)
— screw in (don’t worry about extra holes in motherboard that don’t have a standout)
— read case/motherboard documentation to begin connecting cables
	- +/- matters on things like harddrive light 
— 3- or 4-pin connectors for fans

_________________________________________________
Chapter 7: Power Supply

The Power Supply:
(obj 3.7 - Summarize power supply types and features)
— ATX style power supply = predominant used in PCs
— 
— ON/OFF switch
— red slider - european (230v) vs US (110v) voltages - rare today as autosensing
— Fans
— Step-down transformer - convert AC -> DC power
— ATX Power connector - 2 pieces - 20-pin connector + 4 more pins
— ATX 12B power connector - provides power to the CPU
— 12v=yellow, 5v=red, 3.3v=orange
— ATX12V - standard that allows more power to the motherboard
	- 1-2 connectors for 4-8 pins total depending on motherboard (P4)
— Molex - general purpose
— mini connector - originally for floppy drive
— Sata power connector - hard drives, optical media
— PCIe connector - video cards

— Modular Power Supply - rather than winding up unused cables into case


Mounting a Power Supply:
— sometimes separated in it’s own case section
— heat blows out the back
— can use fan underneath to pull hot air out of entire case or pull cool air in to cool power supply

— mount power supply in case with four screws
— orient the power supply so fans draw air from system
— connect motherboard primary and secondary power
— Modular PSUs offer less cable clutter than non-modular PSUs


Choosing a Power Supply:
— buying based on watts
— Volts X Amps = Watts, but power supplies aren’t perfectly efficient
	- lost through heat, resistance, etc
— How many watts do I need? - Subjective question. Not tested on exam.
	- depends on GPU, hard drives, etc
— Total that you need/get will only be a percentage of what you use (unless constantly playing high end games / accessing HD / etc) - rule: get a PSU with a little more wattage than your system needs
— 1500W = highest commonly found
— even a 60% efficiency is good
	- 575W @ room temperature (heat reduces efficiency), quality of electronics
	- 300W otherwise
— 80+ ratings - high efficiency power supplies
	- percentage of rated load
	- higher up (80 platinum, etc) = better efficiency

— modular vs soldered - convenience vs potential efficiency reduction


Cooling Your PC
(obj 3.5)
— Heat sink - anything that can take heat from another device
	- on CPU: big copper block w/ hollow tubes + cooling fins
	- heat -> fins -> dissapate into environment
— Fans - active cooling function
— pull cool air from front and top in and push hot air out - mainly the CPU fan / holes
— Overheat = Reboots
— Fans = Noise
— PWM connectors - 4-pin connectors for fans - allow CPU to tell fans when to turn on/off
	- most modern motherboards handle this timing for you
	- System Setup allows to set: warning temperatures (beep), fan fail warning, % of max temp to run fans at. 
	- SpeedFan - software to configure fans
	- “Fan speed and noise can be controlled through firmware or software”
— 3-pin connectors for fans - continuous
— Liquid cooling is the quietest solution
— Small fans (which have to spin faster to move the same amount of air) tend to be louder than large ones


Troubleshooting Power Supplies:
(obj 5.2 Troubleshoot problems related to motherboards, RAM, CPUs, and power)
— #1 component inside computer most likely to die are power supplies
— Massive capacitors that act as the primary surge suppressors for your system
— Going to die really quickly (smoke, burning plastic smell) or really slow
— Best way to tell is to test it - power supply tester
	- Slightly lower voltage normal, but can be preliminary warning of slow death
	- can use tester to test individual connectors
	- A “carefully bent paperclip” - green to black to test if fan turns on
— Multimeter V with squiggle (V~) = AC
— Multimeter V with line and three dots (V—…) = DC
	- setting to lowest closest to 12v (20 in this case)
	- don’t need a CPU installed to test this way
	- using piece of metal to connect to turn on PC
— Swapping out power supply when symptoms present

— Power supplies die slowly and cause intermittent problems (rebooting, etc)


Troubleshooting Core Components:
— New build (everything minus HDs) - getting to point in BIOS where says nothing to boot from
	- good place to be - means CPU is mounted properly
— Easy to put RAM in the wrong place - first boot gives a beep code
— CPU overheating causes shutdowns and reboots
— Need some type of graphics to boot system up
	- Intel - all CPUs (some w/ graphics, some w/o); AMD - CPU or APU w/ built in graphics.
— On initial set up: No noise, nothing on screen, but fans on… start over! 
	- Incorrectly installed CPUs or RAM can make it seem like your PC is dead
	- normally he installs the CPU, GPU, and PSU outside of case to see if system boots up

— System lock-ups - gone through System Setup, made some mistake, and nothing is working
	- Clear CMOS jumper - 2 small posts on every motherboard - use metal to short posts for ~30s to bring System Setup back to original settings.

— Loud noises - from fans in contact w/ cables, etc. or obvious from PSU
— LEDs - no standardization here
	- system recognizes good RAM installed on connectors, etc.
— System Setup good place to view RAM installed
— memory checking program to confirm good RAM
	- live CD / thumb drive can be used to boot to Windows w/ WinRe to check
— Smoke coming out of the system - unplug system & fire extinguisher if necessary


___________________________________________
Chapter 8: Mass Storage Technologies
(obj 3.4 - Given a scenario, select, install and configure storage devices)

Introduction to Mass Storage:
— Optical media - tracks ~1000 bytes
— Magnetic media - sector ~ 512 bytes, etc
— Solid state - blocks - blocks ~1000 bites
	- Bottom line: All storage devices have some hundreds of thousands of “logical atoms”

— Logical block addressing (LBA) -
	- controller circuitry + OS —> allocating “blocks” 
	- 4TB HD; each block = 4096 bytes  (0 - 1 billion blocks)
	- inherent to all Operating Systems (just plug in & make sure recognized in BIOS)

— Capacity:
— base 10 mathematics: 0 1 2 3 4 5 6 7 8 9 10
	- 1,000 = kilo
	- 1,000,000 = mega  (1,000 kilos)
	- 1,000,000,000 = giga  (1,000 megas)
	- 1,000,000,000,000 = tera  (1,000 gigas)
	- 1,000,000,000,000,000 = peta  (1,000 teras)
	- 1,000,000,000,000,000,000 = exa  (1,000 petas)
— binary: (thinking about external data bus and num of possible patterns via number of wires)
	- 2^10 = 1024 Kibi
	- 2^20 = Mebi
	- 2^30 = Gibi
	- 2^40 = Tebi
	- 2^50 = Pebi
	- 2^60 = Exbi
	** names like this = IEC values
— so we have two naming systems with similar values…
	- Kilo is similar in value to a Kibi
	- Mega (1,000,000) is similar in value to a Mebi (1,048,576)
	- Giga (1,000,000,000) is similar in value to a Gibi (1,073,741,824)
— Drives sold “4TB” are as decimal values, but computer interested in LBA values, which are binary, so will see a variance on screen.

— physical size:
	- 5.25-inch mass storage
	- 3.5-inch mass storage - dominant form of mass storage
	- 2.5-inch - primarily laptop, but more popular even in larger systems to fit more drives
	- 1.8” mass storage - popular w/ SSDs, but short lived
	- m.2-format mass storage - dominant solid state mass storage format today


Magnetic Disk Drives:
— Hard disk drive (HDD) - has motor to spin
— spinning platters to store data via magnetism and read/write heads (little arm w/in nanometers of platter) to read data stored in:
— Sectors - smallest unit of storage
— physical size: 3.5- and 2.5inch drives = big sizes (1.8” exists)

— Advanced Technology Attachment (ATA) - language to speak to drives
	- Parallel ATA (PATA) - old interface, not on exam, rare to see on systems
	- Serial ATA (SATA)
		- SATA connector - smaller connector = data; larger = power
		- SATA is a serial interface; all data moves in sequence (serial) over a single wire
— Pretty much all motherboards today have built in SATA controllers.
— Can buy an expansion card for more SATA.
— eSATA - connects external case filled w/ SATA drives - has it’s own specific eSATA connector
	- exam tip: on the exam, but eSATA has “taken a back seat” bc of great advances in USB
	- eSATA expansion card - allows for eSATA on more modern motherboards w/o built in

— Boot into System Setup (Boot) to confirm correct physical connection
— We use the u.c. Attachment protocol to communicate with hard disk drives


Solid State Drives:
— most popular - traditionally a lot faster - typically used as boot system
— orgainzed into multiple chips that are organized into “pages” (each chip may have hundreds or thousands of pages) - within a page itself, we get to the smallest unit of storage:
— Block
— common sizes: 2 1/2” SSD, 3.5”, and M.2 SSD
— interfaces: 1st Gen SSDs use the same HDD SATA interface
	- SSDs are much faster than HDDs
	- Non-Volatile Memory Express (NVMe) - much faster interface than SATA
		- system itself takes the job of the hard drive controller / LBA stuff
		- not even really an interface between the CPU and the mass storage
		- traditionally found in M.2 (1 notch vs 2)
		** must make sure motherboard has connectors you want (M.2 connector)
		- uses PCIe lanes. is the fastest. PATA is the slowest. SATA & SCSI fall between

— Again, check System Setup to confirm correct connection.


SCSI:
(obj 3.1 Explain basic cable types, features, and their purposes)
— Old types of mass storage:
— released around the same time. competing languages (incompatable)
— Parallel ATA - ribbon cable - 2-4 harddrives in a system
— Small Computer Systems Interface (iSCSI - “skuzzy”) - wider ribbon - sometimes 7, sometimes 15 drives in a system. - Two modern SCSI standards:
	- Serial Attached SCSI (SAS) - similar to SATA, though not entirely compatable
	- ISCSI - SCSI devices connected via ethernet cable
	- typically only found in server situations now

— exam tip: terms will be on exam (SAS, SCSI, etc)


Boot Order:
(obj 3.5)
— Use System Setup to define boot order (Boot)
— With USB thumb drive, optical media drive, 2.5” SSD, M.2 SSD, and an HDD, want to make sure that the system boots from the correct boot device (e.g. want to load linux from thumb drive if plugged in first)
— UEFI mode vs legacy mode (firmware interfaces)


____________________________________________
Chapter 9: Implementing Mass Storage

New Installation - First Drive:
(obj 3.4)
— Partitioning and formatting tool built in to the OS install program
— Partitioning and formatting must happen whenever using a new drive
— These partitioning and formatting tools provide a subset of tools when compared with their main tools.
— Installation tools may provide features not normally seen anywhere else (such as swap file creation)


RAID:
— Redundant Array of Inexpensive Disks (RAID) - chaining drives together
	- good for: speed and data redundancy

— RAID 0 (striping) - requires absolute minimum of two drives
	- files save in pieces alternating between drives
	- advantage: speed
	- downside: no data safety - if either drive dies, lose everything
— RAID 1 (mirroring) - two drives (can also be four)
	- files save in pieces, but completely on both drives 
	- advantage: redundancy - data safety
	- disadvantage: slow - saving complete data twice
— RAID 5 (striping with parity) - minimum of 3 drives (more if desired)
	- files save in pieces on the first two, then through “interesting binary math” create a parity file that is the same size as the individual pieces combined, and if either drive dies, can reverse the math and recreate the data.
	- downside: can only lose exactly 1 drive - losing more and won’t be able to rebuild data
	- advantages: pretty good speed & good redundancy of data
— RAID 6 - minimum of four drives
	- file saves in pieces in the first 2, creates a parity of the 2 pieces that saves on other 2 drives
	- more expensive “in terms of real estate”
	- advantage: more redundancy - you can lose up to 2 drives

— RAID 10 (striping mirrors) - minimum of 4 drives (technically 2 pairs)
	- 2 mirrored pairs that take alternating pieces of files
	- advantage: can lose 1 of the mirrored pairs on each side
	- downside: if lost a complete mirrored pair, lost half of stripe and data lost
— RAID 0+1 (raiding stripes) - minimum of 2 pairs (4 drives)
	- stripe on first pair, then mirror on the other pair
	- advantage: can lose one complete striped pair on either side
	- downside: losing one on each side, cannot rebuild the mirror; data lost

— Can do through hardware - dedicated controllers built into motherboard or card you can snap in - configurable through System Setup or an optional BIOS - once set up into an “array” the OS will see it as a single large “D drive or something” — or through software (usually the OS itself).

— Proprietary RAIDs - sold systems that aren’t advertised as a particular RAID number, but work out of the box


Hardware RAID:
— most top motherboards these days have built in RAID controllers sodered to it
— System Setup (Storage) to go from AHCI —> RAID
— On reboot a new option (“CTRL-R”) to go into new System Setup (BIOS) screen to configure array
— Initialize Disk(s); choose which to use for array; choose RAID number desired; wait for set up; continue to boot
— (The RAID controller on this motherboard is limited to creating 2-TB RAID arrays)
— Hot spare / swappable drive - option sometimes to have a blank drive waiting to rebuild your array automatically if one hard drive fails.
— “Hot swappable” means you don’t have to shut the system down to remove a hard drive and plug it back in. (Unfortunately on this system it can’t be done. We can make a spare, but in order to make it hot swappable would need to use/get a more advanced controller than is built in.)

— Again, the completed array looks like a single drive to the operating system


Mass Storage Troubleshooting:
(obj 5.3 Given a scenario, troubleshoot hard drives and RAID arrays)
— Rule 1: Back it up
— Rule 2: Mental reinstall - think about the process of reinstalling it from the ground up and you will likely remember the step that you missed
— Rule 3: Triple check - most problems with mass storage aren’t from them breaking, but from us, as technicians, missing a step.

— Raid not found / Raid not working
	- if not found, first assumption is it hasn’t been installed before, check:
		- is the RAID controller active?
		- do I have the right drivers for this particular system?
		- is there a System Setup to get to the RAID array through hardware and checked?
		- connected properly? have power?
	- if not working, means it was installed and working, but now not, check:
		- does hard drive have power? is it plugged in?
		- did somebody erase something you weren’t anticipating?

single drive problems:
— Read/write failure - all hard drives have a certain lifespan and near the end they manifest certain problems, and this is a big one. 
	- S.M.A.R.T. - tool built into drives that can be used to querey a drive as to it’s health
— Slow performance - mass storage last place to look when dealing with this issue (vs not enough RAM, going into virtual memory and getting a “disk thrash”) flickering read/write light; nothing wrong with mass storage, need more RAM…
— Loud clicking - mass storage failed - replace the hard drive
— Failure to boot - typically a thumb drive in place and boot order messed up (check WinRe for boot failures)
— Drive not recognized - formatting problem - assuming no precious data on disk, try reformatting the drive. This error atypical for drives that have been functioning properly - if moving disk from one Windows to another, must initialize the disk before Windows will recognize it.
— OS not found - 99.99% of time messed up boot process
— Attempts to boot to incorrect device - definitely a boot order problem
— Continuous Reboots - not typically a mass storage error (in his experience) - sometimes a corruption in the operating system and it can’t boot properly

— exam tip: Comptia notorious for verbose exam questions, when really the actual question is a tiny sentance within the paragraph. Take your time.


_____________________________________________
Chapter 10: Essential Peripherals

Optical Media:
(obj 3.4)
— been around since 1980
— CDs, DVDs, and Blu-rays
— Compact Disc (CD) - originally designed for music - microscopic pits read by a laser allows to store a ton of 1s and 0s in a tiny space. 74 min & 80 min capacities
— CD-ROM (compact disc/read-only memory) - allows to store data (file system = ISO-9660, “which we don’t care about”) in the CD File System (CDFS) (650-700MB capacity)
— CD-R (CD-recordable) - allows a “burn” - not erasable, but was popular for things like backups
	- speed, capacity in MB & minutes (650-700MB capacity)
— CD-RW (CD-rewritable) - allows burn & erase (650-700MB capacity)

— DVD (digital video disc) - originally designed for movies, but DVD today stands for “digital versatile disc”.
	- Dual-layer (DL) format - two lasers reading different layers
	- Double-sided (DS) format - silver on both sides
— DVD capacities:
	- DVD-5 (12cm, SS/SL) - 4.37 GB, more than 2 hrs of video
	- DVD-9 (12cm, SS/DL) - 7.95 GB, about 4 hrs of video
	- DVD-10 (12cm, DS/SL) - 8.74 GB, about 4.5 hrs of video
	- DVD-18 (12cm, DS/DL) - 15.90 GB, more than 8 hrs of video
— DVD-ROM (DVD/read-only memory) - mastered form of DVD - most common type of optical media today
— DVD+R - burn once; DVD-R; DVD+RW; DVD-RW
	** was a problem when needing a drive that supports specific, but today all are standard

— Blu-ray Disc - highest capacity read-writable format - designed for High Def movies (BD-ROM, BD-DS/SS, DL/SL, BD-RE (Blu-ray Disc Recordable Erasable))
	- capacities:
		- standard disc - 12cm, SL = 25 GB; DL = 50 GB
		- Mini disc - 8cm, SL = 7.8 GB; DL = 15.6 GB

— Uses SATA cable (is an ATA device)
— hole available to use a paperclip to remove a disc when no power connected
— All optical media comes in read-only memory (ROM), write-once (R), and write-many (RW/RE) versions.


USB Standards:
(obj 3.1)
— USB (Universal Serial Bus) - the de facto standard for plugging in peripherals

— USB 1.1 (1.5 Mbps and 12 Mbps)
— USB 2.0 (480 Mbps) - fast enough for file transfer to/from thumb drives
— USB 3.0 (5 Gbps) - compatability issues
— USB 3.1 Gen 1 (5 Gbps) - fix from 3.0
— USB 3.1 Gen 2 (10 Gbps) - current top speed
** cannot stress how important these speeds are for the exam!
** Mbps = Megabits/sec; Gbps = Gigabits/sec

most common types of USB connectors:
— USB Type-A connector - “famous, original”
— USB Type-B connector - plug into devices (scanners, etc)
— USB mini-B - plug into smaller devices (cameras, etc) (butterfly shape)
— USB micro-B - popular in things like Android phones
— USB 3.0 micro-B - has a notch, longer, backward compatable port
— USB Type-C - reversable design - capable of incredibly high-speed data throughput
** need to recognize by picture on exam

typical port colors (for USB-A):
— USB 1.1 - white
— USB 2.0 - black
— USB 3.0 or 3.1 Gen 1 - blue
— USB 3.1 - teal (green)
— Charging ports - red, organge, yellow

— USB is backward compatable - runs at the speed of the port
— Each version of USB in a computer has its own USB controller, which is then connected to a USB hub. 


Understanding USB:
— USB controller - built into motherboard
— commands going downstream - controller is sending commands to device
— A connectors (downstream)
— B connectors (upstream) - sodered on a mouse, but think the port on a TI calculator
	- USB-micro and USB-mini are all B connectors
— With USB Type-C, the upstream/downstream concept is eliminated

— Controllers plugged into a single “Root Hub” (1.1, 2.0, 3.1)- typically all blue as the 3.1 connector is available from any port
— Multiple controllers (1.1 and 3.1) with different Root Hubs for each - black for 1.1 & blue for 3.1
	- with an external hub can have up to 127 devices on one 3.1 Root Hub.
	- powered hubs available to provide AC power so the single port isn’t providing for all devices

— Can see controllers and Root Hubs via OS


Configuring USB:
— USB pretty much works in any operating system
— You need to install a device driver for whatever is being plugged in
— Typically automatically installed (Device Manager - Windows)
— rule used to be: install driver, then plug in device
— If error - check online for driver 
— “signed drivers” - signed by microsoft to say “I’m not carrying malware”
— HID (human interface device) - core device drivers exist so that keyboard+mouse always work
— USB can be a big security issue - keyloggers
	- can Disable USB ports by port or entirely
	- USB lock - software to watch ports to report, whitelist certain devices


Thunder and Lightning:
— Thunderbolt - PCIe and DisplayPort combined into one port.
— Drive x6 monitors, charge, data transfer
— Thunderbolt 1 - 10 Gbits/s (x2 channels = 20 Gbits/s) (mini DisplayPort)
— Thunderbolt 2 - 20 Gbits/s (mini DisplayPort)
— Thunderbolt 3 - 40 Gbits/s (USB Type-C - not the same, but a lot of compatability)

— Lightning - exclusive to Apple (proprietary)
— Charging, data transfer (familiar port if using iOS)
— Becoming more common to see Thunderbolt (USB-C) on Macs
— Downside vs Thunderbolt: 30 Gbits/s
** (Gbits = Gigabits)


Keyboards and Mice:
(obj 3.6 Explain the purpose and uses of various peripheral types)
— USB 1.1 or wireless (w/ USB dongle)
— PS/2 connector - predates USB; becoming more popular w/ gamers for decreased latency
	- purple = keyboard; green = mouse
	- downside: must plug in/out when shut down
— Whatever connection, need some configurations
	- (Control Panel —> Windows Settings)
	** be careful on exam w/ where supposed to go. “think control panel for the exam itself”

— Game controllers - often come w/ propriatory connector + dongle —> USB
— KVM switch (for keyboard, video, and mouse) - designed to allow input devices and a monitor to share between multiple physical computers. Press buttons to switch between individual computers.


Sight and Sound:
— Speakers - at a minimum stereo (x2 speakers)
— 2.1 speaker system - 2 speakers + 1 subwoofer (up to 4.1, 5.1, 7.1)
— color coded: blue = aux line in; green= front 2 stereo; pink = microphone; silver = side speakers (2); black= rear speakers; orange = subwoofer / center channel (for dialog, etc)
— better quality sound can be had with different sound cards
— S/PDIF (Sony/Philips Digital Interface) - optical audio connector - computer -> speaker system
— Headsets - USB connector; w or w/out microphone
— Webcams

— “Open Sound settings”
— Biggest problem w/ sound people run into: speakers - need power, turned on, volume
	- volume: applications, OS, and speakers have individual settings
	- checking this before device drivers, etc

— Sound uses 3.5mm jacks or SPDIF


Readers and Scanners:
— Smart cards -  stores credentials that help authenticate to whatever (e.g. RFID on credit card / credentials for typing passcodes, buying gas, etc.)
	- In high security situations can be used on computers
— Magnetic reader - “swipe” on credit card
— Flash memory reader - SD cards, mini-SD, micro-SD - no difference other than physical size
	- Olympus xD Picture Card - used in Olympus brand cameras (**on exam)
— plug it in and treat 

— Scanners - scans physical documents
	- Flatbed scanner - one page at a time
	- ADF (Automatic document feeder) - 

— Barcode / QR code scanners - printed black&white; store numeric or alphanumeric information
	- used for inventory
	- all smart phones have apps that allow to read Bar/QR codes


Using Expansion Cards:
(obj 3.5)
** Exam discusses types of add-on cards that you need to know how to put into computer
— sound cards, network interface cards, USB expansion cards, eSATA cards, extra PCIe expansion slots, etc.
— usually identical steps - follow manual, install drivers (comes w/ optical media, but may not need to use), check device manager, install additional application software if necessary
— choose placement based on not impeding airflow and connections you might need (power/SATA)
— can have compatibility issues - a new device installation is a common place for Blue Screen of Death screens.

________________________________________________
Chapter 11: Building a PC

The Right PC for the Job:
(obj 3.8 Select and configure appropriate components for a custom PC)
— Thick Client - standard/basic office computer
— Meets recommended requirements for selected OS
	- middle of the road motherboard + matching CPU
	- his selected had onboard graphics
	- Desktop applications - Microsoft Office (or alternatives)

— Thin Client - similar to thick, but rarely counts on internal storage
	- Network connectivity - select motherboard based on this (Gigabit)
	** for the exam: same “meets min req” as above
	- for him: go beyond
	- Basic applications - Word or specialized in house applications

— Graphic/CAD/CAM Design Workstation - more powerful systems
	- good, powerful, Multicore processor (CPU) (he used i9)
	- High-end video (GPU)
	- Maximum RAM

— Virtualization Workstation - 
	- Maximum RAM and CPU cores
		- each VM needs RAM for its OS + RAM for the jobs that it performs
	- high-end motherboard & CPU
	- comptia doesn’t say, but he adds: storage
		- virtual machines take up a lot of space - uses extra HDDs to store VMs when not using

— NAS - network attached storage
	- usually a “headless system” (no mouse/keyboard attached after everything is running)
	- File sharing - media streaming, traditional files via NTFS permissions
	- Gigabit NIC - good, high speed network card
	- RAID array - to protect data (+ lots of storage)
	- good midrange motherboard & CPU

— Gaming PC
	- Multicore Processor + motherboard that supports it
	- high-end power supply
	- High-end cooling
	- High-end video/specialized GPU - (features like SLI allows x2 GPUs to 1 monitor)
	- High-definition sound card
	- storage: SSDs + disk drives to hold games

— Audio & Video Editing Workstation 
	- Specialized audio and video card
	- Large, fast hard drive
	- Dual monitors
	- “If you want to make your life easier in these types of situations just get a Mac”

— Memorize details about each specialized system
— Consider different jobs and make sure the system matches the job specifications
— Concentrate on RAM, storage, and graphic needs.

_______________________________________________________
Chapter 17: Display Technologies

Monitor Technologies:
(obj 3.6)
— Pixel (picture element) - individual pieces that emit RGB light values
— Liquid Crystal Display (LCD) - electricity allows light to pass through, but requires backlight via:
	- Cold cathode flourescent lamp (CCFL) - old
	- Light-emitting diodes (LEDs) - now, vast majority
— Different combinations of RGB values can produce any color (e.g. no electricity in R or B = G light)

different panels for LCD:
— Twisted nematic (TN) - benefit = inexpensive + speed
— In-plane switching (IPS) - benefit = wide range of view

— Resolution - number of pixels across & down (e.g. 1920x1080)
— Brightness - Nit (nt) - measure of light
	- Panels generally run from 200-500 nits
— Response time - panel needs to be able to reset itself to keep persistance of vision\	- (used to be called “refresh rate”, but passe now)
	- Panel response times run from about 1ms-4ms

— LCD backlights are flourescent or LED lights and shine through liquid crystals
— LEDs are a method of backlighting in monitors. 

— Organic LED (OLED) - each RGB is a lightbulb vs having a backlight
	- benefits = thin monitors; flexible monitors
	- found in smart phones and tablets
— Digital Light Processing (DLP) - rather than individual pixels, grid of tiny mirrors
	- grid defines the resolution
	- color wheel spins out RGB color 
	- rare for monitors, popular for projectors


LCD Breakdown:
— millions of tiny wires feed into LCD screen
— an LCD panel has a preset resolution

— CCFL tubes - behind white reflector that keeps light as even as possible
	- standard AC->DC power supply
	- Flourecent bulbs require AC power, convert DC back to AC with inverters
	- Only CCFL screens need inverters - LEDs don’t need inverters

— 1. Panel
— 2. Backlight unit
— 3. Connectors
— 4. Input from data
— 5. Power connection


Graphics Cards and Connections:
(obj 3.1)
— Graphics processing unit (GPU) AKA - video card
— Frame buffering - using some type of RAM to keep track of what is in every single pixel electronically, and then pushing that out to the monitor
— now, GPU processes this “put a circle here” or “here’s an icon that gets used a lot, keep that in your memory” - scanning back and forth rapidly (hopefully a minimum of 60 times/s) and resetting monitor to the new image (not uncommon to have 8 GB of RAM on the chip itself)
	- All graphics cards have RAM to help resolve the screen
— Nvidia and ATI/AMD (and Intel - designed to work more on motherboard itself) make the majority
— Integrated (build-in) GPU - on CPU
	- CPU + GPU = APU! (**not on exam)

different types of connections:
— VGA (Video Graphics Array) - “granddaddy of them all” - 15-pins on 3 rows - almost always blue
	- problem: an analog system - monitor will have to convert to digital and then update pixels
	- wasted step
— Digital Visual Interface (DVI) - first digital connector
	- DVI-I (digital and analog) - has ability to transmit analog signal (..+..)
		- can still use video card w/ old analog monitors w/ an adapter (DVI to VGA)
	-  DVI-D (digital only) - (“—“ on right only)
	- Single-link DVI - (space btwn pins)
	- Dual-link DVI - run 2 monitors from 1 DVI link, or now, run large, high resolution monitors
		- (no space btwn pins)
	- both single and dual on DVI-I and DVI-D
	- problem w/ DVI: still have to go through configurations to make it work
— HDMI (High-Definition Multimedia Interface) - video and sound
	- supports Digital Rights Management (DRM)
	- Mini-HDMI
	- automatic configuration
— DisplayPort - some want a dedicated connector for video
	- popular, competitor to HDMI
	- Mini DisplayPort
— Graphics cards will have a variety of ports for flexability or multiple monitors
	- often have a default port - try to use this one first


Installing a Graphics Card:
(obj 3.5)
— Almost all graphics cards use 16-lane PCIe slots and one or two PCIe power connectors
	- 8-pin PCIe power
	- PCIe ports are numbered
— CMOS allows selection of graphic card to boot from (if on-board graphics IGFX or multiple)
— Riser card - plugs into main expansion bus and allows to add additional graphics cards
— Device Manager - to ensure graphics card
— Settings -> Display - check running in native resolution; adjust text scale
— Update drivers - through Windows or manufacturers site


Projectors:
(obj 3.6)
— Projectors have resolutions and aspect ratios like monitors
— technology: DLP and LCD (bulbs last a long time)
— Lumens - define brightness (small/dark area=1000-1200 lumens; bright area=2500+ lumens)
— Throw - further out you project the larger it gets, closer smaller
	- a lot have ability to adjust the screen size
	- replacable lenses to adjust throw dramatically
— geometric adjustments:
	- Pincushion - concave/convex edges
	- Keystone - slanted edges (trapeziod-esque) - projecting from high or low
	- Skew - tilted keystone


Troubleshooting Monitors:
(obj 5.4 - Given a scenario, troubleshoot video, projector, and display issues)
— Overhead shutdown - video card gets hot and shuts down - could be bad fans on videocard or packed in too tight and not enough ventilation.
— Dead pixels - just happens on LCD monitors - certain allowance by manufacturers - towards center of screen, don’t have to deal with, return/exchange w/ manufacturer/store - can’t fix
— Artifacts - pieces of previous images stays on screen - video RAM goes bad - test w/ a different card - sodered on, no replacement
— Incorrect color patterns - check cable (especially VGA) - check video RAM
— DIM image - not enough light production from somewhere - problem on older CCFL panels - replaceable (Ebay) - make sure brightness is turned up
— Flickering image - check cable (HDMI especially)
— Distorted image - make sure running native resolution of monitor - w/ projectors adjust geometry
— Burn in - can happen with plasma monitors - not often w/ LCD (called Image persistence) - change the screen to something different and will go away on it’s own pretty quickly
— Oversized Images and Icons - on Windows, ability to adjust text size

** The exams cover many monitor troubleshooting situations. Take time to memorize them.


__________________________________________________
Chapter 18: Essentials of Networking

Introduction to Networking:
(obj 2.7 - Compare and contrast Internet connection types, network types, and their features)
— Local area network (LAN) - run wires to a central box (Hub)
	- WAP (wireless access point)
— Ethernet - wire that connects LAN computers
	- Frame - chunk of 1500 bytes max (standard)
— Media access control (MAC) address - 48 bit address always manifested as 12 hexidecimal characters (e.g. 00-14-22-01-23-45) - every network card gets a unique one - uniquely identifies every system on the LAN
	- OEM ID - first 6 characters - issued to manufacturer by the issuing body of the internet
	- ifconfig (or if) - command on mac/linux to view; ipconfig /all - command on windows
	- every time sending data giving - destination MAC, source MAC, the data, and
		- FCS (frame check sequence) - ensures data comes in correct order
— IP address - another identifier - not much value on LAN (useful in wide area networks)

— Ethernet frame: In order, destination MAC address, source MAC address, data payload, FCS

Hubs vs Switches:
(obj 2.2 - Compare and contrast common networking hardware devices)
— Hub - a “repeater” - makes a new copy of the Frame sent from a computer on the LAN - every computer gets a copy of what is being sent from D to A — B & C will see destination MAC address and erase the frame bc not for them
	- considering a maximum throughput of 10 Mb/s - if A & B and C & D are communicating, they are sharing the throughput (5 Mb/s each) - more computers, slows down conversation
— Switch - a “smart repeater” 
	- box collects MAC addresses of connected devices (automatically, not needed to configure)
	- switch looks at destination MAC of frame as it comes in, and creates direct links btwn
	- A & B and B & C can now each have 10 Mb/s conversations
	- (provides full bandwith for all nodes)


Hexadecimal:
— Computer world full of binary - wires or storage areas going on and off - so 1s and 0s is the normal way that computers speak
— 32- or 64-bit CPUs; 8-bit external data busses; 16-bit registers; 256-bit memory in graphics cards
— Important thing all of these different chunks of 1s and 0s have: a least common denominator of 4
— Hexadecimal - nomenclature using complete base 16 numbering system + a-f to shorthand binary
— every possible combination for a string with 4 binary values 0000-1111 (all off - all on) = 16 total
	- 0000 = 0h
	- 0001 = 1h
	- 0010 = 3h
	- 0011 = 4h
	- 0101 = 5h
	- 0110 = 6h
	- 0111 = 7h
	- 1000 = 8h
	- 1001 = 9h
	- 1010 = Ah (vs 10h - which could be assumed as 00010000)
	- 1011 = Bh
	- 1100 = Ch
	- 1101 = Dh
	- 1110 = Eh
	- 1111 = Fh
— e.g 11011101 = DDh
— Goal is to prevent having to write in long strings of 1s and 0s by compressing a lot to smaller values
— Every hexadecimal value = 4 binary values
	- e.g. Physical Address (MAC address) of 40-8D-5C-1C-5A-50 = 12 chars = 48-bit address


WANs and Routers:
(obj 2.7)
— Ethernet - standard says no more than 1024 physical computers on a single / daisy chained switch(es) - (in reality 30-40 computers is the standard max size for a LAN)
— Wide area network (WAN) - hundreds, thousands, potentially millions of little LANs interconnected together
— Router - magic box (looks like a switch) - can differentiate btwn different computers and LANs
— Logical addressing - addressing system to connect multiple LANs
	- vs MAC address being a physical address (“burned in a the factory”)
	- remembered by the router
	- IP addressing - type of logical addressing used
	- Every device on network gets a unique address
		- (e.g. IP=192.168.4.100,
		- phone = 192.168.4.22
		- computer = 192.168.4.15
		- alexa = 192.168.4.6
		- router = 192.168.4.1 - common to give the “.1” - router + switch typically built-in)
— If any 2 computers want to talk to eachother, they don’t even really use the IP address, just use their MAC addresses - however, to talk to anybody that doesn’t have an address that starts with 192.168.4 (in this case) they have to send it out to the router (called the default gateway).
	- Routers use logical addressing (IP addressing) to determine local vs. remote traffic
— Cable modem connection - has another LAN being handled by the cable provider
— DHCP - special type of server built into router that automatically gives connected devices this information to make life easy


Cables and Connectors:
(obj 3.1)
— Predominant networking is called ethernet - defines our frames, how the network cards work, and the type of cabling and connectors we use.
— DOCSIS (used for cable modems)

— as different ethernet standards release, they need improvements in cabling in order to make sure that they run at the speeds they are capable of - different versions of ethernet:
	- 10BaseT (10 Mbps baseband twisted pair) 
	- 1000BaseT
	- 10Gb base T (10 gigabit per second)
	- different types may be copper, fiberoptic (** which are which not on exam)

— Coaxial cable - connectors are axial - big center piece, insulator, and an outer cladding that is a signal tool as well.
	- RG ratings:
		- RG-58 (old - thin cable - was used in networking)
			- BNC connector - not threaded; push in and twist to make connection
		- RG-59 & RG-6 - used often for video and networking uses
			- F-type connectors - used here (familiar use on cable TV)

— Twisted pair - predominant type of cable used today
	- twisted pairs helps propagate the signal better (4 pairs in his example)
	- if not twisted together, the distance able to run individual cables would be much shorter
	- Unshielded twisted pair (UTP) - no metalic foil inside
		- in general, run about 100 m
		- RJ-11 - connector type used in telephone cable (4 contacts)
		- RJ-45 - 4 twisted pairs (8 contacts)
	- Shielded twisted pair (STP) - still an RJ-45
		- metal on connector and through cable provides robust protection
		- motors and fluorescent lights make UTP not work well
		- STP can be a lot closer to these types of interference and work fine
	- CAT ratings:
		- CAT 5 - 100 Mbps
		- CAT 5e - 1 Gbps
		- CAT 6 - 1 Gbps (up to 100 m) & 10 Gbps (up to 55 m)
		- CAT 6a - 10 Gbps (at 100 m segments)
		** will be on exam

— Fiber optic (fiber) cable - uses light vs electricity
	- popular in 10+ Gigabit ethernet situations
	- kevlar
	- cladding w/ hair thin piece of fiberglass that propagates a light signal
	- Multimode - uses LED to propagate the signal
	- Singlemode - uses lasers to propagate over many many Km of distance

** for exam: make sure you can recognize different connectors by picture

— Plenum ratings - based on ability of the plastic cable casings to resist fire
	- PVC (non-plenum) - cheap, most burnable
	- Plenum rating - fire resistant
	- Riser rating - intermediate rating - used running cables between floors - not as resistant
	- (plenum = area between actual and drop ceiling / raised floor where cables run)
	** check local building codes for which to use (probably plenum)

— different manufacturers may use their own CAT rating system (e.g. “Category 6e+”) - have to check with manufacturer on which known rating it ties to 


Crimping Cables:
— Crimps - connector end - has it’s own CAT rating - must make sure to match w/ what you need
— cable crimper and cutter - tool used
	- particular area to cut entirely through or just the jacket away
	- particular area to crimp RJ-45 or RJ-11

— cut off ~1in of jacket, move away kevlar
— untwist and flatten them out (into “broom shape”)
— (on RJ-11) notice colors on 4 twisted pairs: orange, blue, green, and brown
	- each colored pair has a white-striped cable and a solid color one
	- TIA 568A / TIA 568B - standards to define where to put the colors
	- with little tab on crimp upside-down, starting on right (looking at head on) = pin 1-8
	- T568A vs T568B
		- 4 wires go in exact same place (blue & brown - “if it starts w/ a B”
		- position 8 = Brown
		- position 7 = Brown/White
		- position 4 = Blue
		- position 5 = Blue/White
		- “A” stands for “alphabetical” in T568A:
			- position 1 = Green/White
			- position 2 = Green
			- position 3 = Orange/White
			- position 6 = Orange
		- T568B - swap orange and green:
			- position 1 = Orange/White
			- position 2 = Orange
			- position 3 = Green/White
			- position 6 = Green
** In order to stay within any CAT rating, the distance from the last twist to where you actually punch down into the crimp must be 1/2” - maybe cut down wires a bit more w/ scissors to do so
— use crimper tool (ensuring correct orientation)
— use cable checker to check for - continuity (connected from one end to the other) and wire mapping (correct colors between correct pins)
	- Straight-through cable - term for when wired properly (same on both sides)
	- Crossover cable - when wired T568A on one side and T568B on the other
		- handy for connecting 2 computers directly together (depends on network card if can)


Structured Cabling:
(obj 3.1)
— Structured cabling - cables organized in walls vs strung across floor - a hazard to people and data
— Main Distribution Frame (MDF) - room/closet where the equipment is
	- equipment racks are standard 19” (across)
	- “u” - standard for height distance
	- Horizontal run - runs from different wall outlets throughout your LAN to the back of a…
	- Patch panel 
	** patch cables have a boot - an extra piece of rubber at the crimp
— one horizontal run = patch cable from switch -> patch panel; patch cable from patch panel -> walls/ceiling -> wall outlet; cable from outlet -> computer
— According to TIA rules - the longest run you can have in a horizontal run is 90 m (vs ethernet allowing 100 m runs in almost all situations)
	- compensates for the length of the individual patch cables themselves (up to 10 m)

— 110 punchdown tool - used to connect cables to the back of the patch panel
	- make sure the longer tip is always on the outside (tip cuts excess wiring after placing)
	- place according to diagram on back of the patch panel (T568A or T568B)
	- use cable tester to determine if made a good connection
		- good testers come w/ a remote allowing 1 connection into patch panel and at wall
		- helps w/ long runs (through walls, etc)
		- perform same continuity and wire mapping tests
	- Fox (tone generator) and hound (tone probe) - tool used to locate cables
		- allows different sounds to track a “homeless” cable
	- Time Domain Reflectometer (TDR) - uses speed of light to determine how long a cable is
		- e.g. if a 40 m run from patch panel -> wall outlet and reads 20 m = break somewhere

2 types of twisted pair:
— Solid core - put into the walls themselves - each of 8 wires is a solid piece of copper
	- carries electricity really well; often used
— Stranded - used for the patch cables - each of 8 wires is stranded
	- not as good/fast, but flexible - won’t break
** will be on exam


__________________________________________________
Chapter 19: Local Area Networking

Introduction to TCP/IP:
(obj 2.6 - Explain common network configuration concepts)
— sample IP address: 192.168.5.10 - 4 digits separated by 3 dots - addresses to allow us to get information from any computer on the internet
	- given to you by the Internet Authorized Numbering Authority (IANA)
	- TCP/IP adopted as protocol for ARPANET/the internet

origins of the internet:
— thousands of individual local area networks (military bases, universities) with the idea to connect them so any LAN can communicate with another LAN
— connected originally by telephone poles by ARPANET (ARPA today)
	- create multiple connections to each individual node acting to help other nodes
	- if any nodes went down, we could reroute the information and still get to where needed
	- need a numbering system to organize them
— 10.11.12.13
	- each of 4 values called an octet can go from 0-255
	- all total combinations = 4 billion addresses
	- each computer needs it’s own address to:
		- 1. Identify which LAN you are a part of
		- 2. Give you a unique host ID

— TIER 1 of the internet 
	- Rice University = 12 (arbitrarily)
	- University of Houston = 12.1 (get own router vs “connecting to the top part”)
		- Parallel Processing Center 12.1.44
		- College of Engineering = 12.1.27
		- College of the Arts = 12.1.28
		- (all seperate local area networks)
			- individual computers = 12.1.28.1 (up to .254)
	- idea was called “aggregation” 

— Class C - 210.11.12.x (first numbers locked, anything going in x) - 254 hosts
— Class B - 172.16.x.x - 65,534 hosts
— Class A - 6.x.x.x - Millions of hosts

— IP Addressing built with the idea that you’ll always be no more than 4 routers away from the top of the internet - big mistake
— Total address space of the IP addressing = ~4 Billion IP addresses
	- limitations/wasted - e.g. 1. = “experimental” (no one could use) or can’t use 255
	- nowhere near enough 

** exam tip: watch out for “which one of these is valid” - not the one with 257 in it
	- addresses never end with a 0 or 255
	- one reason can’t put a 0 on the end is that it identifies an entire LAN (e.g. 10.11.12.0)

— Now: destination MAC, source MAC, destination IP, source IP, data, PCS
	- allows us to jump from LAN to LAN
— Subnet mask - allows computer to see if local or long distance call
	- e.g. 255.255.255.0 - wherever a 255, numbers must match
	- 225 means the octet is part of the network address
	- by comparing the destination to own IP address, computer knows if the other address is within it’s local area network - that way it can just put on the proper MAC addresses and send directly to the other computer (“it’s a local call, as we say”)
— when found to not be in the same LAN, computer sends to router (e.g. 10.11.12.44 -> 10.11.12.1)

If you want a computer to be on the internet:
— 1. Give it an IP address
— 2. Give it a subnet mask
— 3. Give it a default gateway (router)


Network IDs and Subnet Masks:
— Network and Sharing Center (through control panel or “Network Connections”)
—> “Change adapter settings” - shows network cards
	- right click and select “Properties”
	** note: different than if you right clicked on same network card in Device Manager
	- interested in setting for “Internet Protocol 4 (TCP/IPv4)”
		- (IPv4 = early IP type that built the internet, new = IPv6)
		- IPv4 addresses are 32-bits long
		- click “Properties” - where you type in your address
			- overwhelming number of subnet masks will be Type C 255.255.255.0
— Static IP address - when manually typing in the IP address, subnet mask, and default gateway
	- not “out of thin air” - came from administrator / someone configuring the network


Special IP Addresses:

“looking at classes with an old fashioned bend” (not in CompTIA):
— Class A addresses go from 1.0.0.0-126.0.0.0
— Class B addresses go from 128.X.0.0-191.X.0.0 (X’s are assigned)
— Class C addresses go from 192.X.X.0-223.X.X.0
— If you have subnet mask 255.0.0.0, meaning you can do whatever you want with the other 3 - no one cares what the first number is anymore

— Class D address - 224.X.X.X
— Class E address - 240.X.X.X
— Class D-multicast - used in presentation stuff - e.g. someone doing a video presentation live and a bunch of other want to watch are temporarily given a second IP address that starts w/ 224 (for the duration of the video and then erased)
— Class E-Reserved - nobody ever touches it

— Private IP address - not connected to the big internet, but like the TCP/IP protocol
	- Class A - 10.X.X.X
	- Class B - 172.16.X.X-172.31.X.X (put anything you want for X’s)
	- Class C - 192.168.X.X (given first X, whatever you want for second)
	- used within private networks, if a router part of the real internet itself sees, will erase packets

— Loopback IP Address - 127.0.0.1 - refers to your own system
	- used to be a handy way to test your computer
	- ping 127.0.0.1 - “ping” command sends a Ping packet, a single ping, to an IP address
	- pinging yourself allows you to make sure that your network card is working
	- ipconfig - command that allows you to see your own IP address (for Windows)
	- ifconfig or ip (same thing for Mac/Linux)
	- if you can ping something, you should be able to communicate with it
	- ipconfig /all - shows more (incl MAC address)
	- ping -t router_address - keeps pinging (on Windows)
	- on Mac/Linux - ping repeatedly by default - use flags to stop this


NAT:
(obj 2.3 Compare and contrast wireless security protocols and authentication)

Originally:
— a default gateway was assigned an IP address by an ISP, the internal address (of your LAN) would be assigned it’s own unique address, and then you manually go in and set up every device with it’s own individual final octet.
— “Back in the glory days when there were lots of IP addresses” when you called your ISP, you would probably be given a Class C address - were given a box and piece of paper and have to manually assign addresses.
— Downside: All devices in your network had public, easy to find IP addresses - put firewalls on routers for security, but if got behind firewall everything on your network was visible to everything else - also eating up a lot of IP addresses with devices (wasteful)

— NAT (Network Address Translation) - allows for not everyone to need their own unique IP addresses
— Still provided an IP address for the router on the WAN side from ISP; however, all devices inside network use a private IP address (default gateway=11.12.13.14; internal network=192.168.5.0; device A=192.168.5.22; etc.) - lots of LANs can use these private IP addresses
— Computer 192.168.5.22 wants to communicate with 129.46.88.3, sending a packet, goes into the gateway router, it strips the private IP and insert it’s own WAN address (11.12.13.14), “which is a legit public IP address” — the response packet is sent back to 11.12.13.14, but the gateway router remembers that 192.168.5.22 requested the information from 129.46.88.3, strips his own IP and reinserts the private IP address
— Benefit: Don’t have to give out a ton of IP addresses; Downside: slower, and anything inside the LAN is invisible to the internet, so you can’t put web servers, etc (not that you would want to, would be a lot of work to get that data through a home router)


Dynamic IP addressing:
(obj 2.6)
— Dynamic Host Configuration Protocol (DHCP) - a DHCP server automatically assigns IP addresses, subnet mask, etc rather than manually entering (static IP addressing)
	- home router also acts as a DHCP server

— On Windows: Network Connection -> Status -> Network and Sharing Center -> Change adapter settings -> right click on network card and go into “Properties” -> Internet Protocol Version 4 (TCP/IPv4) -> “Properties” -> Obtain an IP address automatically; Obtain DNS server address automatically

—APIPA (automatic private IP addressing) - takes over if the DHCP server goes down
	- (from the same window) go to “Alternate Configuration” tab
	- APIPA will always give 169.254.X.X address (a Class B Address, where Xs are autogen)
	- when booting a computer will always first reach out for DHCP server before APIPA kicks in
	- can still access shared stuff (printers, files, etc) bc all devices have 169.254 addresses
	- but not internet bc router has fixed address (doesn’t use APIPA)
	- you can use “User Configured” to manually give yourself a non-APIPA address
		- rare to use
		- better to leave and then is known DHCP server issue if your IP address is APIPA

— troubleshooting: using ipconfig, if your IP address is an APIPA, you have a DHCP server problem
	- ipconfig /release - will disconnect you from a DHCP server
	- ipconfig /renew - will connect you to a DHCP server
— right click on network and click “Troubleshoot problems” - will disconnect and reconnect network card, does a release and a renew, and even make some queries to the internet to verify you have connectivity 


IPv6:
(obj 3.6)
— Example IPv4: 172.16.254.1 - has worked well for decades, but have run out of them (all 4 billion)
— Example IPv6: 2001:0db8:85a3:0000:0000:8a2e:0370:7334
	- a 128-bit addressing scheme, using hexadecimal notation
	- 8 groups separated by 7 colons
	- 340,282,366,920,938,463,463,374,607,431,768,211,456 addresses total!
	- “all air molecules on earth divided by 7”

— IPv6 shorthand:
	- remove all leading zeros
		- 2001:0000:0000:0001:0000:0000:0000:8a2e —> 2001:0:0:1:0:0:0:8a2e
	- compress 3 zeros in a row to two colons
		- 2001:0:0:1:0:0:0:8a2e —> 2001:0:0:1::8a2e

IPv6 requires 2 addresses:
— Link-local address - always starts with fe80:0000:0000:000:[last half auto generated by system]
	- used for local connections
— Internet address (global unicast address) - router broadcasts you the first half, and comp automatically generates the second half
	- used to connect to the Internet

— As a security feature - a computer will have one main IPv6 address, and (depending on OS) can have multiple temporary IP addresses to communicate with different servers.

** exam tip: important to be able to recognize an IPv4 vs. IPv6 address
	- IPv4 - one address and a subnet mask
	- IPv6 - prefix length fixed at /64
	- need a subnet mask to tell IPv4 if LAN vs “long distance call”
	- prefix in IPv6 is used to talk to upstream routers to get data where needed the quickest


Port Numbers:
(obj 3.1 - Compare and contrast TCP and UDP ports, protocols, and their purposes)
— in order to get information from the Internet, use some program generically called a “client” to access something generically called a “server”
— web browser is a web client - designed to be used to querey servers for information
	 - “www dot whatever dot com” is running server software (e.g. IIS or Apache)
	- waits and listens for you to make requests to it’s stored pages

— Domain Name System (DNS) - a “speed dialer” - when typing “www dot whatever dot com” it goes out and gets the actual IP address so we can actually send a request
	- data=“can we have initial webpage”, from=199.44.6.15, to=12.13.14.15
	- from=12.13.14.15, to=199.44.6.15, data= “initial webpage”

— Port Number - gets data to the right application
	- port numbers range from 0-65535
	- always going to have a source and destination IP address & port number
— 12.13.14.15 is a web server (http) listening on Port 80 (for webpage requests) and Port 445 (to share folders if a Windows file server)
	- making a request for a webpage to Port 80; Port 445 ignores
	- responds with data and swaps the To and From IP & Ports
	- each window open on your computer has it’s own port number (automatically generated)

— (On Windows) Resource Monitor - “TCP Connections” shows open ports
	- opens chrome - “this is a secure site so it uses Port 443 not Port 80”
	- “just bacause you’re opening one webpage doesn’t mean you only get a single connection”

3 types of port numbers:
— Well-known ports: 0-1023
	- applications like the web, etc
— registered ports: 1024-49151
	- applications that came out after well-know ports that want their own ports
	- (e.g. Steam games)
	- “you probably don’t want to use these port numbers either”
— Dynamic/Ephemeral: 49152-65535
	- the second port number (“remember how you always have to have 2 port numbers?”)
	- spun up by your system every time it makes a connection to give a return port number for whatever server you might be connecting to

** Common Port Numbers: (need to memorize for exam)
21-FTP
22-SSH
23-TELNET
25-SMTP
53-DNS
80-HTTP
110-POP3
161/162-SNMP
143-IMAP
334-HTTPS
3389-RDP
137-139-NETBIOS/NETBT
445-SMB/CIFS
427-SLP
548-AFD
67/68-DHCP
389-LDAP
(note: almost all of them are a well-known port)


TCP, UDP, and ICMP:
— Protocol - set of rules that allow different things to work together

— Transmission Control Protocol/Internet Protocol (TCP/IP) - two different protocols working together to get data to your systems

— TCP - connection-oriented protocol
	- as a client, talk to the server (“Hello? Hello?”; “Yes I hear you.”), and create a Handshake
	- almost all data we get on the Internet uses this protocol (webpages, Skype, etc)
	- sends multiple packets
— UDP - conectionless protocol
	- no handshake; assume that the server is ready/always on the job
	- request data outright
	- also sends multiple packets
— ICMP - single-packet only
	- e.g. ping command

— Ethernet frame - entire collection of sent/recieved data (dst+src MACs, IPs, Ports + Data, PCS)
— Protocol data unit (PDU) - organized individual parts of the packet
	 - IP packet - part of frame containing dst+src MACs & IPs + Data
	- TCP segment / UDP datagram - dst+src Ports + Data
		- used “once actually in our system”
		- can be TCP, UDP, or ICMP


Understanding DNS:
(obj 3.6)
— Domain Name System (DNS) - like a contact list for the internet
	- takes fully qualified domain names (“www dot whatever dot com”)
	- figures out what IP address is associated with that, then sends out package
— Hosts file - was the primary way to resolve names into the mid-90’s
	- used to give Internet your IP address, assign it a name
	- every morning at 3AM the host file was distributed to every computer on the Internet
	- hosts files still exist, but DNS is king

heirarchical organization of DNS to resolve FQDNs to IP addresses:
— Root Servers - control one fully qualified domain name called “.” (dot)
—First Level Domains - below root severs, hundreds of thousands of servers in charge of (e.g. “.edu”)
— Second Level Domains - below first level domains, hundreds of thousands of servers that control  (e.g. “google dot com”)
	 - all considered “authoratative”

— opening a web browser and go to “www dot whatever dot com”
	- computer auto goes to DNS server and asks “do you know the IP address for this url?”
	- has a list of all IP addresses for all of the root servers around the world
	- asks one (based on geography) “Great root server, do you know who this url is?”
	- responds “No, but here is the closest .com server” - now DNS has the IP for this .com server
	- DNS server asks “ Great .com server, do you know the IP address for this url?”
	- responds “No, but I do know who the authoritative server is for this url.”
	- DNS server asks “Great this url DNS server, do you have the IP address for this url?”
	- responds “Yes I do.”
	- hands to DNS server which hands to you
	- now you’re actually hitting this url
— cacheing - your computer and DNS server will keep a copy of the IP address for this url internally
	- Now, someone else on your DNS server will get the answer for this url quickly (held for a certain amount of time) 

— Fully qualified domain name (FQDN) - 
	- go through a registration process to register a unique name
	- once verified (and paid for) it’s yours
	- set up a DNS server (w/ web interface so you can configure it)
	- then you can add your own “www”s
	- FQDNs have a 256-character limit (including “.”s)


Working with DNS:
(obj 2.6)
— Some set up involved. DNS is provided by your DHCP server
— Use ipconfig /all is view DNS Server IP address

— Sometimes you want to statically configure your DNS:
	- Network Connections -> Network and Sharing Center -> Change adapter settings
	- right click on network card interested in - > select “Properties” -> select (TCP/IPv4)
	- can choose to set DNS statically even though your IP address comes from DHCP
		- Preffered DNS server: “using my local one bc resolving stuff w/in my LAN”
		- Alternative DNS server: 8.8.8.8
— DNS is an inperfect too (servers go up and come down) - sometimes you can’t get to a url specifically because your DNS server is the problem
	- 1. Manually configure DNS
		- choosing 2 servers (like above):
			- local
			- one of many popular public DNS servers (8.8.8.8 or 8.8.4.4)
				- these particular ones come from google
	- 2. nslookup - tool to determine if a particular DNS server is a DNS server
		- stores records
			- A record - run of the mill records (“www”, IP address)
			- MX record - used by mail servers
			- Cname - if different names for a particular IP address, you can give
		- was abused, so many years ago most DNS servers locked down queries
		- more than glad to tell you that it is a DNS server, but not much else…
		- nslookup - alone, enters an interactive mode
		- host - gives your local DNS server
		- “www dot whatever dot com” - will show if DNS server and IP address
		- server 8.8.8.8 - sets your DNS server to the popular public DNS hosted by google
		- again, “www dot whatever dot com” - will show and resolve through this google DNS
		- server 129.42.38.10 - setting to an incorrect DNS server IP address
		- this time, “www dot whatever dot com”  - gives a “DNS request timed out.”

** exam doesn’t expect you to know how to fix DNS servers, but to know how to recognize a DNS problem so you can call whoever is administering your DNS server


Windows Naming:
(obj 1.3 - Summarize general OS installation considerations and upgrade methods)
— every computer on your network needs a name; a lot of different naming conventions exist
	- DNS is one - works in a LAN and is often used

— Netbios/netbt - convention created by Windows still used today
	- takes place during the installation of Windows. (“who’s going to use this PC?”)
	- easy human name to recognize what this computer is
	- predates DNS (and most of the modern Internet)
	- will be a member of a Workgroup or an active directory domain
		- can view in System Properties
		- will show “Domain:” or “Workgroup:” depending
		- “Change settings”
			- “Computer description” - does nothing - just handy descriptive term
			- “Network ID…” (wizard) and “Change…” (dialog box) - do the same thing
				- can change “Computer name:” to almost anything you want
				- can set Workgroup or Domain here
— Workgroup vs. domain
	- a Workgroup is the most basic type of networking organization
		- just used as an organizational tool - no security, central administration
		- old fashioned, but for small networks, works just fine (share printer, share folder, etc)
	- a Domain - requires a Windows server system (different type of computer)
		- Active Directory domain - provide substantial security, central administration
			- can disperse all kinds of security stuff out to a bunch of comps at same time
			- powerful, but expensive (server, software, backup server + software)
— Homegroup - Microsoft wanted security of domain w/ convenience of workgroups
	- could set up a homegroup and when joining automatically shares doc, music, etc folders
	- was dumped by Microsoft at some point in Windows 10 


Routers:
(obj 3.2)
— Router - device that forewards and filters traffic based on IP addresses
	- magic tool used to interconnect local area networks

— Router has 2 connections:
	- 192.168.7.0 on a switch that has a built in NIC of 192.168.7.1
	- on the other side (from an ISP) has an IP address of 11.12.13.0 connected to 11.12.13.44
	- rule #1: routers don’t care where any packets come from
	- so say a packet is coming in from the internet on 11.12.13.44
	- router has (built-in or programmed by you) a routing table - tells the router where to send stuff
		- incoming packet is designed for the network 192.168.7.0 w/ a computer 192.168.7.59
			- so it sends it out on that particular port (192.168.7.1)
		- or outgoing packet for 44.99.69.5 (from 192.168.7.0) goes to default gateway
			- “if I don’t specifically list the network ID, send it out” via that port (11.12.13.44)
— without a router, wouldn’t have a way to seperate out all LANs

— enterprise type routers and home/office type routers - will have power based on their size
	- in home/office - common to see routers as 2 port routers + 4 port switch
	- Router/switch with WAP - also built-in wireless access point in one box
	- in enterprise situations - must get WAPs if needed

— DOCSIS - connection to router via cable modem vs ethernet
— Console port - a serial port using the RS-232 language to act as a connection
	- connect to a comp and use a terminal program (e.g. putty) to talk to router on init config via:
	- Yost / Rollover cable - 
		- DB-9 connector - used on the computer side
		- otherside looks like RJ-45

setting up a router via a web connection vs console ports:
— SOHO (Small Office / Home Office)
	- on initial connection will be passing out:
		- a DHCP range, giving out DHCP for individual devices connected
		- a Default username and password - important to change ASAP
	- first, use ipconfig to confirm getting a 192.168.0.X address
	- if getting an APIPA (169.254.X.XX) address - router is not passing out DHCP
	- get default IP address from manual and statically set an IP address that matches range
	- go into browser and type the default gateway (e.g. 192.168.0.1)
	- log in w/ default user and password


Basic Router Configuration:
(obj 3.6)
— most SOHO routers designed to work out-of-box - plug in and you’re connected to the internet - considered dangerous - a lot of security and configuration issues to deal with

— Quick Setup, Basic, Advanced

— WAN - IPv4 set to “Dynamic IP”  - most routers are actually DHCP clients
	- on connection up to your cable modem (or whatever you’re using upstream) a DHCP client
	- “just like your Windows computer”
	- can set to static IP, but your ISP must be giving you a particular one to type
— LAN - matter of personal choice
	** he likes to change the internal network id (“IP address:”) from default to something else
	- likes 10.11.12.1 - giving the router a new IP address on the LAN side 
	- as a DHCP server, will take care of assigning 10.11.12.X IP addresses to machines
	** must be careful in selection - if doesn’t work will need to connect to reset

— DHCP Server - can turn on/off
	** he likes to cut down default “IP Address Pool:”
		- 10.11.12.100-10.11.12.199 means 100 computers can connect
		- changed to 10.11.12.100-10.11.12.120
	- “Address Lease Time:” - how long a particular IP is given to a particular computer
		- default to 120 mins (2hrs)
		- desktops like bigger numbers
		- phones like smaller numbers
		- “when in doubt, leave as defaults”
	- “Primary DNS:” and “Secondary DNS:” - empty by default
		- almost all home routers are DHCP clients to whoever upstream to
		- upstream is giving them an IP address, default gateway, subnet mask, and DNS info
		- router going to pass that DNS down to your individual system
		- if wanted, can put e.g. 8.8.8.8, and router will pass that to individual clients
		- “when in doubt, leave it blank”
	- DHCP Reservation - don’t pass out one of the IP addresses in the pool
		- give MAC address, IP address, and Description
		- he thinks using is a mistake
		- say you have server or camera and don’t want IP address to change,
			- save 10.11.12.2-0.11.12.9 for those and set statically
			- don’t have to worry about setting a reservation
			- kept outside of the pool size anyway

— System Tools
	- Time Settings - making sure you have the right time
		- use NTP Servers to get automatically from the Internet
	- Diagnostics - handy if you think you have a problem
	- Firmware Upgrade - solves a lot of problems
	- Administration - add new users+passwords
		- Local Management
			- rather than allowing any comp connected to LAN that knows routers IP address
			- can turn it off and filter those allowed to access configs by MAC address
		- Remote Management
			- how to get in from the WAN size
			- off by default
			- setting “Web Management Port:” to e.g. 8181 allows to connect via
				- WAN IP address + :8181
			- turning on “most unsmart thing you can do as a technician”


Advanced Router Configuration:
(obj 2.3)
— Quality of Service (QoS) - toolset that allows us to meter how much bandwith things get
	- we have a limited amount of bandwith and want to take best advantage of it as we can
	- can meter based on IP address, MAC address, certain ports
— NAT / QoS
	- choose WAN or LAN & WLAN (wireless)
	- have to know and enter Uplink and Downlink speed (kbps)
	- Priority levels - Exempt, Premium, Express, Standard, Bulk (not official speeds)
		- Exempt - “if this is running, nothing else”
		- Bulk - slows it down

	- Universal Plug and Play (UPnP)
		- makes your device “noisy” - announces itself to the world
		- shows up in networking (and things like that) easier vs counting on Windows
		- just have to turn it on

— Link Layer Discovery Protocol - for Windows and is on by default
	- when you connect to a new network just have to make yourself discoverable

— Simple Network Management Protocol (SNMP) - tool that goes beyond simple discovery
	- used by network administrators to
		- not only know there’s a switch there, but see how much bandwith is going through it
		- not only know there’s a router, but have an idea what it’s filtering right now
	- (Network+ goes deep into this too)


VLANS:
(obj 3.6)
— Virtual Local Area Network (VLAN) - allows one physical switch and electronically seperates into multiple local area networks
— Managed Switch - giving a switch an IP address (which normally are accessable by MAC address)
	- look in manual for how, his got through DHCP so plugged into router
	- log into router to find
	- type the IP address into browser (Internet Explorer works best here)

— Use firmware interface to manage VLANs:
	- VLAN Configuration
		- define your VLANs by number - assign ports to VLAN
		- no interconnectivity between VLAN 1 and 2 - totally different LANS
	- Port Security
		- tell switch to memorize MAC addresses of whatever is plugged in now
		- if anything other than those try to connect, turn the port off or send me message

** exam tip: if plugging devices into a switch and they don’t see eachother, good chance of VLAN configurations


Network Troubleshooting:
(obj 5.7 - Given a scenario, troubleshoot common wired and wireless network problems)
— No connectivity - can’t get to whatever desired resource
	- are you physically connected? Is your patch cable connected to the back of your computer? Do you have good link lights?
	- if yes - and have static IP addressing on your network - check IP addresses
		- IP conflict - 2 devices with the exact same IP addresses
			- all OS’s will give error screens here
			- use ping

— Limited connectivity - some stuff I can get to, some stuff I can’t
	- screams DHCP issue - search for APIPA address
	- Rogue DHCP Server - know your network ID is 192.168.4.X and log on and see 192.168.7.X
		- scarry error - someone else has plugged in a DHCP server passing out bad info
		- must trace and find whatever box is connected and doing this

— Intermittent Connectivity - rare in wired network - problem with actual cabling itself
	- cable near elevator or motor that goes on at certain times
	- interference issue - nothing you can do other than move cable

— Unavailable Resources - normally accessable resource you can’t get to
	- e.g. folders - try pinging the actual resource and if can’t problem w/ system itself
	- not hard btwn NTFS or Network share permissions to unplug you from a resource

— Slow Transfer Speeds - more a wireless issue
	- go into task manager and see how hard wireless card is being used
	- remove processes that are eating up your network bandwith
	- “might have to update your steam games later to get work done”
	- QoS settings can be handy here

_____________________________________________
Chapter 20: Wireless Networking

Wireless Network Hardware:
(obj 2.2)
— IEEE 802.11 - primary wireless standard
— Wireless access point (WAP) - bridge between ethernet network and a wireless 802.11 network
	- only has 1 ethernet connection

two IEEE 802.11 modes:
— \ (infrastructure mode) - common (school, coffee shops, etc)
	- uses WAPs
	- Wireless network card - PCIe cards, built-in on motherboards, USB, mobile devices
	** exam tip: antenna for wireless network on laptops is in the monitor
	- Service set identifier (SSID) - name set up to connect to networks
— Ad hoc mode - more rare
	- no WAP
	- have a bunch of NICs (e.g. bunch of laptops) and one sets up an Ad hoc wireless network
	- all other computers treat that system like a WAP
	- useful e.g. “play counterstrike on an airplane”

— Antennas - get the signal around
	- Omni-directional - single piece of metal sticking up
		- radiation patten is a big fuzzy ball
		- more power to antenna, bigger fuzzy ball gets
		- doesn’t work well in multi-floor office situations
		- Diploe - 2 omni-directional antennas pointing exactly opposite eachother
			- gives flat, circular signal
			- perfect for highway, single floor office, park
			- big signal going out - don’t care about signal going up or down
	- Patch - flat rectangular
		- radiation signal = 1/2 of a big fuzzy ball
		- if against a wall and want to propogate signal in a direction
	- Highly directional - 
		- Yagi - antenna on old TVs
		- radiation signal = long stretched out football pattern
		- often have another antenna on the opposite side pointing back at it
		- popular for long throws 
		- Parabolic - like a satellite dish


Wi-Fi Standards:
(obj 1.1 - Compare and contrast wireless networking protocols)
— original 802.11 protocol defined a network speed of 1 Mbps
— same standards, extended to support higher speeds

— Industrial, scientific, and medical (ISM) radio bands - unlicensed standards that 802.11 uses
	- band = a range of frequencies
	- 2.4 GHz band: 2.412-2.4884 GHz
	- 5 GHz band: 5.150-5.875 GHz
	- different WAPs can use different ranges and not step on eachother
	- Channels - premade pieces of the band
		- 2.4 GHz band has 14 channels in Japan, 13 in UK, 11 in US)
		- 5 GHz band has a lot - 36-64; 100-144; 149-165 - no odd numbers, not all others

— 802.11a - 54Mbps - 5GHz
— 802.11b - 11Mbps - 2.4GHz
— 802.11g - 54Mbps - 2.4GHz (backwards compatible to b, not a)
— 802.11n - 100Mbps - 2.4GHz / 5GHz (backwards compatible to any)
	- MIMO (multiple in/multiple out) - allows a single WAP to use multiple antennas to narrow signal to a single device

— 802.11ac - used today
	- Multi-user MIMO - can zoom in on multiple clients at a time based on num radios
	- have a 2.4GHz band, but just for backwards compatability 

** need to know these band usages and relative speeds of the 802.11 extensions for exam

— different nomenclature:
	- 802.11n = Wi-Fi 4
	- 802.11ac = Wi-Fi 5
	- used bc if you have ac, won’t be able to take advantage of w/out ac devices
	- desktops can often be upgraded
	- “make sure your NIC matches your WAP”


Basic WAP Setup:
(obj 2.10 - Given a scenario, configure security on SOHO wireless and wired networks)
— WiFiman - tool used to show you what wireless networks are already up and running
	- can switch to channel mode to see individual bands (site survey)
	- see which channels are the most open to select best
	- general rule for 2.4GHz: set to 1, 6, or 11 - guarenteed to not overlap
	- ok if SSIDs overlap, just run better if they don’t
	- general rule for 5GHz: set to automatic - will find least congested channel
	- easy to set through same webpage interface:

— Wireless
	- create an SSID for the individual WAP
	** he doesn’t like to use the default SSID
	- Hide/disable SSID broadcast - CompTIA obsessed w/ this as a security protocol
		- might stop the honest people from trying to hack your wireless SSID
		- but, savy people, just by knowing it’s there, can do what’s necessary to attack
	- “Mode:” - can improve throughput by changing if you don’t have any 802.11b clients
		- 2.4 GHz - he changed to 802.11g/n mixed
		- 5 GHz - 802.11a/n/ac —> 802.11n/ac
			- “no a devices out there; changing speeds up dramatically”
	- “Channel Width:” - always go w/ Auto
		- individual 2.4GHz channels are 20MHz, can be sped up to 40MHz
		- this would speed up dramatically, but 2.4GHz is crowded so people avoid doing
	- “Channel:” - still choosing auto even though he’s seen 3/4 is least crowded
	- “Transmit Power:”	
		- ISM standards allow a single unliceneced device to trans 1 watt of power max
		- can adjust this for longer rage or less if neighbors using


Connecting to a Wi-Fi Network:
(ob 2.3)
— verify clients can see the SSIDs
— make sure you don’t have a disabled network card
— choosing “stay connected” creates a profile
	- Settings -> Network & Internet -> Wi-Fi -> “Manage known networks”
	- when connecting to a known network and having problems: “forget this network”

issues with connecting to an SSID:
— 1. NIC is configured as DHCP client
	- will connect but get an APIPA address
	- clue you have a bad password
	- most modern OS will tell you it can’t connect to this network
	** exam likes to ask questions like this
— 2. Passwords can change
	- forget the profile
— 3. Set wireless NIC to a static IP
	- looks like a wireless issue, but really an IP configuration issue


It’s a Huge Mesh:
(obj 2.7)
— Wireless Mesh Network (WMN) - like Ad hoc mode on steroids
	- 1 basestation connected to wireless network itself + configure SSID & password
	- plug external stations (beacon devices) wherever you want better coverage
	- works as a mesh network
	- easy to set up; usually through an app
	- use robust 3rd party encryption vs WPA2, etc

— popular; won’t have the throughput of a large robost network with lots of WAPs, but easy to configure and great for needs in small offices / homes


Beyond Wi-Fi:
(obj 2.4)
— Radio Frequency Identification (RFID)
	- sticker = radio - place on a box, etc
	- use reader to use radio freq energy to power stickers and transmit data back to reader
	- popular in warehouses (industrial world)
	- Near Field Communication (NFC) - RFID usecase for general / consumer
		- almost all smart phones today have an RFID reader
		- low power, need to be close
		- “Tap to print”, “Tap-to-pay (tap pay device)”
	- doesn’t transmit very fast

— Bluetooth
	- looks like 802.11 from a signal level, but is a:
	- Personal Area Network (PAN) - designed to connect to 2 and only 2 devices together at once
	- Class 1 — 100 mW = power — 100 m = range
	- Class 2 — 2.5 mW = power — 10 m = range
	- Class 3 — 1mW = power — 1 m = range
	- devices will have a bluetooth class that makes sense for the device (keyboard = class 2)
	- “discoverable mode” and other seeks out devices -> 4-digit pin code to verify pairing


Troubleshooting Wireless Connections:
(obj 5.7)
— No connectivity - maybe trying to get to nonexistant SSID
	- maybe changed SSID or passcode at coffee shop
	- or SSID broadcast off - will need to manually create profile
— Low RF signal - will connect but keeps turning on/off
	- get closer to ID
	- check antennas
		- remember: these are dipoles, if pointing down/out you’re sending signal into ground
		- sometimes certain antennas are specific to 2.4/5GHz bands
— Limited connectivity - suddenly built wall or put baby monitors near router creating
	- Slow transfer speeds
	- find interference and move
	- not just 802.11 - anything in ISM band (baby monitor), microwave
— Intermittant connectivity - running great or stalling
	- low RF signals - especially more advanced 802.11’s are good at getting around problems
		- if they can’t will start and stop again 
	- too many people on your wireless network
		- must get more WAPs
		- consider using QoS


________________________________________________________
Chapter 21: The Internet

Beyond the LAN:
(obj 2.7)
— Personal Area Network (PAN) - direct connection btwn two bluetooth capable devices
	- unique to bluetooth networks 
— Local Area Network (LAN) - group of computers all connected to a switch in such a way they can easily communicate
	- all computer share an identical network ID
— Wide Area Network (WAN) - interconnected LANs via a bunch of routers (1+)
	- each LAN has a unique network ID
— Metropolitan Area Network (MAN) - large WAN; limited to a local municipal area (across a town)
— The Internet - connected MANs across the world (biggest WAN)


Internet Tiers:
— Tier 1 - between 10 companies, cover the entire US - must work together
	- Peering agreements - allow traffic to go through another companies network
	- Network Operation Centers (NOCs) - 3rd party owned connection point
		- different companies set up routers here and all connected
— Tier 2 - smaller entities; decent coverage area, but not entire US
	- no peering agreement w/ Tier 1
	- pay for certain connections to Tier 1
— Tier 3 - big ISPs (comcast, AT&T)
	- no peering agreements
	- pay Tier 1 & 2 for their internet connections
	- sell internet to us - bottom of the food chain


Dial-up Connections:
(obj 2.7)
— Dial up - better known as POTS (Plain Old Telephone Service) or PSTN (Public Switched Telephone Network)
— taking a system designed to transmit analog voice and getting it to send digital data
— latest versions of every OS still can connect to this
— phone/computer <— RJ-11 connectors —> Modem
	- Modems convert analog POTS to digital COM port connections
— COM port - how Windows recognizes different serial ports
— Network & Internet -> Dial-up -> “Connect to the internet” -> enter phone num, user, pass
— Dial-up 56kbps Max

— ISDN (Integrated Services Device)
	- uses “terminal adapters”
	- completely digital line - was transition
	- could still have a telephone
	- voiceover actors established an ISDN network, still used here today


Broadband Connections:
— Broadband Connection - typical way we connect
	- always on connection vs dial-up call ins

— Digital Subscriber Line (DSL) - piggybacked telephone lines and added a digital signal
	- (need to be careful with the word Modem; only dial-up connection)
	- Asymmetric DSL (ADSL) - upload slower than download speed
		- up: 768 Kbps to 3 Mbps
		- down: 1.5 to 7+ Mbps
	- Symmetric DSL (SDSL) - upload + download are same speed
	- rare today
	- Point-to-Point Protocol Over Ethernet (PPPoE) 
		- allows multiple computers to connect to a DSL connection
		- where companies could charge for each comp connection on dial-up (multiple lines)
		- PPPoE allowed to get around this multiple user/password

— Cable 
	- Data Over Cable Service Interface Specification (DOCSIS) 
		- similar to ethernet, but allowed internet use + cable TV watching
	- speeds = 1.5/10Mbps, today 50/100Mbps or better (upload/download)
	- “MAC Clone” - setting that allows you to buy your own cable modem vs renting from cable company - today, cable companies allow you to just call and register your device

— Satellite - good for people not near cable or DSL opportunities (country, ocean)
	- speeds = 3Mbps/25 or better
	- uses a modem like anything else
	- Latency - stalls/slow

— 802.11
	- given Yagi/parabolic antenna that has much greater range than normal 802.11


Firewalls and Servers:
(obj 2.5 - Summarize the properties and purposes of services provided by networked hosts)
— One of the primary functions of firewalls is to block ports - on an incoming vs. outgoing concept
— host based firewall(s) (computer & router) allows outgoing connections on Port 80, but firewall blocks incoming connections on Port 80 —> server listens on Port 80, responds with data and swaps incoming/outgoing port numbers (14421/80) —> computer - doesn’t block this source port number
— all servers have firewalls; must have incoming port open (80) as they are serving public facing servers (e.g. web server) - but, will use stateful firewalls to block people pinging, etc
** exam tip: must be comfortable w/ incoming/outgoing on a particular port number


FTP:
(obj 2.1)
— File Transfer Protocol (FTP) - before web was popular, was way to transfer files
	- “FTP was cloud storage before cloud storage was cool.”
	- uses Port 21
	- need an FTP client - every web browser is one (“ftp://“)
	- robust FTP client (e.g. FileZilla) + robust FTP server allows creating folders, etc
	- Passive Mode - everything done on Port 21
	- Active Mode - send on Port 21, server sends back on Port 20
		- 5x faster than passive mode
		- any good routers will block
		- Port Triggering - router setting that allows incoming from a different port based on outgoing port number


E-Mail:
(obj 1.1)
— Simple Main Transfer Protocol (SMTP) - Port 25
	- send mail to SMTP server
— Post Office Protocol (POP) - Port 110
	- POP3
	- bring email down to email client
	- simplistic, but have to set up folders on client itself
— Internet Message Access Protocol (IMAP) - Port 143
	- IMAP4
	- bring email down to email client
	- stores folders/organization wherever your client is

— Iphone: Settings -> Passwords & Accounts -> Add Account
— If you have to set up manually - will need someone to give you this information
** for exam: make sure you know these port numbers - however, (in the real world) all mail today is secure mail, different port numbers used


Proxy Servers:
(obj 2.5)
— Proxy Server - additional computer to reroute web traffic through between computer and router
	- can block specific connections here rather than firewall on router
	- block bad URLs
	- check for malware
	- filter for your information (e.g. watching for Social Security Numbers)
	- popular in schools
	- application specific - web browsers, etc require setting changes for this

— (On Windows:) Control Panel -> Internet Options -> Connections -> LAN Settings
	- give IP address of proxy server
	- can specify exceptions by IP address (e.g. in-house web server)
	- he changed “Secure:” -> 443 and “FTP:” -> 21

— Proxy servers can do caching - for webpages everyone goes to often
	- webpages that update often - proxy servers will cache static stuff and only grab updating stuff

— On router, block all outgoing connections on Port 80 unless coming from proxy server


Virtual Private Networks (VPNs):
(obj 2.6)
— Virtual Private Networking (VPN) - allows remote access to printers, folders, file servers, etc
	- taking the Internet (most public of all networks) and turning it into a “fake” private network
	- “As if taking a chunk of CAT 6 cable from our switch all the way out to the Denver airport”
	- have IP address as if at home and have access to shared resources on LAN
	- VPN Client - special software make direct connection between laptop and WAN side of the router back at the office (give software the IP address)
		- DHCP server gives you another IP address
	- VPN tunnel - name for the connection
	- will need a router or dedicated box to act as VPN endpoint in your LAN

— PPTP, L2TP, IPsec - different protocols to make VPN connections; require 3rd party software
— VPN client built into Windows is limited
	- Network Connections -> VPN -> Add a VPN connection
	- give it IP address of router
	- “VPN type:” - when in doubt, leave it Automatic
	- “Type of sign-in info:” - user/pass (most common), smart card, 1-time password
— VPN connection manifests as a new network card (in “Change adapter options”)

— Split tunneling - problem where when connecting to a webpage through a VPN your computer sends request through internet to your home network, out to get webpage, back to home network, out to you
	- more advanced 3rd party VPN clients can take care of little issues like this


Internet of Things (IoT):
(obj 2.4)
— Internet of Things (IoT) - Giving internet connectivity to devices not traditionally associated with the internet to allow remote control (e.g. home automation - thermostats, light bulbs, fridge, door locks, )

3 types of tech to talk to these devices:
— 802.11 - common method to talk to these devices (almost all IoT are wireless)
— Zigbee - used exclusively for IoT - commonly home automation - runs on 2.4 GHz band bc doesn’t need a lot of bandwith (e.g. turn on/off dryer vs streaming movies)
— Z-Wave - runs on 900MHz band

— require a hub
	- smart phone applications primarily for set-up/settings


__________________________________________________________
Chapter 22: Virtualization

Understanding Virtualization:
(obj 4.2 - Given a scenario, set up and configure client-side virtualization)
— Virtual machine - completely self contained computer running within a host operating system
	- quiz - a virtual machine is a guest OS running within a host OS.
— Virtualization - real hardware allocated to a seperate system
— Emulation - pretending to have hardware you don’t (e.g. N64)

— need a CPU that supports virtualization - most do, but may need to change settings to turn it on within System Setup
— Hypervisor - actual host that runs the virtual machines
	- Type 1 - installs like an OS (nothing between hypervisor and hardware)
		- e.g. VMware ESXi, Microsoft Hyper-V, KVM
	- Type 2 - some OS already installed (Linux, Mac, etc.), install hypervisor like any application
		- e.g. VirtualBox from Oracle (free)
	- VMs run on top
	- Type 2 hypervisor not as efficient as Type 1

— Virtual machine doesn’t see the actual host OS
— Can turn it off - virtual harddrive turns into a file
— Can use to set up a ton of websites on a single machine
— Security/Recovery - if hacked, just need to turn VM off and run a backup copy of it


Your First Virtual Machine:
— download VirtualBox for your host OS
— download extension pack (allows things like mouse movement)
— download copy of OS (Ubuntu, etc)
— load iso into virtual optical drive
— follow installation
— then go to Devices -> “Insert Guest Additions CD image…”

— different OS require different resources (RAM is most important)
— can set virtual hard drive to be dynamically allocated to save on space


Advanced Virtualization Setup:
— VMs must be powered off for certain settings (e.g. creating a new virtual hard disk)
— Networking
	- Devices -> Network Settings ->
		- “Bridge Adapter” - create virtual network card via a real card on host computer
			- gets it’s own IP address through DHCP
		- “NAT” - virtual router created - creates own network ID
			- treats your physical host computer as ISP
			- puts a VM in a unique network ID
		- “NAT Network” -
			- change settings in VirtualBox first
			- create network and then VMs to populate them
			- puts multiple VMs into a single network ID
		- “Internal Network” - no router out to internet through host computer - just internal
		- “Host-only Adapter” - connected directly to host network card
			- “probably something you want to avoid using”
		- “Generic Driver” - pretends to be a different network card
			- use w/ older OS that doesn’t recognize newer network cards
			- actually emulation

** exam tip: questions about dismanagement - wants you to mess with a bunch of drives - rather than buying a comp and a bunch of drives make a virtual machine w/ drives


Cloud Computing:
(obj 4.1 - Compare and contrast cloud computing concepts)
— The Cloud - virtual machines in a server farm with remote access
	- anytime you don’t know where the computer is but you can access via it’s IP address

— Rapid elasticity - take copy of VM to different markets (e.g. want better access in Japan too)
— On-demand - clone VMs based on demand (e.g. NFL spins up tons of VMs for superbowl traffic)
— Resource pooling - billions of VMs w/ shared resources for effeciency (e.g. storage, electrical needs, HVAC, etc.)
— Infrastructure as a Service (IaaS) - rather than buying your own hardware (e.g. AWS)
	- moves network tasks such as firewalls into the Cloud
— Platform as a Service (Paas) - is IaaS but “invisible to us” - just run code (e.g. Heroku)
	- moves the machines into the Cloud so you can concentrate on the apps
— Software as a Service (SaaS) - (e.g. Google Docs, just google searching itself too, etc.)
	- moves apps to the Cloud


Cloud Ownership:
— Private Cloud - own VMs generated within an organization
— Public Cloud - open for business (e.g. Amazon S3, Microsoft Azure)
— Hybrid Cloud - big cloud partially segerated as private + public
— Community Cloud - organizations share a cloud (pool to reduce expensive setup costs)


Cloud-Based Applications:
— Cloud storage and synchronization - (e.g. OneDrive, DropBox, iCloud, etc.)
	- if multiple people are accessing at same time different syncronization methods
		- DropBox - “conflicted copy”
		- OneDrive - “whoever saves last wins”
	- email, domain controller, PVirtual desktops
	- Streaming applications - pulls down what it needs when it needs it (e.g. PowerPoint Online)
		- provides access to apps without installing them locally
		- smart phones & tablets - e.g. “Try it” on a game

** quiz - which is not a benefit of cloud technology? - applications can be downloaded locally
____________________________________________________
Chapter 23: Portable Computing

Laptop Features:
(obj 1.3 - Given a scenario, use appropriate laptop features)
 — Special function keys (use Fn + key)
	- Dual displays
	- Touchpad (on/off)
	- economy mode (use less power)
	- camera (on/off)
	- Airplane mode
	- Bluetooth (on/off)
	- Wireless (on/off)
	- Volume settings
	- Screen brightness
	- Keyboard backlight
	- Gaming mode - fans run at full speed - getting ready to cool system
— Settings -> Devices
	- Enable Bluetooth
	 - & other devices (touchpad sensitivities)
— Settings -> General
	- Location - GPS (on/off)

— Physical laptop lock and cable lock -> locking port - secure in public spaces
— Docking station - proprietary connector + port - snap laptop in to use peripherals (monitor, etc.)
— Port replicator - simpler than docking station - big USB hub

** exam tip: “Janet is doing xyz on a laptop” and sometimes being on a laptop has nothing to do with. desktops and laptops run the exact same OS and same troubleshooting issues are same.
** exam tip: occasionally network issues resolved with a button (wireless/airplane mode)


Laptop Hardware Troubleshooting - The Tools:
(obj 1.1)
— use caution - laptops all different on the inside - weak connectors, tiny screws, tape (double/single sided) - go in with a particular goal in mind
— use maintenance guides from manufacturer sites
— iFixit Web site offers a lot of user-generated how-to guides
— certain parts (e.g. 2.5” SATA drive, RAM) are identical no matter where you get - avoid buying directly from the OEM because expensive
— use Ebay - sometimes cheapest to buy complete other (maybe dead) identical laptop even for a single part

— power screwdriver, iFixit kit, piece of tape to organize screws onto
— take pictures of the disassembly process


Laptop Hardware - Core Hardware:
— Battery
— Hard drive (2.5-inch hard drive) 
— SODIMM RAM (Memory)
— Real-time Clock battery
— Mini PCIe (express) slot 
	- Wireless card/Bluetooth module
	- Wi-Fi antenna connector/placement
— Optical drive


Laptop Hardware - CPU and Motherboard:
— “almost always require a little extra surgery”
— Monitor/Screen
	- Wi-Fi antenna connector/placement - wire running through monitor - make sure reconnected
— Keyboard 
— Touchpad
— Smart card reader
— Fan - can get dirty/jammed up - sometimes need to be replaced
— DC jack - charging circuit or jack can go out often (**not on exam)

— Motherboard
— CPU - rare to be able to replace on modern laptops (soldered on) 


Touring Your Laptop Display:
(obj 1.2 - Given a scenario, install components within the display of a laptop)
— big LCD panels are easy to fix - can replace backlighting, panels, etc and save a lot of $$ doing so

— laptop monitors tend to be sealed systems - in general, will replace entire monitor
— biggest concern is taking care to reconnect all wires (camera, wireless antenna, backlight, touch screen)
— can get into some w/ spudgers & heat guns (/hair dryers) to loosen glue


_____________________________________________________
Chapter 24: Understanding Mobile Devices

What is a Mobile Device?:
(obj 1.4 - Compare and contrast characteristics of various types of other mobile devices)
— 1. single, sealed unit
— 2. Running specific mobile OS
	- Embedded System - OS is intrinsic, stored on firmware within device
	- devices not designed to support different drivers; won’t see external stuff in a sealed system
— 3. Wireless connectivity - all have 802.11 at a minimum - bluetooth, cellular, Zigby, etc.
	- may or may not have wired connectivity
	- wire mainly used for charging

— Smart Phone 
	- Android or iOS 
	- have GPS, accelerometers, etc.
	- bumper - protective case
	- wireless charging possible
	- Battery chargers
	- Battery packs
	- screen protectors

— Tablet 
	- point-of-sales systems, ordering
	- same equivalent operating systems

— Wearable technology 
	- e.g. FitBit - accelerometer, HR monitor, etc
	- e.g. Wahoo - HR monitor chest strap
	- sync with phones

— E-reader
	- uses little power
	- no backlight, color, etc

— Global Positioning System (GPS) device
	- has OS - usually cut down version of Linux

— Credit card reader
	- swipe / chip reader

— Micro/mini SD cards
	- add storage to smart devices


Mobile Connections:
(obj 1.5 - Given a scenario, connect and configure accessories and ports of other mobile devices)
— wired - base of smart devices is micro-USB, Apple Lightning, USB Type-C
	- connect for power, transfer files, syncronization
	- Mini-USB - CompTIA mentions as an option for connectors on smart devices
	- Thunderbolt - looks like USB-C - just make sure you can recognize these connections

— wireless
	- Near Field Communication (NFC) 
		- Tap-to-print/Tap-to-pay
		- just have to remember to make sure it’s turned on
		- (Android devices only - things like sending someone to a webpage)
	- Bluetooth
		- speakers, headsets,
		- Bluetooth pairing - makes a connection, creates a profile
		- inherently less secure
		- pin codes important for things like phone-phone
		- sometimes things like speakers don’t have pin codes - fine, only transmitting audio
		- will keep a profile pretty much indefinitely - if problems, delete and re pair
	- Infrared (IR) - line-of-sight
		- most phones in first decade had; less have now
		- used for things like TV remotes
		** for exam: remember it has to be line-of-sight and
		- is a low speed connection
	- 802.11
		- simple to connect to wireless network through SSID on smart phones

— cellular
	- Hotspot - device passes out an SSID
	- Tethering - has to be physically connected

— Airplane mode - shuts off 802.11, Bluetooth, NFC, anything making radio waves 


Touring Android:
(obj 1.4)
— customization is the biggest difference btwn Android and iOS
— use “Dock” to view all applications - drag and drop onto “Desktop”
— drag and drop applications together to create folders
— pull down for notification center & critical settings
— limited default gestures vs iOS (can download 3rd party)

— Applications
	- Google Play Store 
	- doesn’t have nearly as strict of control on downloads from store vs iOS
	- little more risk, but getting better all the time
	- click and hold to uninstall
	- all applications need permissions (GPS, Phone, Storage, etc.)
	- wasn’t as good with granularity of permissions vs iOS, but over time doing better job
	- limiting permissions can make apps not function the way you want

— Accounts
	- compelled to create a Google account to pair with phone
	- apply other accounts through Accounts settings (email, etc.)

— Backup/reset
	- have to turn on by default (to Google Drive)
	- most recent version as good as iOS
	- “Factory Data Reset” - can be a disaster on Android
		- must first delete all of your accounts
		- if you don’t, bricks phone - difficult/impossible to recover
		- does this so if stolen, factory reset can’t be used to erase and then use phone

— Location
	- problem - most people don’t set their location properly for their phone
	- “Location mode” 
		- High accuracy - Use GPS, Wi-Fi, Bluetooth, or cellular networks to determine loc
		- Battery Saving - Use Wi-Fi, Bluetooth, or cellular networks to determine loc
		- Device only - Use GPS to determine location
		- choice is a matter of battery life more than anything else


Touring iOS:
— Desktop/home screen - downloading an app goes directly here
— Notification center - swipe down
— Spotlight search - swipe left - wigets
— Control Center - swipe up - critical settings
— double tap on home screen to see open apps

— Applications
	- App Store
	- uninstall - hold down on app, click “x”

— Permissions
	- wonderful granularity
	- see individual permissions per app at bottom of Settings

— Accounts
	- required to have an iCloud account
	- add any other email account easily

— Backup
	- iCloud
	- log-in to iCloud account on new phone and everything (including app locations) in place

— Location Services
	- Settings -> Privacy
	- can see what apps have specific permissions


Virtual Reality:
(obj 3.6)
— Virtual Reality (VR) 
	- complete virtualized environment
	- real-world applications: military, medical, engineering
	- gaming
	- HTC VIVE Pro
	- 2 OLED monitors make 3D
	- infrared transmitters
	- detects head movement (tracking)

— Augmented Reality (AR) - 
	- places virtual objects in the real world
	- e.g. on the fly text translation

** for exam: just understand the basic difference between VR and AR


______________________________________________________
Chapter 25: Care and Feeding of Mobile Devices

Maintaining Mobile Devices:
(obj 1.6 - Given a scenario, configure basic mobile device network connectivity and application support)

two types of phones:
— CDMA (code division multiple access) phones - don’t come with SIM card
	- Firmware - drivers, OS, etc stored on ROM
	- lots of stuff that needs to be updated:
	- Baseband updates - cellular
	- Broadband updates
	- Radio firmware updates
	- Preferred Roaming List (PRL) - if texting or connecting to phone calls slow, update
		- usually dial something and does automatically
		- part of PRI (product release information)
— GSM (Global System for Mobile Communications) phones - come with SIM card
	- all updates sent to you
	- choose between automatic or manual updates
	- he is cautious re desktop updates; always updates mobile

— International Mobile Subscriber Identity (IMSI) - built into SIM - defines subscriber info
— International Mobile Equipment Identity (IMEI) - defines phone itself
	- dialing “*#06#” gives IMEI info
	- activating a phone is just connecting IMSI and IMEI

— Virtual Private Network (VPN) - 
	- higher quality VPN clients will have own software vs built-in
	- same as on desktop OS
	- 1. Give it a name
	- 2. Set up VPN
	- 3. Know the server IP address

— Remote backups - just remember to turn it on

— Antivirus/Anti-malware 
	- iOS and Android can both install
	- general concensus is iOS doesn’t need because of tight app lockdown
	- on Android, download from Google Play Store (Trusted source)
	- can download apps outside of store on Android (Untrusted source)

— Firewalls - host based firewalls as important on mobile as desktop
	- Android has 3rd party firewalls
	- iOS less necessary
	- if downloading via store on Android, less likely to need


Mobile Devices and E-mail:
— Two different incoming protocols: POP3 or IMAP
— Outgoing protocol: SMTP

— Corporate E-mail Configuration
	- Android - download a mail program and set up there, or separately in settings
	- 1. FQDN of SMTP server
	- 2. Username & password
	- 3. Port number for SMTP (usually port 25)
	- 4. FQDN of IMAP server
	- 5. Username & password
	- 6. Port number for IMAP (usually port 143)
	- choose manual set-up
	- everytime you input something phone will attempt to connect and give error
— Commercial E-mail Providers - Google, Yahoo, etc.
	- handles everything after email & password

Email security:
— POP3 encrypted port: 995
— IMAP encrypted port: 993
— SMTP encrypted port: 465 or 587
— SSL, STARTTLS
— Point-to-point encryption (P2PE) - from phone to mail server is encrypted

— S/MIME (Secure/Multi-purpose Internet Mail Extensions - 
	- MIME - turns a binary file into ASCII code (text) - reconverted on reciept
	- for a long time couldn’t encrypt email so we encrypted attachments
	- mostly obsolete because of email encryption

— ProtonMail - fully encrypted end-to-end if both parties have account

** for exam: know port numbers, etc


Mobile Synchronization:
(obj 1.7 - Given a scenario, use methods to perform mobile device synchronization)
— Synchronization - update two or more data stores so information is identical
	- predates the Cloud (**on exam)
	- on the fly updates vs backup which just creates copy

— 1. Synchronize to the desktop - with cable to computer
	- iTunes
— 2. Synchronize to an automobile - through Android or iOS via Bluetooth
— 3. Synchronize to the Cloud - dominant - Google Drive or iCloud

— Types of data to synchronize
	- handled by the OS
	- Bookmarks
	- Contacts
	- Location data
	- E-books
	- health data, applications
	- Social Media data 
		- through the app/service itself
		- Hootsuite - propogates all social media data

— Applications - have Software requirements to install 
_______________________________________________________
Chapter 26: Printers and Multifunction Devices

Laser Printers:
(obj 3.11 - Given a scenario, install and maintain various print technologies)
— Laser Printer
	- Photosensitive drum - holds a static electrical charge - more light at a particular spot causes less light to be able to be held

— 1. Processing 
	- print jobs are stored in local memory on the laser printer 
— 2. Charging
	- Primary Corona - puts a uniform negative charge (-440—600v charge)
— 3. Exposing
	- laser writes image onto photosensitive drum, reducing charge (-150v)
— 4. Developing
	- Toner @ -300v charge
	- negatives avoid negatives -  repulsed from area not exposed to laser
	- @ -300v toner is less charge than -150v so toner sticks to these areas
— 5. Transfer
	- pick up rollers - draw in paper
	- separation pads - keep only 1 piece going in at a time
	- transfer corona - puts +150v on paper
	- as paper rotates, goes past photosensitive drum
	- toner slams into paper
— 6. Fusing
	- user assembly - heat and pressure to melt and fuse toner to paper
— 7. Cleaning
	- rubber scraper removes residual toner from roller

** must know steps for exam

— All happening at the same time in a continuous process until print job is done

— This is for black & white printing; color printers have CMYK - cyan, magenta, yellow, black toner cartridges.
— 4 different rollers add color toner to the transfer belt before 

— Maintenance
	- Replace toner - new photosentive drum & toner
	- Cleaning - read documentation - sometimes an antistatic vacuum
	- Maintenance kits - new pick up rollers, transfer roller, etc
	- “maintenance mode” - to print vital statistics
	- Calibration - fixes toner placement


Inkjet Printers:
— arguably more inexpensive, cost less to run
— ink cartridges connected to jet heated up, boiled, shot
— metal deflectors point ink in different directions
— print head - stores jets and moves back and forth on carriage allows to put ink across all paper
— feeding mechanisms to bring in/out paper
— less heat and voltages - safer
— ink cartridges - MCYK - individually replacable

— Multifunction devices (MFDs)
 	- Printers
	- Scanner
	- Copiers
	- Fax

— Maintenance
	- “maintenance mode”
	- maintenance area - plugs ink jet when not in use (off to side)
	- 1. Clean heads
	- 2. Calibration
	- 3. Replace cartridges
	- 4. Clear jams


Impact Printers:
— Print head - has tiny pins that push through ink ribbon and onto paper
— Ink Ribbon
— Platin - push paper against ink ribbon
— ribbons wear out
— Tractor feed paper - holes on either side, perforated
— Impact paper - multiple copies that can be punched through
— less common in home/office - used in industrial / shipping for multipart forms

— Maintenance
	- replacing the ribbon
	- keeping it clean
	- platins run out of adjustment, use screws to realign


Thermal Printers:
— reciepts from point-of-sales systems
— thermally sensitive paper - changes colors w/ heat
— Feed assembly
— Heating element
— Special thermal paper - multipart forms - white+yellow sheet
— left in hot room will cause to change color - not a long term solution

— Maintenance
	- Replace paper
	- Clean heating element - wipe dander w/ cloth
	- Remove debris - accumulates paper dander - use air gun


Installing a Local Printer:
(obj 3.10 - Given a scenario, configure SOHO multifunction devices/printers and settings)
— Local Printer - connecting to a workstation via:
	- USB - overwhelming majority of printers have
	- Serial - connected to point-of-sales systems

— OSes generally have drivers - otherwise use manufacturers site
— Firmware updates - can be often
— download utility software to see issues

— Spooler - software that holds the print jobs - prints queue in supplied orders

— Control Panel -> Devices and Printers

— Collate - prints to multiple trays
	- software (e.g. Word) allows collation (123,123,123 vs 111,222,333)
— Duplex - prints to both sides of paper
	- software (e.g. Word) allows duplex (odd -> even)

** exam tip: can’t stop the printer? spooler requires admin permissions

— Virtual Printers -
	- Print to PDF
	- Print to XPS
	- Print to image


Sharing Printers:
— Control Panel -> Devices and Printers -> Printer Properties -> Sharing
	- can change drives, spooling (local vs your spooler)
— Settings -> Printers & scanners
	- Select a shared printer by name (if not auto found)

— Mapping a printer - 
	- mapping a folder puts on specific drives
	- net use lpt1: \\desktop-5fpl527\brother / persistent:yes
	- allows ancient dos program that uses lpt1 redirects to this printer

— Data privacy - security options enable local control over the print spooler (user authentication, no Google Drive, etc.)


Installing Wireless and Cloud Printers:
— Network Printer 
	- wired device - requires to have a network card in printer (RJ-45)
	- wireless device - requires wireless NIC in printer
	- DHCP clients - will grab IP autimatically
	- Mac - SLP; Windows - LLDP - protocols to get IP from DHCP and broadcast existance
	- use little screen to set up TCP/IP settings
	- use printer utilites from manufacturer on computer to resolve configuration issues
	- wireless subject to 802.11 standards - old printers maybe not ac
	- Ad hoc (wireless networks) - can be used
	- Bluetooth - not often, but exists - same pairing process
	- Zeroconf (Zero configuration) - Windows; Bonjour - Mac - no installation needed
	- AirPrint - wireless (Mac) 

— Cloud Printing
	 - Google Cloud Print - print to a printer you install to a google account
		- must be wireless capable (and google supported)
		- set up and then can print from any network


Troubleshooting Printers:
(obj 5.6 Given a scenario, troubleshoot printers)
— Unable to install printer - don’t have admin rights - no printer on network, etc.
— No connectivity - used before, suddenly not there - is it connected? getting DHCP? others able to use? - use mental reinstall - Rollback device driver
— Access denied - need admin permissions

— No image on printer display - is it on? sleep mode? admin locked out? bad display>
— Paper not feeding / Paper jam - problem w/ rollers or pads - maintenance kit - humidity can cause issues
— Low memory errors - probably laser printers - have RAM - can reduce resolution or buy more RAM
— Error code - research what means

— Garbled characters on paper - bad/corrupted drivers - corruption in print job - dump print job and hard reset printer
— Vertical lines on page - probably laser printers - foreign matter on optically sensitive roller (string, etc) - replace toner cartridge - too sensitive to have stuff cut off
— Color prints in wrong color - driver error or dead ink
— Printing blank pages - think based on technology and fix (thermal w/ broken heating element, etc)
— Streaks - horizontal - inkjet issue - clogged jets - “maintenance mode”
— Faded prints - low on toner, ribbon, or ink/clogged
— Ghost images - laser printer often - rubber piece that scrubs off roller broken
— Toner not fused to paper - fuser assembly needs replaced
— Creased paper - one of pick up rollers having issues and pulling at angles - maintenance kit to fix



3D Printing:
(obj 3.11)
— Filament - unmelted raw material - melt and harden quickly (thermal plastic)
— heating element and table that moves around - heated thermal plastic -> shape
— take image into tool to prepare for printing (Blender, etc)
— 3D image is sliced to produce the layers that are printed
— select slice file on printer
— The printing process requires preheating the various print elements, such as the filament, extruder, and bed


_______________________________________________________
Chapter 27: Securing Computers

Dealing with Threats:
(obj 2.5 - Summarize the properties and purposes of services provided by network hosts)
— if you want to avoid threats you need to keep your shells from being vulnerable - protect host and network (+ physical security)

— Patch your system! - all OSes generally automatically patch
	- applications need patching, servers applications need updating as well
— Run anti-malware
— Run a host-based firewall

— Intrusion Detection Systems (IDS) - box or software in network that monitors and gives notification
	- downside is must physically go to firewall after
	- not used as much as…
— Intrusion prevention systems (IPS) 
	- agents - software installed on individual machines or centrally
	- talks to firewall to turn off individual ports, urls, or whatever necessary

— tend to be expensive and need central administration (Endpoint Managemet - central system that watches for these intrusions, keeps everything up to date, software patching, etc) - great in enterprise environments


— Unified Threat Management (UTM) 
	- included IDS/IPS, firewalls. anti-malware; available on the Cloud




