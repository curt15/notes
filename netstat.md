Links: [[TECHNOLOGY]] - [[PROGRAMMING]]
Rel: [[macos]]; [[linux]]; [[commands]]
Ref: 
Tags: #public 

windows = [[net]] ?

--- 
(used alone) shows statistics for all network connections (TCP & UDP; ICM leaves quick) on system; shows: Proto (protocol), Local Address (IP+port), Foreign Address, State

```sh
netstat
```

netstat see info as raw numbers (-n) vs strings
```sh
netstat -n
```

netstat see everything (-a="all") in numeric form (-n) - includes where things are listening; "will show a bunch of stuff even if not on browser, skype call, etc.";
see Windows Telemetry (checking for updates, listening for Cortana to update voice file online, etc.)
```sh
netstat -n -a

```

when connected to drive on local network, Foreign Address = your_ip:445 

can be a sign of malware if things are listening on ports you don’t know

sometimes things like network card drivers will listen on Port 80