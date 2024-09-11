Cisco ios 

Multicast is a second class D address given 224.x.x.x 

netstat -r
route print




Private “intranet” route

Routers have default gateways to other routers

Routing tables contain information for destination, subnet mask, gateway, and NIC

Convergence is where all router tables reflect all routes 

Hop count - the # of routers it takes to get to a particular network ID

MTU (maximum transmission unit) - Ethernet = 1500 bytes

Latency - how long does it take for this particular route to react to whatever I have to do? Satellite = high latency 

Distance-vector dynamic routing protocol - sends full routing table to neighbors at fixed intervals - receiving end takes and adjusts table based on shortest hop count
Link-state dynamic routing protocol uses advertisement - sends regular “I updated” re routing table change = faster convergence (not waiting for full updates to fix broken paths) 

IGP vs EGP dynamic routing protocols 
EGP — autonomous system (AS) of routers owned by particular (e.g. Comcast) communicate externally via Border Gateway Protocol (BGP), the only EGP there is
IGP — interior gateway protocol

RIP (routing information protocol) - an IGP distance vector protocol w/ max hop count of 15 hops 
OSPF (open shortest path first) - #1 most common IGP link-state protocol. - uses one Designated Router (and one back-up) - each router is individually configured to be in an “Area ID” -> Sends individual link-states vs full routing tables - convergence happens in seconds
BGP - hybrid protocol (uses aspects of both) - breaks the internet down into ~20k AS  (w/ 