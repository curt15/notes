Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[macos]]; [[linux]]; [[windows]]; [[commands]]

--- 
ifconfig /all - "know your network" - document your network ID, router, DNS, etc.' "run before things go bad, so when it does, you know what supposed to look like"

```sh
ifconfig -a #sh
ifconfig /all #win

sudo ifconfig awdl0 down
sudo ifconfig awdl0 up
```

```sh
ifconfig 

    ####### LEGEND ######
	# o0 = loopback
	# gif0 = Software Network Interface
	# stf0 = 6to4 tunnel interface
	# en0 = Ethernet 0
	# fw0 = Firewire
	# en1 = Ethernet 1
	# vmnet8 = Virtual Interface
	# vmnet1 = Virtual Interface
	############################################


## LOOPBACK ADDRESS: ##
# lo0: flags=8049<UP,LOOPBACK,RUNNING,MULTICAST> mtu 16384
# 	options=1203<RXCSUM,TXCSUM,TXSTATUS,SW_TIMESTAMP>
# 	inet 127.0.0.1 netmask 0xff000000
#	inet6 ::1 prefixlen 128 
#	inet6 fe80::1%lo0 prefixlen 64 scopeid 0x1 
#	nd6 options=201<PERFORMNUD,DAD>
#
#	## SOFTWARE NETWORK INTERFACE: ##
#	gif0: flags=8010<POINTOPOINT,MULTICAST> mtu 1280
#
#	## 6-TO-4 TUNNEL INTERFACE: ##
#	stf0: flags=0<> mtu 1280
#	XHC20: flags=0<> mtu 0
#
## ETHERNET 0 // WIFI ##
#	en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
#	ether 18:65:90:cc:e4:07  ## MAC ADDRESS
#	inet6 fe80::4c6:3592:3bd0:85bb%en0 prefixlen 64 secured scopeid 0x5 
#	inet 10.0.0.39 netmask 0xffffff00 broadcast 10.0.0.255
#	nd6 options=201<PERFORMNUD,DAD>
#	media: autoselect
#	status: active
#
## NET SHARING: ##
#p2p0: flags=8843<UP,BROADCAST,RUNNING,SIMPLEX,MULTICAST> mtu 2304
#	ether 0a:65:90:cc:e4:07 
#	media: autoselect
#	status: inactive
#
## APPLE WIRELESS DIRECT LINK: ##
#awdl0: flags=8943<UP,BROADCAST,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1484
#	ether 06:1d:c4:a4:ff:49 
#	inet6 fe80::41d:c4ff:fea4:ff49%awdl0 prefixlen 64 scopeid 0x7 
#	nd6 options=201<PERFORMNUD,DAD>
#	media: autoselect
#	status: inactive
#
## ETHERNET 1 & 2: ##
#en1: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
#	options=60<TSO4,TSO6>
#	ether 4a:00:08:42:eb:30 
#	media: autoselect <full-duplex>
#	status: inactive
#en2: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
#	options=60<TSO4,TSO6>
#	ether 4a:00:08:42:eb:31 
#	media: autoselect <full-duplex>
#	status: inactive
#
## THUNDERBOLT BRIDGE: ##
#bridge0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
#	options=63<RXCSUM,TXCSUM,TSO4,TSO6>
#	ether 4a:00:08:42:eb:30 
#	Configuration:
#		id 0:0:0:0:0:0 priority 0 hellotime 0 fwddelay 0
#		maxage 0 holdcnt 0 proto stp maxaddr 100 timeout 1200
#		root id 0:0:0:0:0:0 priority 0 ifcost 0 port 0
#		ipfilter disabled flags 0x2
#	member: en1 flags=3<LEARNING,DISCOVER>
#	        ifmaxaddr 0 port 8 priority 0 path cost 0
#	member: en2 flags=3<LEARNING,DISCOVER>
#	        ifmaxaddr 0 port 9 priority 0 path cost 0
#	nd6 options=201<PERFORMNUD,DAD>
#	media: <unknown type>
#	status: inactive
#
## "BACK TO MY MAC" (disabled): ##
#utun0: flags=8051<UP,POINTOPOINT,RUNNING,MULTICAST> mtu 2000
#	inet6 fe80::9665:151b:e9e:7407%utun0 prefixlen 64 scopeid 0xb 
#	nd6 options=201<PERFORMNUD,DAD>
#	
#ipsec0: flags=8051<UP,POINTOPOINT,RUNNING,MULTICAST> mtu 1400
#	inet 10.6.6.129 --> 10.6.6.129 netmask 0xffffffff 
```

--- 

```sh
ifconfig | grep "inet 192"
```