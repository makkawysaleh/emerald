---
layout: page
title: Computer Networking
---
# Computer Networking
***
## ch1 (Introduction)
### Computer Networking Layers:
#### 1- OSI model (Open Systems Interconnection):
|#|OSI Model Layers  |Function|
|-|------------------|--------|
|1|Application Layer |Rules and protocols for how end host get email or webpage from a server.|
|2|Presentation Layer|Allow application to translate the  meaning of data, encryption and comparession.|
|3|Session Layer| Synchronization checkingpointing, recover of data exchange.|
|4|Transport Layer| Responsible for end-to-end communication over a network.|
|5|Network Layer | Responsible for moving the packets from source to the destination.|
|6|Data Link Layer| Used for error free transfer of data frames. |
|7|Physical Layer| Provides a physical medium through which bits are transmitted.|
**OSI mdel has 7 layers.**
#### 2- TCP/IP model:
|#|OSI Model Layers |Function |Example|
|-|------------------|--------|--------|
|1| Application Layer |Define the messages between end host| P2P,HTTP,SMTP,FTP,DNS|
|2| Transport Layer |Deal with reliability and congestion control.| TCP, UDP |
|3| Network Layer | Deal with routing the packets.| ICMP,IP,IGMP|
|4| Link Layer |Deal with linking and connecting routers/gateway to end host.| Fiber, coaxial, twisted-pair, wireless, Ethernet, PPP|
|5| Physical Layer |Deal with converting logical bits into its physical quantities voltage level.| bits (0,1)|
**TCP/IP model has 5 Layers.**
#### Circut Switching V.S. Packet Switching:
|Area |Circut Switching| Packet Switching|
|-----|---------------|-----------------|
|Data | In stream.    | In packets and must be digital|
|Bandwidth | Each connection get its own wire bandwidth. |Bandwidth is shared among users equally likely|
|Call setup | Yes, call must be setup. | No, connection setup needed.|
|Connection | Can share  a wire via multiplexing (FDM,TDM): <br/>**Frequancey Division Multiplexing:** on each hop, the connection gets its own bandwidth such as TV,Radio and Cell phones.<br/>**Time Division Multiplexing:** on each hop, the connection gets a slot of time. | wire cann't be shared.|
|Pros| * Guranteed that the circut is yours, when you need it.<br/>* Less overhead when connection setup.|* You can get more bandwith if you need it. If not someone else will use it.  |
|Cons|* Lots of control is needed to setup a circut. <br/>* If there is no data to send the line will be wasted. | * More overhead. <br/>* If two packets get to a switch at the same time, one will be either dropped or placed in a buffer. <br/>* packet may get lost or delayed. Congestion Control required.--> Queuing delay. |
|Better use| - Large file transfer. <br/>- When no loss or delay is allowed. <br/>- in very regular use like TV. | - Random use like surfing web. <br/>- Small file transfer. <br/>- When loss and delay is ok.|
!!! hint Hint 
*Fiber link has a bit error of 10 ^-12*
**What is the probability of packet error, when a packet is 1500 bytes?**
> 1 - (1-10^-12)^(1500*8) = 1.2 * 10 ^ -8
!!!
#### Type of delays in Packet-switching: 
1- Queuing Delay. 
 > $$Tqueuing = p /(1-p)$$
 > It is impossible to have network at full utilization. Because the delay would become infinte. 

2- Transmittion Delay. 
 > $$Ttransmission= L/R$$
 > L: is the packet size in bits
 > R: is the bitrate, bandwidth in bps.
 
3- Propagation Delay.
 >$$Tpropagation = d/s$$
 >d: distance in meter m.
 >s: speed of propagation in m/s.  

4- Processing Delay.
 > it is variable and usually given in a question.

!!! hint Data Units Conversion
**Data**
- Kilo = 10^3
- Mega = 10^6
- Giga = 10^9
- Tera = 10^12
- 1 Byte = 8 bits
***
**Speed** 
- light speed = 3\times 10^8 m/s
- fiber speed = 2*10^8 m/s
!!!
 #### Utilization: 
 ##### Formula 
 $$1- P:= \frac {actual\ user}{maximum\ use}$$
 $$2- P:= \frac{X \times(Y\times p)}{Z}$$
**where:**
X: number of users.
Y: data rate (bandwidth) of a user.
p: a probability of use per user.
Z: link bitrate(bandwidth).
#### Internet 
> Is a network of networks. 
>Tire 1 : Global ISP such as Sprint,Verizon and at&t.
> - national and international coverage.
> - treat eachother equall.
>Tire 2: Smaller ISP often regional:
> -connect to one or more Tire 1 ISPs.
> -possiple to connect Tire 2 ISPs.
> -pays Tire 1 to connect to the world, so it is a customer of Tire 1.
> Tire 3: ISPs and local ISPs 
> - closet to the end hosts.
> - last hop access.
> - customer of Tire 2.  

#### PoP (point of Presence)
Is an interface between communication entities.
**Example:** Local access point, that allow user to connect to the internet with their ISP.
</br>
***
## ch2 (Application Layer)
#### TCP V.S UDP 
|Area|TCP|UDP|
|---|---|---|
|Connection| Required connection setup _Cause delay_.<br/>`3 Sockets`|Doesn't require connection setup _faster_.<br/>`2 Sockets`|
|Pros| **high throughput** because it uses Congestion control. Data is retransmitted until receiver acknowledge recipt.<br/>**Congestion Control:** Sending rate is adjust to maximum throughput, while not overloading network.<br/>**Flow Control:** Sending as fast as possible without overload the receiver window buffer size.<br/>**easier to use**<br/>**reliability** data will be retreansmitted untill it gets `Acknowledge`| **Timing** the programmer control when data is sent.<br/><br/>**Sending rate** the  programmer control how fast data is transmitted.|
|Cons| **No timing** the programmer cann't control when data is sent.<br/> **No throughput guarantees** the programmer cann't control how fast data is transmitted.| **No Reliability** the programmer need to write a code to transmit when is needed.<br/>**No Congestion control:** the programmer need to write  a code to decide how fast to send data.|
|Examples| HTTP, SSLT, FTP, telnet, SMTP.|DNS, VoIP, TFTP.|
#### Performance of HTTP Connection:
##### 1- None-persistent HTTP:
One opject send over a TCP connection.
##### 2- Persistent HTTP:
Multiple objects can be send over single TCP connection. 
##### 3- Serial none-persistent HTTP:
One object is sent over a TCP connection and the next connection will wait until the first connection has completed.
##### 4- Parallel none-persistent HTTP:
One object is sent over TCP connection. Many Connection at once. 
#### RTT (Round Trip Time)
The time for a packet to go from the **Clinet** to **Server** and back. 
#### FTP (File Transfer Protocol)
Transfer file to/from remote host. 
port used:**21** 
It has two chnnels:
- Commands: used to transfer commands, port **21**.
- Data: used to transfer data, port **22**.  
#### SMTP (Smiple Mail Transfer Protocpl)
Has Three major components: 
  - User agent. 
  - Mail server.
  - Simple mail protocol.

It is a presistent push connection.
It is reliable, it notifies the user if it failed to send.
It uses port **25**. It uses **CRLF.CRLF** to determinate a message.

Has three faces: 
  - Hand shaking. 
  - Transfer messages.
  - Clouser.
  
#### DNS (Domain Name System)
It translates domain names to IP addresses.
It has two types:
  - **Centralized DNS:** 
    - **Pros:** 
    -Easy to maintain (one system).
    - **Cons:** 
    -Single point of falier. 
    -Need to be always online. 
    -It's database need to be big. 
    -Server could be far from users.
  - **Decentralized DNS:**
    - **Pros:** 
    -Server would be closer to user, faster in response. 
    -Much reliable.
    - **Cons:**
    -Harder to maintan and manage.
    
##### FQDN (Fully qualified domain name)
It is a complete domain name that is refer to a specific computer, or server, on the internet.
!!! note Note
**Mail server** and **web server** can both have same domain name. Web server will use **A** in RR,Resource Records. While mail server use **MX** in RR.
!!!
##### Root server
There are 13 of the world wide.
There addresses are hard coded into DNS software.
The highest level of DNS servers.
##### TLD (Top Level Domain) server
There are 1200 of the world wide.
They incloud .com , .org , .edu etc.
.com is maintain by `Network solution`.
##### Local DNS server
Usually in your broweser if you are at home network.
##### DNS attack:
- DoS (Denial of Service) attack:
Uses `ICMP` ping to flood a server and stop its services. 
##### DNS message details:
- Request Record:
(NAME, VALUE, TYPE, CLASS, TTL)
- TYPES
  - A (NAME: hostname, VALUE: IP address of host)
  - NS (NAME: domainname, VALUE: IP address of domain)
  - MX (NAME: domainname, VALUE: IP address of domain)
  - CNAME (NAME: hostname, VALUE: Canonical name for host)
##### DNS Protocol: 
  1- Query. 2- Reply. **(Both same formate)**
#### P2P (Peer to Peer) file sharing:
  __Example:__ SKYPE,Voice over IP.
  Files transfeer is between peers,not from servers.
  - Each host act like both client and server.
  - File transfer is between peers, not form servers.
  Formula of time take to distribute a file F to N clients.
$$ dcs= max\left[\frac{NF}{U_s},\frac{F}{min_i(d_i)} \right]
\newline
Where:\ {U_s}:\ is server upload bandwidth.
\newline {U_i}:\ peer\ i\ upload\ bandwidth.
\newline {d_i}: peer\ i\ download\ bandwidth. 
$$
##### Query Flooding:
 - Server: send msg to all neighborsl to search "XYZ"
 - Every host received msg: if it has"XYZ" return it, else send it to it's neighbors.
##### DHT (Distributed Hash Tabble)
- __Circular DHT(1):__
Each peer only need to know abbout immediate successor and predcessor. `O(N) messages on avg to resolve query when n peers.`
***
## ch3 (Transport Layer)
### UDP method
> Transfer as fast as data arraives from Application layer. > Application make sure no congestion.
### TCP method
> Transfer as fast as possibble with no congestion.
> The data will bbuffered if there is congestion.
### TCP V.S UDP 
|Area|TCP|UDP|
|---|---|---|
|Connection| Required connection setup _Cause delay_. `3 Sockets`|Doesn't require connection setup _faster_. `2 Sockets`| 
|Pros| <br>**high throughput** because it uses Congestion control. Data is retransmitted until receiver acknowledge recipt. <br>**Congestion Control:** Sending rate is adjust to maximum throughput, while not overloading network. <br>**Flow Control:** Sending as fast as possible without overload the receiver window buffer size. <br>**easier to use** <br>**reliability** data will be retreansmitted untill it gets `Acknowledge`| **Timing** the programmer control when data is sent. <br>**Sending rate** the programmer control how fast data is transmitted.|
|Cons| **No timing** the programmer cann't control when data is sent. <br>**No throughput guarantees** the programmer cann't control how fast data is transmitted.| **No Reliability** the programmer need to write a code to transmit when is needed. <br>**No Congestion control:** the programmer need to write a code to decide how fast to send data.| 
|Examples| HTTP, SSLT, FTP, telnet, SMTP.|DNS, VoIP, TFTP.|

#### 5 Tuples: 
__1- Protocol.__
__2- Source IP.__
__3- Destination IP.__
__4- Source port number.__
__5- Destination port number.__

#### Stop and Wait
> __Formula:__
> $$t=RTT+\frac{L}{R}$$
> $$\newline \frac{L}{R} \rightarrow T_{transmission}$$
#### Pipelined Protocols:
>Sender allow multiple "Inflight" yet to be acknowledge packets.
>- Dramatic improvment in protocol performance specially with high latency connections.
>- Increase `utilization` by factor of number of packet send.
>- Reduce waiting time of process.
>__1- GBN (Go-Back-N)__
>__2- SR (Selective Rpeat)__ 
#### Go-Back-N V.S Selective Rpeat (pipelined)
|Area|Go-Back-N|Selective Rpeat|
|----|---------|---------------|
|window size | <p align="center">__N__</p> ||
|Sender | - Sender can have up to N unacked pkts in pipeline.<br>-Sender have a timer for oldest unacked packets. `If timer expires, retransmit all unacked packets.` |- Sender can have up to N unacked pkts in pipeline.<br>-Sender have a timer for oldest unacked packets. `If timer expires, retransmit only unacked packet.`|
|Receiver| Receiver can sends only cumulative acks.`Doesn't ack pkt if there is a gap.`|Receiver acks individual packet or selective ack.|
|capabilites| Can handel high throughput. | required receiver buffer.|
|Pros| __Reliable:__<br> - Sequance number.<br>- ACKs.<br>- Time out.<br>- Sliding window.| The loss of a single ACK will result in retansmit it ~~Not the whole unacked packets~~. 
|Example | Used in TCP | -|
|Optimal size of N| Large enough so transmitter `sender` is allways transmitting.||
|How many pkts can be transmitted before the first ACK?|<p align="center">__N= RTT/(L/R)__</p>||
##### TCP Sequance Number and ACKs:
> __1- Seq. #:__
> - Byte stream "number" of the first byte is in segment's data.
> - Can be used as pointer for received data in the receiver buffer.
> 
> __2- ACKs:__
> - Sequance number of next byte expected from other side.
> - Cumulative ACK.
##### Detecting losses:
> __1- Time out: RTO retransmission time out__
> - If ACK is not received before RTO ---> `transmission time out`.
> - If RTO is too large it is wasted bandwidth and time.
> - If RTO is too small retransmitted is not needed and waste of bandwidth.
> __Best RTO= RTT+ Epsilon (smoothed RTT)__
> 
> __2-Duplicate ACKs: called NACK __
> Is 4 of the same ACK number to decide that it lost.
#### TCP Flow Control:
> Sender won't overload reveiver buffer. When `RW=0` ---> the buffer is `Full`.
> 
> __Why receiver have `recv buffer`?__
> - If packet is lost, the rest packets helds in buffer untill missing packet received.
> If app is busy, the data need to be buffer untill the app is free.

##### Client side:
Connection setup with losses. 
Total time = 3 + 6 +12 + 24 + 48 + 64 = 157 sec
__64 sec ---> give up__ 
##### Server side:
RTO = min (64, 2RTO)

### SYN 
* Each machine sould mentain a sequance # Claint and Server. 
* The clinet start the process by sending a SYN paccket. 
* The server then replay with a SYN-ACK. 
* Finally, the client replay with a ACK.
 ```sequence 
 Title: TCP connection setup 
 Client -> Server: SYN 
 Server --> Client: SYN-ACK 
 Client -> Server: ACK
 ```
 #### SYN Attack:
 * Fllod the reveiver with SYN packets + ignore ACK.
 * Each SYN arrives the OS allocate 20 KB.
 
 #### SYN-COOKIE (Defense from SYN attack ): 
 > __1- Ignore too many SYN from same host.__
 > Bad attacker can change of spoof his IP address easily.
 > __2- Use SYN Cookie.__
 >| - | Time(t) | Maximum Segment Size(MSS) | hashfunction(hash)| 
 > |:---:|:-------:| :------------------------:|:-----------------:| 
 > |**Content**| sequance random # | TCP header that specifies the largest amount of data, specified in bytes| hash of (srcIP,srcPort,desIP,desPort,t) | 
 > |**bit size**| 5 bits | 3 bits | 24 bits |
 > * The sequance number is so hard to be gueesed.
 > 
 #### TCP Congestion Control:
 ##### AIMD (Additive Increase Multiple Decrease):
 * cwnd = maximum number of unacked bytes.
 * Approche: Increse transmittion rate (window size), looking for usable bandwidth, untill loss occours.
    * Additive Increase:
      Increse cwnd by 1 MSS every RTT untill loss detected. MSS(Maximum Segment Size= 576Byte)
    * Multiple Decrease:Cut down cwnd in half after loss detected by 3 duplicate ACKs or restart from=1 when `timeout`.
  * Performance:
    __What is the data rate = how many packets are send over RTT?__
  Rate = cwnd / RTT
  __How fast does cwnd increse?__
  cwnd increase by 1 each RTT.
##### TCP Behavior:
![tcp behavior.png](:storage/60bf33df-c7e1-4959-9fe0-8b83725a620e/d6053f25.png)
__From: 
[1-6] ---> Slow start
[6-16] ---> AIMD
[16]---> 3 douplicate ACKs, But not timeout. 
(33) ---> SSthresh__

#### TCP Fairness:
![TCP fairness.png](:storage/60bf33df-c7e1-4959-9fe0-8b83725a620e/fdd24ea8.png)
* If K TCP sessions share the same link of the band with R. Each should have avrage of R/K rates.


***
## ch4 (Network Layer)
> __The service is finding paths through the network and moving packets along these path toword their destination.__
> __Addresses are needed to identify destinations.__
> 
#### Network Layer Performance Services:
* Guaranted throughput.
* Guaranted latency.
* High priority.
* Best effort no gaurantee on anything.
#### Router Function:
1- run routing algorithm to fill forwarding tabel.
2- Forward datagram from incoming to outgoing link.
### NAT (Network Address Translation):
> - Protocol that translate or map LAN address to WAN IP address.
> ![NAT.png](:storage/60bf33df-c7e1-4959-9fe0-8b83725a620e/55d96aa7.png)
> NAT Table:
> |1|2|3|4|5|
> |--|--|--|--|--|
> |Foreign IP |Foreign Port| Local Port| LAN IP|LAN port|
### DHCP (Dynamic Host Configuration Protocol)
__It configure and set end hosts:__
1- IP address. 
2- Gateway IP address.
3- Subnet mask.
4- Local DNS server IP.
### Subnets:
> - Sets of machines (Interfaces).
> - Sets of addresses.
> 
> If two or more machine are on same interface:
> They can physically reach each other without an intervening `router`. __(layer 2)__

### CIDR (Classless Inter Domain Routing):
* Subnetn portion of address of arbitrary length.
|<p align="center">IP address 24 bits</p>||
|---|--|
| **subnet part** [1-23] bits| **host part** [1-23] bits|
![CIDR.png](:storage/60bf33df-c7e1-4959-9fe0-8b83725a620e/0d180950.png)
### Graphs :
> 1- Directed graph: Edge have direction. 
> 2- Undirectedgraph: Edge are bidirectional.
> 3- Weighted edges graph.Eg. bitrate,delay,congestion,cost, etc. 
> 4- Weighted vertix graph. Eg.remaning battery power, security, etc.
#### K-connected graph:
* Connected graph is if it is possible from any vertix to any other other vertix.
* __Graph would stay connected when any (k-1) edges are removed__  
#### Least Cost / Hop Path:
![07086352.png](:storage/60bf33df-c7e1-4959-9fe0-8b83725a620e/07086352.png)
**Least Cost From A-E ---> `2 hops`
Hop path From A-E ---> `cost 5`**
#### Graph Diameter:
Is the maximum of the least hops path.
#### Vertex Degree:
Is the number of edges connected to the vertex.
#### Routing V.S Forwarding:
#### Routing
>Is the prosses of computing the table of routing.
>
> #### It has two cases:
> #### Link State: (global information)
> - All routers have a complete toplogy and link cost info.
> - OSPF and ISIS are example of Link State.
> - OLSR is Link State protected for adhock wireless.
> 
> __Cons:__ 
>   - Overhead is requaired to ensure all reouter have latest `pictuer` of topology and it consist, so no loop occur.
> 
> __Pros:__
>   - Route can immediatly computed, no problem with cconvegrance.
> 
> __Steps:__
> 1- Determine the link. 
> 2- Exchange/flood topology. 
> 3- Comoute routes Dijkstra's. 
> #### Distance Vector: (Local information)
> - Router know physically-connected neighbors, link cost neighbors.
> - Iterative process of computation, exchange of info with neighbors.
> 
> __Cons:__
>   - Iterative scheme is required, which may required many itrations before convegrece.
>   - While iterations there may be loops.
>   
> __Pros:__ 
> - Routers need to get information from their neighbors, which is low overhead in theory.
 
#### Forwarding
> Perform table lookup and moving packets to output interface is called forwarding.
> #### It has three cases:
>  __1- Static:__ 
> Roouters are manually set and only changed manually.
> 
> __2- Dynamic:__
> Routers are computed automatically. 
> - New router are computed automatically when change happen in the network topology is detected.
> 
> __hint:__ `Change in topology means that some links has broken or added.`
> 
> __3- Adaptive:__
> Routers are computed automatically
> - New routers are computed preiodically when change happen in network detected then route can change.
>   
>  __Cons:__
>  - It result in unstable networks because it will always adjast forwarding table.
>  - It is rearely used.

#### Dijsktra's Algorithm:  (Link State) 
> 1-C(XY): Link cost from X to Y, `∞` if not direct.
> 2-D(V): Current value of cost of path from source to destination V.
> 3- P(V): predessor node along path from source to destination V.
> 4- N': set of nodes whose least cost path unknown.
> 
> __Algorithm complexity: O(n^2)__

#### Dynamic programming (Bellman-Ford):
> 1- D(i,j): end to end cost from i ,j.
> 2- c(i,j): the edge cost from i to j vertex must have always do 
>   D(i,j)= min {c(i,K)+D(k,j)}
>   
#### Count to infinity (Distance Vector)
* Bad news travel quicklly.

##### Count to infinity (Poisned Reverse)
* Bad news travel slow.

####  BGP (Border Gateway Protocol)
- Used to make routers between ISPs.
- Each network is given an (AS) Autonomus System.
- There are 50000 ASs ICANN assign.

__Provide:-__
1- Obtain subnet reachability info from neighboring ASs.
2- Propagate reachability info to all AS internal routers.
3- Determine good route to subnet.
**`BGP Holes: What Pakistan goverment did to block Youtube back in days.`**

***
## ch5 (Link Layer)
***
## ch6 (Physical Layer)
***
