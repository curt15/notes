Links: [[TECHNOLOGY]] - 

---


## Section 1 : Introduction

## Section 2 : Network Models
1. What is a model? (obj 1.2)
	- a model is a representation of a real world object or process.
	- models do not change a process by expanding or compressing it
	- models don't duplicate a process, they represent it to improve understanding of the underlying principles

- models are idealized & simplified - processes that allow us to represent the form and function "of the real McCoy"
- 2x very popular network models:
	- the OSI seven-layer model
	- the TCP/IP model

3. OSI vs TCP/IP Model (obj 1.2)

**OSI 7-layer model** = 7x distinct functions that a network must do in order to help make interconnectivity work (older model) 
OSI = Open Systems Interconnection model 

| | | |
| :----: | :----: | :----: |
| 7 | Application | not applications themselves, the "smarts in applications that make them network aware" (e.g. API) |
| 6 | Presentation | (old) convert data into a format that your application can read |
| 5 | Session | the actual connection btwn 2x systems; defines what is taking place in terms of how that connectivity really works (e.g. TCP connection btwn web server and client, shared folders, email) |
| 4 | Transport | "Data is big. The actual chunks of data that go through a network are relatively small"; assembly/disassembly area - disassemble & make sure packets get to the other system in good order |
| 3 | Network | logical addresses (IP addresses) (e.g. Routers in particular) |
| 2 | Data Link | anything that works w/ a MAC address (e.g. network card(s), switches, ) |
| 1 | Physical | (e.g. what type(s) of cables are used) |

**TCP/IP Model** = more simplistic than OSI model, simply because when using TCP/IP, a lot of parts don't really come into play as much.

| |||
| :----: | :----: | :----: |
| 4 | Application | handles ~ OSI 7,6,5 Application, Presentation, and Session layers. The TCP model looks at applications as applications (e.g. email, FTP, or telnet) |
| 3 | Transport | assembly & disassembly AND whatever it takes to connect to the other system to make sure the data gets there (TCP or UDP) |
| 2 | Internet | IP addresses e.g. Routers or anything that has to do with IP addresses |
| 1 | Network Interface (Link) | covers all physical cabling, MAC addresses, network cards, etc. Pretty much everything in terms of hardware (except e.g. routers); essentially OSI 1&2 |

\*\* for exam: know the name of each layer as well as the number associated with it. (e.g. OSI layer 3 -> Network Layer; OSI Transport Layer -> OSI Layer 4)

--- 
"Talking about art is like dancing about architecture." ~Steve Martin

**4. Walking Through OSI and TCP/IP** (obj 1.2)
- Starting off as a client system sending out an HTTP request to open a web page -> 
- then, on return, a web server who is actually bringing info back

| # | OSI | TCP/IP | Taking an incoming Ethernet frame and turning it into data out application can use: |
| :----: | :----: | :----: | :----: |
| 1 | 1-> 2 | 1 | |
| 2 | 3 | 2 ||
| 3 | 4 | 3 ||
| 4 | 5->6->7 | 4 ||

1 - Lowest layer, lots of pieces involved, as a **network card** waiting for data -> receive an **Ethernet frame**. The network card's job is to verify incoming MAC address is self, check frame check sequence and entire Ethernet frame to ensure good shape -> strips off **frame check sequence** & **MAC addresses** (keeping & storing the source MAC address for later/future frames sent back out). The remaining pieces of the Ethernet frame are called an **IP Packet** -> passed up to next layer. The network card's job is essentially done at this point.

2 - Biggest / \#1 job is to make sure IP address supposed to receive is self -> strip off **IP Information**, keeping source IP address b/c likely to want to send an IP packet back in a bit. The remaining pieces of Ethernet frame are called (depends on what type of packet, but in this case =) **TCP Segment** -> is designed and ready for my computer.

3 - **DATA** could be all together (e.g. one HTTP page) OR big chunks of data, if coming inbound, use the sequencing number to order individual TCP/IP segments when receiving/sending (assembly/disassembly) -> take off **sequencing number**; at this point the **DATA** is a complete chunk of data, only thing left are **port numbers**. 

4 - The very top of both models.
- The **Session Layer** (OSI Layer 5) is designed to connect a server to a client on a remote system. On today's systems we have network aware applications (web-pages, email, FTP, WoW, ) so a session layer now doesn't make sense - when starting up, they are by definition going to try to connect to something. Back in OSI days, OSes may nor have been network aware; e.g. MS Word couldn't save to anything but a drive letter -> distinct session layer that allowed to connect to a remote system vs. just saving to local hard drive.
- The **Presentation Layer** (OSI Layer 6) was designed "a bazillion years ago" b/c data would get to application, but not in form the application itself could use (e.g. ascii files, EBCDIC, etc.) -> mostly / pretty much disappeared.
- The **Application Layer**  - *not* actual application itself (browser, email client, etc.). The job = look at **port numbers** -> coming in at port 80, -> needs to go to web server. Keeps the return port number in case need to send back towards later. 

Reversed process:

| # | OSI | TCP/IP | Start with data and send out an ethernet frame |
| :----: | :----: | :----: | :----: |
| 1 | 7->6->5 | 4 | |
| 2 | 4 | 3 | |
| 3 | 3 | 2 | |
| 4 | 2->1 | 1 | |

1 - Data coming from specific application w/ goal of getting to correct computer elsewhere. Reverse **port numbers** (source and destination) and send w/ **DATA** down another layer... 
2 - Take a look at data, bring in **sequencing numbers**, break data up to individual IP packets -> making a **TCP Segment** (in this case, as a web server).
3 - Taking **IP information** from original incoming data and reversing; now have **IP packet** which is ready for the next layer. 
4 - Now, putting on the **MAC addresses**, run & add another **frame check sequence** -> SEND OUT. 

--- 
**5. Meet the Frame** (obj 1.4)

Network Interface Card (NIC) <------> Hub
- Data transfer whether through copper or fiber turning lights on/off; is always binary, 1's & 0's, -> reconstructed (e.x. for MS .doc file format).
- Data is not sent in continuous streams; sent in discrete chunks traditionally called **frames** (or packets, but differences).
- **Packetized data** = big streams of 1's & 0's; discrete chunks ("is the cornerstone of networking").
- **A single frame can be up to a max of fifteen hundred bytes long**.
- 8 bits to a byte ~= 10,000 1's & 0's to represent one single frame
- A frame is actually generated inside the network card & equally "eaten up"/destroyed on reception of frame(s).
- Data comes down from whatever application (e.g. MS Word) <-> network card creates/receives frames

--- 
**6. The MAC address** (obj 1.4)

DATA -> NIC -> HUB
- Hub (aka **Repeater**) takes the signal that comes in from one of the ports and then recreates multiple copies of it, and sends it out on ALL of the other connected cables. Every other NIC will identify that the frame is not for it and they'll just wipe it out or consume it so it never goes past the NIC, while the single computer that the frame is for will read/use it.
- **The frame does not identify the destination**; this is where a **MAC (media access control) address** comes into play.
- -> cmd or PowerShell: ```ipconfig /all```
- physical address = MAC address (e.g. 40-8D-5C-1C-5A-50)
- a 48-bit address as 12 hexadecimal characters, which are each 4 binary characters.
	- first 3 pairs = **OEM (original equipment manufacturer) numbers**; companies like Intel are issued this value "from the internet folks"
	- last 3 pairs = **Unique ID**; burned into each card at the factory and each card gets a different value
- Along with source & destination MAC addresses now attached to the frame, a **CRC (Cyclic Redundancy Check)** is attached/sent - used as a way to verify that the data is good - if its bad data, it knows to re-sent it. CRC is a FCS algorithm. 

--- 
**7. Broadcast vs. Unicast** (obj 1.4)
Unicast - the exact MAC address of the network card on the desired machine is the one that the data is being sent to.
Broadcast - 
- \*\* destination MAC address = **FF-FF-FF-FF-FF-FF** (<- always)
- *each* computer knows this is a broadcast address and "sends the data up"
- important on a LAN e.g. computer doesn't know the MAC address of another computer it's trying to find, will send out a broadcast on the LAN saying "hey, whoever has the name Mike's PC, send me back a frame so that I know who you are (by MAC address)".
- **broadcast domain** - anytime you have a group of computers that can hear eachother's broadcast are in one (e.g. all computers ona Hub are going to be members on a single broadcast domain).

Again,
- Unicast transmission is addressed to a single device on a network. 
- A broadcast transmission is sent to every device in a broadcast domain.

--- 
**8. Introduction to IP Addressing** (obj 1.4)
problem \#1 = as you add more and more computers to a broadcast domain, you end up getting so much broadcasting that nobody can get anything else done.
problem \#2 = MAC addresses don't identify in any way that computers are all part of a single LAN.

IP addressing - the overwhelming predominant form of logical addressing used to "make a big network work".

IPv4 (31.44.17).231
IPv4 (110.14.56).5
- () showing **network ID**; all computers on each network are part of a particular broadcast domain

| dst MAC | src MAC | dst IP | src IP | DATA | CRC |
- IP Packet = dst IP + src IP + DATA
- dst MAC = Router (default gateway) -> Hub -> Router - strips away frame "stuff" leaving only the IP packet.
	- built into every router "in the universe" is a routing table,
		- 110.14.56 --> use 110.14.56.1
		- 32.44.17 --> use 32.44.17.1
		- 0.0.0.0 --> use 76.4.22.123
	- based on network information, knows where to send data
	- -> Router will get MAC address of the receiving computer, build a frame with it's own MAC address as source -> SEND.
	- packets never travel alone, are always encapsulated w/in some frame or another. 
	- although the frame changes a number of times, the IP packet stays intact.

--- 
**9. Packets and Ports** (obj 1.1)

| dst IP | src IP | dst Port | src Port | DATA |
^^ IP Packet

Port Numbers - are unique to individual applications that are used all over the internet. 
- **first 1024 = well-known ports** (reserved)
- **Range = 0-65535**

| 32.44.17.231 | 110.14.56.5 | 80 | 16394 | DATA |
^^ e.g. going out to web server, src + dst switch on return, port will ensure data from specific web page will reach correct browser/location.

TCP (Transmission Control Protocol) - a connection-oriented conversation between two computers to make sure that the data transfers whole, complete, and in order. Is the overwhelming protocol used on the internet.
- Sequencing number - allows everything to reassemble properly
- **Acknowledgment number** - used when talking back to src computer and ensuring "I got it, everything is good."

**UDP (User Datagram Protocol)** - similar to TCP, but is NOT connection-oriented (connectionless)
- in a UDP environment, one computer just sends the data and hopes that you're ready for it.
- if the data doesn't come to you in good order it's up to the application itself to verify the data and then try again if not.

--- 
--- 
## Section 3 : Cabling and Topology

**10. Network Topologies** (obj 1.5) 
\*\* exam will have diagrams
- A frame is always going to be a discrete chunk of ones and zeros moving from host to host - copper cabling? electrical impulses. fiber optic? flashes of light.
- Topology = nothing more than the organization of how the ones and zeros in the form of frames move from host to host.
- Physical (physical look of cables) vs Logical (electronic/circuit diagram) topology

TYPES:
Bus Topology - all hosts are connected to a single chunk of cable called a bus. "If anybody wants to talk to anybody else, they have to get on the bus." - used to have to "tap" a lone running through the ceiling and a line would drop to each host through the ceiling. "drop" term still used today when running cables through walls -> outlet boxes.
Ring Topology - anybody wanting to get on this type of network has to connect to the individual ring. Token Ring = IBM developed this topology type and named it this; mustly gone tiday, though ring topology can still show up in a few more unique types of technologies.
Star Topology - if signal comes out of one hist, it goes to all other different hosts on the network. Quite rare and very old.
Star Bus - bus -> "box" (switch/hub) - from bus to each individual host computer through their drop(s) as much as 100m. Looks like a starr, logically works as a bus. **Is the primary topology we use today. Ethernet exclusively uses this.**
Mesh Topology - unique to wireless networks, each computer is directly connected to every other host on the network == fully meshed topology. Partially meshed topology - most common wireless network topology (e.g. sell 3-4 little pucks sold for network through a partially meshed topology).

--- 
**11. Coaxial Cabling** (obj 2.1)
(dates back to WWII)
- copper conductor, surrounded by (white) insulator, surrounded by a second conductor (metal/aluminum foil), and then all wrapped in polyvinyl chloride.  ( . )
- COmmon AXis = COAXIAL = both conductors share the same center point.
- Several types of coaxial cables are separated by the terminology of **Radio Grade (RG)**, which defines the thickness of the cable, conductors, and uses the term **OHMs**, a measurement of resistance.
	- **RG-58** - (50 OHM (rating)) - one of the oldest types of coaxial cables used in networking; uses BNC connector (which has a little rotating locket vs being threaded).
	- **RG-59** - (75 OHM) - used on cable modem / to TV; uses a threaded connector (F-type connector)
	- **RG-6** - (75 OHM) - far and beyond the most common type of cabling you will see w/ cable modems (\*thicker than RG-59\* (know for exam))

--- 
**12. Twisted Pair Cabling** (obj 2.1)
- twisting allows the signal to propagate further down a piece of copper wire.
- Unshielded Twisted Pair (UTP) = no metal covering; wouldn't want to run near an electric motor or around anything particularly high heat or high magnetic interference because it will degrade the signal. Benefit = cheap. 
- in network environment, these days, will be near exclusively 4 pairs.
- has RJ-45 connector
- Shielded Twisted Pair (STP)

EIA/TIA 568A / 568B = two standards for wiring pairs to RJ-45 connector (can be solid or stranded core (copper)):

| | 568A | 568B |
| :----: | :----: | :----: |
| 8 | brown | brown |
| 7 | brown/white | brown/white |
| 6 | orange | green |
| 5 | blue/white | blue/white |
| 4 | blue | blue |
| 3 | orange/white | green/white |
| 2 | green | orange |
| 1 | green/white | orange/white |


--- 
**13. CAT Rating** (obj 2.1)
- Cat 3 (10 Mbps) 10 megabit networks are obsolete and so is this category rating
- Cat 5 (100 Mbps) runs a max of 100m from central point to individual host
- -> Cat 5e (100-1000 Mbps @ 100m)
- Cat 6 (1 Gbps @ 100m) -> 10 Gbps for 55m
- -> Cat 6a (10 Gbps @ 100m)
- Cat 7 (10 Gbps @ 100m, shielded)
- \*\* different Cat ratings of twisted pair cabling have different number of twists


--- 
**14. Fiber Optic Cabling** 
cable contents:
- core - fiber optic that actually carries the light
- cladding - surrounds the core, light reflects off as it stays inside the fiber itself.
- cable jacket - fiber optic jacket that protects the entire set up.
- \*\* always has two connectors = **Duplex**.

types:
- **Multimode** - designed to propagate light. **LED** lights up->down through the cable (almost always **orange** cabling).
- **Single-mode** - designed to be used w/ **lasers**. Has thinner piece of fiber optic in it (almost always **yellow** cabling).
- \*\* must have the right type of device for the right cabling.

ST connector - round - like a BNC, "punch it in, twist, and it stays in place" - old...
SC connector - square - old...
FC connector - looks like ST, but is thereaded to screw in - old...
LC connector - 2 sep cables -> 1 smaller connector 
MT-RJ connector - doesn't visually show duplex - smaller
(\*\* identify from image for exam)

polishing:
PC (flat top) = physical contact - slightly rounded edged
UPC (round) = ultra physical contact  - much more rounded; creates less light loss
APC (slanted) = angled physical contact - ~7deg angle on cut - works better too
- UPC & APC work better, but take more time/craftsmanship to make


--- 
**15. Fire Ratings**

**Plenum-rated** = a *plenum* is the space between a dropped ceiling and the actual ceiling OR between a raised floor and actual floor itself. Plenum-rated has the highest fire rating of any type of cladding that can be put on cabling.
**Riser-rated** = designed to run between floors in a building. Less fire resistance required because of "fire stop" requirements.
**PVC or non-plenum** = (rated) absolutely no fire protection at all.
- plenum-rated cabling usually 2-3x as expensive as PVC


--- 
**16. Legacy Network Connections** (obj 2.1)
- not really used in networking anymore (\*\* most likely to see as wrong answer on exam than anything else)

Serial Ports = literally the oldest I/O connection in the world of computers.
	- use a language called RS-232
	- physical connection manifests as either DB-9 or DB-25

Parallel Port = aka IEEE 1284 = DB-25, but a female connector vs male part of serial
- typically used with printers
- IEEE = American standards organization - the body that organized network standards

On higher-end routers, will use a **Rollover/Yost cable** in the "CONSOLE" port (RJ-45) -> DB-9 to provide a low-end way to connect to a device (e.g. initial configuration, if something has to be completely reset from the factory). "To this day is something that really pretty much all network guys use."

--- 
--- 
## Section 4 : Ethernet Basics

**17. What is Ethernet?** (obj 2.1)
Broadband - like cable TV, a single cable runs lots and lots of conversations at once.
Baseband - one channel - everything that's being used is to send one conversation at a time.

10Base5
10 = speed in Mbps (10, 100, 1000, etc.)
Base (or Broad)
5 = 500m = length of cable running to hook into (Vampire top)
T = most often seen now = uses an unshielded twisted pair w/ a switch in the middle

...
- Ethernet is defined by the IEEE 802.3 standard
- The IEEE has defined many versions of Ethernet
- \*\* for the exam: be able to recognize the Ethernet naming syntax.


--- 
**18. Ethernet Frames** (obj 1.3)
- 1 byte = 1 octet = 8 bits

| PREAMBLE | dst MAC | src MAC | DATA TYPE | DATA | PAD | FCS |
PREAMBLE = a bunch of alternating 1's & 0's that tell a network card that a frame is incoming.
DATA TYPE = Ether type - a ~2 bytes long value (e.g. 0800 = sending IPv4 data)
DATA = min of 64 bytes; max of 1522 bytes
PAD = included if small to get up to minimum size

Jumbo frame - more advanced types of Ethernet today, unique and only for very high-speed networks; can push an individual frame of as much as 9,000 bytes.
MTU (maximum transmission unit) - max amount of data we can haul
FCS (frame check sequence) - 32-bit cyclic redundancy check - used for error detection


--- 
**19. Early Ethernet** (obj 1.3)

Segmented Ethernet - there is no  switch, just one big cable up in the ceiling.
- Computers connected to transceivers connected to 10Base5 through vampire taps w/ Ethernet cabling through drops (up to a certain limitation).
- **CSMA/CD** (Carrier sense multiple access / collision detection)
	- -> **CS (Carrier sense)** = for a computer to talk, can't have anybody else talking. Before any computers tapped in start to talk, they will listen on the wire to be able to hear if anybody else is talking, and then go ahead and do so themselves.
	- -> **MA (multiple access)** = multiple computers on the same segment talking
	- -> **CD (collision detection)** = if multiple computers start talking at the same time, the network cards would recognize a collision generate a random digit from 1-65,000 and wait in ms before transmitting again.

**10Base2** = 185m segments - "poor man's 10Base5"
- using a T connector w/ a BNC connector in a network card + cabling to the next, w/ a terminating resister on the end machines.
- up to 30 devices on one 10Base2 segment


--- 
**20. The Daddy of Ethernet, 10BaseT** (obj 2.1)
- with segmented Ethernet, if the segment itself broke at any location, the entire network would drop. IBM released an Ethernet competitor **Token Ring** that, rather than using a bus, a box called an **MSAU (multistation access unit)**, which meant that if any one of the computers broke, it didn't take down the entire netowrk. It was (a) proprietary and (b) expensive.
- --> Ethernet, in order to remain competitive, took the big, long, expensive coaxial cabling (bus) and shrunk it into a box (hub), which used cheaper UTP (unshielded twisted pair) called **10BaseT**.
- **10BaseT** is old, slow, and out of date now; nobody uses Hubs anymore, switches instead, bu the concept became cornerstone topology that every later version of Ethernet uses.
	- (1) Runs at 10 megabits per second
	- (2) maximum of 100m btwn your hub/switch and the individual nodes
	- (3) maximum of 1024 nodes per hub/switch
	- (4) designed to run on Cat3 or better UTP cable


--- 
**21. Terminating Twisted Pair** (obj 2.1)
- Terminated cable
- Straight through cable = "whatever is on pin 1 will be on pin 1 on the other end"
	- connector: 568A <--> 568A
- Crossover cable = crosses the sends and recieves. Can connect two systems together (laptop/computer) into a network w/out needing switches or anything else.
	- connector: 568A <--> 568B
- 8P8C Connector = official term for RJ-45. "Anybody who calls RJ-45 8P8C will be technically correct, but they won't have any friends"


--- 
**22. Hubs vs. Switches** (obj 1.3)

Hub -> multiport repeater 
- recreates the exact same frame for each computer plugged in when it receives one.
- e.g. 10BaseT, if 2x2 computers are having a conversation, each is using 1/2 of the total bandwidth (5 mbps)
- with a hub, you get a big degradation of the overall throughput because you have lots of people talking at the same time.
- USes CSMA/CD
- **Collision domain** = anybody who's plugged into a single hub can hear the same collision.

Switch - also a multiport repeater, but it looks at / uses MAC addresses.
- When first turned on, will act like a hub, but then quickly figure out by watching frames that "this MAC address is plugged into me at Port 1", memorize this to a MAC table, and update itself when changes are made.
- e.g. 10BaseT, each conversation on network can run at 10 mbps as Switch creates essentially a point-to-point connection between the two devices.
- **Broadcast domain** = anybody connected to the same Switch that hear eachother's broadcasts (to: FF-FF-FF-FF-FF-FF)

...
- Hubs are convenient for example, if you want to listen in on the conversations going on, can plug into any other port and listen in to everything that's going on.
- With a Switch, this is pretty much impossible b/c there are hardwired connections. Plugging into Port 5 wouldn't be able to hear. Some switches have a **maintenance port** that essentially says "I don't care what's happening, you give ma a copy of all traffic that's taking place."


--- 
## Section 5 : Modern Ethernet

**23. 100BaseT** (obj 2.1)
- Variations like 20BaseT existed, but nobody wanted it; not worth the investment of new cabling and network cards until 10x improvement.
- started at *100 Mbps Ethernet*, and everything beyond is full duplex today
- **full Duplex** - can listen and talk at the same time (allows both sides of a conversation to occur at the same time); versus for example CB Radio at half duplex that requires you to let go of the talk button before being able to hear anything. 

A number of standards came out w/ 100BaseT:
- 100BaseT4 = 100 Mbps, 1024 nodes per *hub*, and from the hub to any node was 100m, and it used *Cat 3 cabling*. (Was one of the first Ethernets that used all 4 pairs inside of an unshielded twisted pair cable.)
- 100BaseTX = 100 Mbps, 1024 nodes per hub, and from the hub to any node was 100m, and it used *Cat 5e cabling*, and it only used 2 pairs. (Was full duplex)
- -> were competing standards, no way to tell apart other than looking on the hub for "100BaseT4" or "100BaseTX" became simply known as "100BaseT"
- 100BaseFX = 100 Mbps, 1024 nodes per hub, but could run **multimode fibers** - would have to have a fiber optic switch, and you **could run 2Km**. (Was an extremely attractive option for places requiring long throws)


--- 
**24. Connecting Switches**

- Expand a broadcast domain by bringing in another switch, interconnecting with the old/other, and they will work together as one big switch.
- w/ Patch Cables
	- on old switches, would use a crossover cable btwn pretty much any ports on either switch and a link light on each will confirm connection(s)
	- on new switches, will see an **Uplink port**, basically a pre-crossover port, and uses regular straight-through cable. Some have button for "uplink/downlink" that switches btwn the uplink and the normal port function.
	- Today, most modern switches will have **Auto-sensing ports**  that will automatically configure themselves when recognizing another switch rather than a host. 


--- 
**25. Gigabit Ethernet and 10-Gigabit Ethernet** (obj 2.1)

Gigabit Ethernet Standard: 
1000BaseCX = weird as a copper standard, but uses a very strange coaxial cable called Twinax, and was 25m btwn the switch and individual nodes. 
1000BaseSX = uses multimode fiber optic cable and can have distances up to about 500m.
1000BaseLX = uses singlemode fiber optic cable and has distances up to about 5Km.
1000BaseT = uses UTP cable, originally designed to work w/ Cat 5e, but now most Cat 6 of distances to about 100m.

10-Gigabit Ethernet Standards:
(SONET = the "backbone of the internet" that these use versus else/earlier.)
10GBaseT = runs on **Cat 6** (up to 55m) or **Cat 6a** (up to 100m)
10GBaseSR = runs on multimode cable that can run 26m-400m depending on things like the type of cabling used. 
10GBaseLR = runs on singlemode cable, specifically 1310nm singlemode fiber up to 10Km (LR=long-range).
10GBaseER = runs on 1550nm singlemode cable up to 40Km.
10GBaseSR/SW = -
10GBaseLR/LW =  - all 3 have the exact same values as above ^^, 
10GBaseER/EW = - but are designed to work on these old school SONET networks.

--- 
**26. Transceivers**
- Multisource Agreement (MSA) - problem when using fiber optic Ethernet, needed to come up w/ an interchangable module that will work in any switch. MSA allows those w/ ST connectors to have a module that you swap in w/ ST connectors, or SC connectors w/ SC snap-ins, etc. Various vendors com together for development/agreement.
- Transceivers = pluggable devices that allow you to keep one switch and use any type of fiber connectors you want w/in that standard. 
- GBIC (Gigabit interface converter) = the first generation of MSA, mostly btwn ST and SC.
- SFP (small form-factor pluggable) = Same concept as GBIC, but smaller "module" (port on switch)
- SFP+ (Enhanced small form-factor pluggable) = same look as SFP, switch would specify for your particular system if/which it requires. More common today. 
- QSFP (Quad small form-factor pluggable) = designed for 40 Gigabit Ethernet more than anything else
- Bidirectional (bidi) - particularly common w/ singlemode fiber optic is rather than being a duplex cable, can use different color lasers to send AND receive on the same cable. 
	- biggest benefit is less cable running and likely to also increase network speed when it comes to fiber optic in the next 5-20 yrs. 


--- 
**27. Connecting Ethernet Scenarios** (obj 2.1)

**Loop Issues**
- Bridging loop = data will start "zooming around infinitely" and will literally take down the entire broadcast domain
- STP (Spanning Tree Protocol) - developed many years agi, a protocol to expressly avoid these types of bridging loops. On most switches just turn on, or really difficult to turn off. One switch will consider itself the "root switch", will automatically simply turn off one of its ports (the offending).
- Flood Guard - a flood is a **layer 2 attack**; some device is physically connected to the network usually for a Denial of Service or Man In the Middle type of attack(s). A smart switch can detect incoming MAC address flooding, etc. and simply turn the port off. 

**Mismatched Switch Issues**
- In most cases that a low speed switch is plugged into a high speed switch, it will slow down whenever it's talking to the slower switch (e.g. 10GBe <- 10BastT) as are auto-sensing. 
- **Speed mismatch** = a tricky thing to diagnose as either nothing will happen (not even a link light) and/or the speed light will show up different on each. Not much you can do other than junk the old switch and get something more modern.

**Dedicated High-speed Ports**
- Less common today, but for example can have a 100BaseT switch w/ a single 1GB port. Want to set up in a way to take advantage of the speed that we have e.g. (drawn configuration) OR replacing the two lower switches w/ ones that have a 1GB port + add a Gigabit switch to act as a backbone to connect from to every 1GB port available.

**Uplink and Crossover**
(drawn configuration)
- computers on the left can communicate with each other
- computers on the right can communicate with each other
- They are not able to communicate across

solutions (either...):
- a straight-through cable from uplink port to a regular port on either/or.
- a cross-over cable btwn any two regular ports
- You can run a crossover cable from uplink to uplink port(e, but Mike Meyers will tease you mercilessly if you do)

**Duplex Mismatch**
- The great thing about modern Ethernet switches is that everything today is full duplex. An individual computer plugged into the switch will auto-negotiate the best possible speed it can get, which is always w/ today's speeds going to be full duplex. 
- (drawn configuration) In this one scenario, with a crossover cable attached btwn two individual systems, but it's not working (Windows 10), will need to manually change to Half Duplex where both cumputers are negotiating for teh best speed available. 
	- Device Manager -> find network card -> right-click to Properties, change from "auto-negotiate" to "half duplex"

--- 
**Question 3**:
Which is not true of Gigabit Ethernet?
- [ ] 1000BaseT supports up to 100m over UTP
- [ ] 1000BaseLX supports btwn 100m and 10Km and can be used w/ multimode or single-mode fiber optic cable
- [ ] 1000BaseSX supports runs up to 100m over multi-mode fiber optic cable
- [x] 1000BaseSX supports btwn 100m and 10Km and can be used w/ multimode or singlemode fiber optic cable (false b/c not 10Km or singlemode)

**Question 4**:
Which of the following is not a common network problem?
- [ ] Loops
- [x] Connecting switches in a tree structure 
- [ ] Replay attack 
- [ ] Initialization vector attack 


--- 
--- 
## Section 6 : Installing a Physical Network

**28. Introduction to Structured Cabling** (obj 2.1)
- Telecomunication closet / equipment room
- Horizontal Run
- Work Area
- Patch Pannel :
- TIA Standards

--- 
**29. Terminating Structured Cabling**
110-punchdown (+ tool)
- patch panels (and RJ-44 connectors) also have associated CAT ratings 
- Horizontal runs are terminated w/ 110-punchdowns
- RJ-45 crimps are used only as patch cables

--- 
**30. Equipment Room**
Main Distribution Frame (MDF)
Intermediate Distribution Frame (IDF) = equipment rack "on every other floor"
"U" (or unit) = a standard height for components 
D marc - the point at which the cable/telephone companies equipment is separated from your (customer/subscriber) owned cabling and equipment.
D marc extension - E.g. in a leased office w/in a building, run cabling from the D marc to your floor -> router becomes D marc.

---
**31. Alternative Distribution Panels**
66-punchdown = a very old patch panel, typically used in non-VOIP telephone systems.
Fiber distribution patch panel = used to distribute fiber-optic networs
110-punchdown block patch panel is the way to distribute copper wire networks

--- 
**32. Testing Cable** (obj 5.2)
cable tester readings:
- Wiremap - each of the wires are punched in at the right place on both ends of the cable
- Continuity - the wires are actually connected (punched down) at all
- Distance - testing this requires a **Time domain reflectometer (TDR)**
	- EIA/TIA -> horizontal run must be less than 90m
	- Ethernet standard of 100m tie ins; ensures up to 10m available for patch cables (on either end)
	- **Optical TDR (OTDR)** - used to test fiber optic runs

Near-end crosstalk (NEXT), far-end crosstalk (FEXT) = more advanced tests available
**crosstalk** - interference between pairs on individual cable (on old phonelines would manifest as crackling noise), measured in dB (decibals)
- cable installers must certify that the runs are capable of advertised/required speeds (e.g. CAT 6A @ 10 Gbps)

--- 
**33. Troubleshooting Structured Cabling, Part 1** (obj 5.3)

\*\* when your network goes down, the last lace you're going to start looking for suspects is within the structured cabling system itself, however, it does happen.
- (1) verify that the OS itself sees a problem
- (2) verify link lights on the system itself as well as at the switch
- (3) check the network settings in the OS (is the network card enabled? Do you have good IP info?)

**Loopback adapter** - an RJ-45 that connects pin 1 to pin 3, and pin 2 to pin 6 -> "ping 127.0.0.1" -> get a response -> theoretically the network card itself is good. -- In reality, when most network cards today see a loopback connection like this will ping w/in own circuitry without ever going to the network card itself and using the physical connections... (\*\*know for exam, but is archaic and untrustworthy)

...
- check the patch cable
- the actual plug that goes into the wall (outlet) is subject to damage - not a bad idea to replace it if you think you've got a problem.


--- 

**34. Troubleshooting Structured Cablng, Part 2**
- Issues taking place w/in the equipment room / MDF are typically going to affect more than one user (e.g. Switch goes down and everyone connected to it will lose network access).
- **Voltmeter** - first thing to suspect is electricity, use to ensure good electricity getting to the room.
- **Voltage monitor** - plugs in -> watches Voltage for an extended peiord of time (e.g. 5:30pm and all elevators in building are Kicking in and causing sags).
	- -> FIX: a **UPS** will generally take care of these problems
- **Environmental / Temperature monitor(s)** - can determine if any problems like moisture/temp are causing issues. 
- Breaks in the cable are extremely rare, but can use TDR to test (e.g. reads 18ft, but know that run = 60ft -> ... -> it's broken.)
- **Interference** is biggest issue w/ horizontal runs, though cable installer should certify as not, can happen (e.g. A/C installed and motor close to cabling)
- **Modal distortion** - fiber optic runs, particularly multimode, are subject ro distortion over the length of the cable as the LED light bounces along. (\* singlemode is not susceptible)

--- 
**35. Using a Toner and Probe** (obj 5.2)

Fox & Hound are Tm names for the generic
**Tone generator** - creates the signal for the probe
& 
**Tone Probe** - translates the signal into an audible tone
- used to locate cables and connections (e.g. wall jack -> switch room)


--- 
**36. Wired Connection Scenarios** (obj 5.3)

Two groups of problems: (1) problems that are giving you slow or poor communication, (2) problems where there is no connectivity at all

(1)
- **Attenuation** = over a distance, a signal will begin to degrade. A slow problem ("not a problem you create, it's a problem you allowed") via poor supervision or observation of constructors who are pulling cable. 
- **Jitter** = anytime info is running through cabling, things happen and certain packets get dropped; built into the network stack to ask for ones that are missing and ntt a big deal generally. A VoIP / video streaming problem
	- wildly uncomplicated to diagnose. Have to **increase throughput** somehow to find a bottleneck, and then do something about it.
	- **Buffering** can fix, on VoIP scenarios will allow a certain amount of delay which is irritating (or increasing speed (?))
	- "In a lot of situations, the answer to jitter, is live with it."
- **Incorrect cable** = e.g. have a 10 Gbps netowrk running CAT 6a cables throughout, but use old CAT 5e to connect a device. SOLUTION: Good inventory (tracking what you have and using the right cables)

(2)
- **Bad ports** = primarily on switches are a lot less rare than you'd think. Transient electrical problems, even at low voltage, can short them out. **Use a different port**; you'd be surprised how often this fixes the problem. (\*\* bad ports on a switch is a sure sign that the switch is getting ready to die and is probably a good time to completely replace the entire switch)
- **TX/RX Reverse** = (transmit and receive reverse) using a straight-through or crossover cable when you should be using the other. SOLUTION: *Good documentation*; "if I make a crossover cable, it's clearly labeled".
- **Bent pins** = little landing pins inside the switch port can become bent through abuse, best to replace the switch. Diagnose by attempting to plug into something else and seeing what happens. (test in another device). If bent pins suspected w/in the horizontal run, can run cable from switch to host computer and test.
- **Open/Short** = used a bad cable - terminating a cable and one of transmit wires not all the way up = open 


--- 
--- 
## Section 7 : TCP/IP Basics

**37. Introduction to IP Addressing and Binary** (obj 3.1)

Dotted decimal notation = short-hand representation of the 32 1's & 0's that make up an IP address in 4 groups of 8.
- 2^8 (256 total) combinations. 0-255.
- Remember "128" and divide in half up to "1" (8 digits), then add all numbers corresponding w/ a 1

| 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | -> |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| 1 | 1 | 0 | 0 | 0 | 1 | 0 | 1 | 128+64+4+1=197 |
| 0 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 8+4+2=14 |
| 1 | 0 | 1 | 0 | 1 | 0 | 1 | 0 | =170 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | =0 |
| 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | =255 |
| 1 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | =128 |
| 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1 | =1 |


| -> | 128 | 64 | 32 | 16 | 8 | 4 | 2 | 1 | ... |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| 171-> | 1 | 0 | 1 | 0 | 1 | 0 | 1 | 1 | 171-128=43-32=11-8=3-2=1-1=0 |
| 224-> | 1 | 1 | 1 | 0 | 0 | 0 | 0 | 0 | 224-128=96-64=32-32=0 |
| 95-> | 0 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 95-64-31-16=15-8=7-4-2-1=0 |


--- 

**38. Introduction to ARP**

ARP (Address Resolution Protocol) - resolves MAC addresses from IP addresses
- a **broadcast** is sent "who has 192.168.15.163? Tell me, 192.168.15.23", everyone on the network will hear, but only the IP address holder will respond "I am 192.168.15.23! My MAC address is C9-60-00-01-2E-AC."; then, the IP packet can be wrapped -> Ethernet frame and sent.
- ```arp -a``` = Windows command to show ARM cache


--- 

**39. Classful Addressing** (obj 1.4)

**iana (Internet Assigned Numbers Authority)** = Organization that keeps track of available IP addresses and passes them out when needed - to **Regional Internet Registries (RIRs)** of the world in chunks, who then pass out chunks of IP addresses to **ISPs**.

Class licences:
**Class A** - 0 -> 126 /8 (e.g. 14.0.0.0 = 16.7 million IP addresses)
**Class B** - 128-199 /16 (=65,534 IP addresses)
**Class C** - 192-233 /24 (e.g. 193.44.16 /25 = 254 possible hosts)
- You can always tell a Class A/B/C by memorizing the first number in the octet
- **Subnetting** divides Network IDs into two or more networks.
- (Subnets don't have to be on the dots) = classless
- /16 -> a bunch of /24s ("whack 24")

subnet masks:
| 11111111 | 11111111 | 00000000 | 00000000 /16
| 255        | 255        | 0                | 0                |

network ID:
| 10100000 | 00011001 | 00000000 | 00000000 /16
| 160        | 25        | 0                | 0                |

\*\* cannot end an IP address w/ 0 or 255, but subnets can 


--- 
**40. Subnet Masks **


subnet masks:
| 11111111 | 11111111 | 11111111 | 00000000 /24
| 255        | 255        | 255                | 0                |

network ID:
| 11101000 | 000110001 | 11010000 | 00000000 /24
| 232        | 25        | 208                | 0                |

^^ in this case a /24 network, first 3 octets must be the same, & the network gets exactly 254 hosts
\*\* the subnet mask is only used by the computer - it is never sent out. It is used to determine if making a local call or if it needs to send to the default gateway -> default gateway will figure out whre to foreward the network.


--- 
**41. Subnetting with CIDR** (obj 1.4)

Classless Inter-Domain Routing (CIDR)

subnet masks:
| 11111111 | 11111111 | 11111111 | 10000000 /25 |
| 255        | 255        | 255                | 128                |

network ID:
| 11010000 | 000110001 | 10100000 | 00000000 1-126 |
| 208        | 25        | 160                | 0                |
