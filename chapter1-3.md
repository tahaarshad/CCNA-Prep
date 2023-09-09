# Network Fundamentals
## Chapter 1
> Provides definitions of same-layer and adjacent-layer interaction.<br>

- Same Layer Interaction on different computers: 
The two computers use a protocol to communicate with the same 
layer on another computer. The protocol defines a header that 
communicates what each computer wants to do.
- Adjacent-layer 
interaction on same computer: On a single computer, one lower layer provides a service to the layer just above. The software or hardware that implements the higher layer requests that the next lower layer perform the needed function. 

> Shows the general concept of IP routing
- Imagine how a postal service works.
> Depicts the data-link services provided to IP for the purpose of delivering IP packets from host to host
- The primary service of the data link layer is to support error-free transmission. The physical layer sends the data from the sender’s hub to the receiver’s hub as raw bits. The data link layer should recognize and correct some errors in the communicated data.
> Five steps to encapsulate data on the sending host
1. Create and encapsulate the application data with any required application 
layer headers. For example, the HTTP OK message can be returned in an HTTP 
header, followed by part of the contents of a web page.
2.  Encapsulate the data supplied by the application layer inside a transport 
layer header. For end-user applications, a TCP or UDP header is typically used.
3.  Encapsulate the data supplied by the transport layer inside a network layer 
(IP) header. IP defines the IP addresses that uniquely identify each computer.
4.  Encapsulate the data supplied by the network layer inside a data-link layer 
header and trailer. This layer uses both a header and a trailer.
5.  Transmit the bits. The physical layer encodes a signal onto the medium to 
transmit the frame
> Shows the meaning of the terms segment, packet, and frame
- Transport Layer = Segment
- Network Layer = Packet
- Data-Link Layer = Frame
> Compares the OSI and TCP/IP network models
- Layer names and numbers
> Terminology related to encapsulation
- OSI Model Data Encapsulation Terms are related to the layer number + Protocol Data Unit. So L7PDU, L6PDU and so on.
> Key Terms: adjacent-layer interaction, de-encapsulation, encapsulation, frame, networking model, packet, protocol data unit (PDU), same-layer interaction, segment>

<br>
<br>
<br>

## Chapter 2
**Term**: Distribution Switch (SWD). <br>
All these Ethernet standards come from the IEEE and include the number 
802.3 as the beginning part of the standard name.
The formal name begins with 802.3 followed by some suffix letters. The IEEE also 
uses more meaningful shortcut names that identify the speed, as well as a clue about whether 
the cabling is UTP (with a suffix that includes T) or fiber (with a suffix that includes X). 

***Ethernet Frame***
|Field|Bytes|Description|
|---|---|---------|
Preamble |7| Synchronization.
Start Frame Delimiter (SFD) | 1| Signifies that the next byte begins the Destination MAC Address field.
Destination MAC Address|6 |Identifies the intended recipient of this frame.
Source MAC Address|6| Identifies the sender of this frame.
Type |2| Defines the type of protocol listed inside the frame; today, most likely identifies IP version 4 (IPv4) or IP version 6 (IPv6).
Data and Pad*| 46– 1500 |Holds data from a higher layer, typically an L3PDU (usually an IPv4 or IPv6 packet). The sender adds padding to meet the minimum length requirement for this field (46 bytes).
Frame Check Sequence (FCS) |4 |Provides a method for the receiving NIC to determine whether the frame experienced transmission errors.

IP Type: 0800 - v4 and 86DD - V6
<br>



> Drawing of a typical wired and wireless enterprise LAN
> Several types of Ethernet LANs and some details about each

| Speed | Common Name | Informal IEEE Standard Name | Formal Name | Cable Type, Length|
| ----------- | ----------- | ----------- | ----------- | ----------- |
10 Mbps | Ethernet | 10BASE-T | 802.3 | Copper, 100m
100 Mbps | Fast Ethernet | 100BASE-T | 802.3u | Copper, 100 m
1000 Mbps | Gigabit Ethernet | 1000BASE-LX | 802.3z | Fiber, 5000 m
1000 Mbps | Gigabit Ethernet | 1000BASE-T | 802.3ab | Copper, 100 m
10 Gbps | 10 Gig Ethernet | 10GBASE-T | 802.3an | Copper, 100 m


> Conceptual drawing of transmitting in one direction each over two different electrical circuits between two Ethernet nodes <br>
> 10- and 100-Mbps Ethernet straight-through cable pinouts <br>
>  10- and 100-Mbps Ethernet crossover cable pinouts <br>
>  List of devices that transmit on wire pair 1,2 and pair 3,6 <br>
>  Typical uses for straight-through and crossover Ethernet cables <br>
- As a rule, Ethernet NIC transmitters use the pair connected to pins 1 and 2; the NIC receivers use a pair of wires at pin positions 3 and 6. LAN switches, knowing those facts about what Ethernet NICs do, do the opposite: Their receivers use the wire pair at pins 1 and 2, and their transmitters use the wire pair at pins 3 and 6.

| Pin 1,2| Pin 3,6 |
|------- | ----- |
PC NICs | Hubs
Routers | Switches
Wireless access point (Ethernet interface) | —

- The straight-through cable for 1000BASE-T uses the four wire pairs to create four circuits, but the pins need to match. It uses the same pinouts for two pairs as do the 10BASE-T and 100BASE-T standards, and it adds a pair at pins 4 and 5 and the final pair at pins 7 and 8. The Gigabit Ethernet crossover cable crosses the same two-wire pairs as the crossover cable for the other types of Ethernet (the pairs at pins 1,2 and 3,6). It also crosses the two new pairs as well (the pair at pins 4,5 with the pair at pins 7,8).

> Physical transmission concepts in a multimode cable

|Standard|Type|Distance|
|------|-------| -------|
10GBASE-S| MM | 400m
10GBASE-LX4| MM | 300m
10GBASE-LR | SM | 10km
10GBASE-E | SM | 30km


> Comparison between UTP, MM, and SM Ethernet Cabling

|Criteria|UTP|MM|SM|
|-----|----|----|-------|
Relative Cost of Cabling | Low| Medium| Medium
Relative Cost of a Switch Port |Low |Medium| High
Approximate Max Distance |100m |500m |40km
Relative Susceptibility to Interference |Some |None| None
Relative Risk of Copying from Cable Emissions |Some |None| None


>  Format of Ethernet MAC addresses
- 24 bit OUI, 24 bits Vendor
- 6 hex digits each
- 00 60 2F, 3A 07 BC
> Definitions of half duplex and full duplex
- Half duplex: The device must wait to send if it is currently receiving a frame; in other 
words, it cannot send and receive at the same time.<br>
- Full duplex: The device does not have to wait before sending; it can send and receive at 
the same time
> Examples of which interfaces use full duplex and which interfaces use half duplex
- Only when connecting to lan hub, use half-duplex


## Chapter 3

> Ethernet over MPLS—physical connections


This book refers to this particular Ethernet WAN service with a couple of the common names:
<br>
Ethernet over MPLS (EoMPLS): A term that refers to Multiprotocol Label Switching 
(MPLS), a technology that can be used to create the Ethernet service for the customer. 

>Four-step process of how routers route (forward) packets

Step 1. Use the data-link Frame Check Sequence (FCS) field to ensure that the frame had no errors; if errors occurred, discard the frame.
<br>

Step 2. Assuming that the frame was not discarded at Step 1, discard the old data-link  header and trailer, leaving the IP packet.
<br>

Step 3. Compare the IP packet’s destination IP address to the routing table, and find the 
route that best matches the destination address. This route identifies the outgoing interface of the router and possibly the next-hop router IP address.
<br>

Step 4. Encapsulate the IP packet inside a new data-link header and trailer, appropriate 
for the outgoing interface, and forward the frame

>IP Routing and Encapsulation

PC1 sends the packet to its default router

R1 processes the incoming frame and forwards the packet to R2.

R2 processes the incoming frame and forwards the packet to R3

R3 processes the incoming frame and forwards the packet to PC2

>Two statements about how IP expects IP addresses to be grouped into networks or subnets

■ Two IP addresses, not separated from each other by a router, must be in the same group 
(subnet). 

■ Two IP addresses, separated from each other by at least one router, must be in different 
groups (subnets).

>Three-step process of how routing protocols learn routes

Step 1. Each router, independent of the routing protocol, adds a route to its routing 
table for each subnet directly connected to the router.

Step 2. Each router’s routing protocol tells its neighbors about the routes in its routing 
table, including the directly connected routes and routes learned from other 
routers.

Step 3. After learning a new route from a neighbor, the router’s routing protocol adds 
a route to its IP routing table, with the next-hop router of that route typically 
being the neighbor from which the route was learned.

>IP Routing Protocol Basic Process

Step A. Subnet 150.150.4.0 exists as a subnet at the bottom of the figure, connected to 
Router R3.

Step B. R3 adds a connected route for 150.150.4.0 to its IP routing table; this happens 
without help from the routing protocol.

Step C. R3 sends a routing protocol message, called a routing update, to R2, causing 
R2 to learn about subnet 150.150.4.0.

Step D. R2 adds a route for subnet 150.150.4.0 to its routing table.

Step E. R2 sends a similar routing update to R1, causing R1 to learn about subnet 
150.150.4.0.

Step F. R1 adds a route for subnet 150.150.4.0 to its routing table. The route lists R1’s 
own Serial0 as the outgoing interface and R2 as the next-hop router IP address 
(150.150.2.7)

>Example that shows the purpose and process of DNS name resolution

In this case, PC11, on the left, needs to connect to a server 
named Server1. At some point, the user either types in the name Server1 or some application on PC11 refers to that server by name. At Step 1, PC11 sends a DNS message—a 
DNS query—to the DNS server. At Step 2, the DNS server sends back a DNS reply that 
lists Server1’s IP address. At Step 3, PC11 can now send an IP packet to destination address 
10.1.2.3, the address used by Server1.

>Example of the purpose and process of ARP

The figure shows the ARP Request sent by router R3, on the left of 
the figure, as a LAN broadcast. All devices on the LAN will then process the received frame. 
On the right, at Step 2, host PC2 sends back an ARP Reply, identifying PC2’s MAC address. 
The text beside each message shows the contents inside the ARP message itself, which lets 
PC2 learn R3’s IP address and matching MAC address, and R3 learn PC2’s IP address and 
matching MAC address.

>Ping and ICMP

Ping (Packet Internet Groper) uses the Internet Control Message Protocol (ICMP), sending 
a message called an ICMP echo request to another IP address. The computer with that IP 
address should reply with an ICMP echo reply. If that works, you successfully have tested 
the IP network. In other words, you know that the network can deliver a packet from one 
host to the other and back. ICMP does not rely on any application, so it really just tests 
basic IP connectivity—Layers 1, 2, and 3 of the OSI model. 