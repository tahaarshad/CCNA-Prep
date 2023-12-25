# Quality of Service

Prioritiing traffic

## When
- Aggregation
- SPeed mismatch
- LAN to WAN
  
## Source of Delay
- Code delay: The fixed amount of time it takes to compress data at the source before transmitting to the first internetworking device, usually a switch.
- Packetization delay:	The fixed time it takes to encapsulate a packet with all the necessary header information.
- Queuing delay:	The variable amount of time a frame or packet waits to be transmitted on the link.
- Serialization delay:	The fixed amount of time it takes to transmit a frame onto the wire.
- Propagation delay:	The variable amount of time it takes for the frame to travel between the source and destination.
- De-jitter delay:	The fixed amount of time it takes to buffer a flow of packets and then send them out in evenly spaced intervals.


Packet loss is the result of excessive network congestion.

Jitter is caused by variations in delay.

## Voice
- Predictable and smooth
- Voice can tolerate a certain amount of latency, jitter, and loss without any noticeable effects. 

## Video
- Without QoS and a significant amount of extra bandwidth capacity, video quality typically degrades. The picture appears blurry, jagged, or in slow motion. The audio portion of the feed may become unsynchronized with the video.
- Video traffic tends to be unpredictable, inconsistent, and bursty compared to voice traffic.

## Data
- Most applications use either TCP or UDP. Unlike UDP, TCP performs error recovery. Data applications that have no tolerance for data loss, such as email and web pages, use TCP to ensure that, if packets are lost in transit, they will be resent. Data traffic can be smooth or bursty. Network control traffic is usually smooth and predictable. 

- However, some TCP applications can consume a large portion of network capacity. FTP will consume as much bandwidth as it can get when you download a large file, such as a movie or game.


## Queuing ALogrithms
- First In First Out: No QoS
- Weighted Fair QUeuing: Adds prority to certain traffic
- Class-Based Weighted Fair Queuing: User defined classes
- Low Latency Queuing: Proritize certain traffic over other queues. So a priority queue and CBWFQ

Which queuing algorithm is effective for large links that have little delay and minimal congestion?
FIFO

## QoS Models
### Best Effort
The basic design of the internet is best-effort packet delivery and provides no guarantees. 
- Benefits
    - scalable, easy and quick, no special mechanism required

- Drawbacks
    - no guarantee, any order of arrival, no special treatment

### Integrated Services
developed in 1994 to meet the needs of real-time applications, such as remote video, multimedia conferencing, data visualization applications, and virtual reality. IntServ is a multiple-service model that can accommodate many QoS requirements.
- Benefits
    - Explicit end-to-end resource admission control, Per-request policy admission control, Signaling of dynamic port numbers

- Drawbacks
      - Resource intensive, Flow-based approach not scalable to large implementations such as the internet.

### Differentiated Services
(DiffServ) QoS model specifies a simple and scalable mechanism for classifying and managing network traffic. For example, DiffServ can provide low-latency guaranteed service to critical network traffic such as voice or video, while providing simple best-effort traffic guarantees to non-critical services such as web traffic or file transfers.
- Benefits
    - Scalable, provides different levels of quality

- Drawbacks
    - No absolute guarantee of service quality, Requires a set of complex mechanisms to work in concert throughout the network
  
## QoS Implementation
### Classification and Marking
Classify packets and then mark them by adding a vlaue to the packet header according to the policies. Marking is done close to source.

Ethernet (802.1Q, 802.1p) --- 2	--- Class of Service (CoS) --- 	3
802.11 (Wi-Fi)--- 	2	--- Wi-Fi Traffic Identifier (TID)	--- 3
MPLS--- 	2	--- Experimental (EXP)--- 	3
IPv4 and IPv6	--- 3	--- IP Precedence (IPP)	--- 3
IPv4 and IPv6	--- 3	--- Differentiated Services Code Point (DSCP)	--- 6

- Marking at layer 2
    - 802.1q,Class of Service: The 802.1Q standard also includes the QoS prioritization scheme known as IEEE 802.1p. The 802.1p standard uses the first three bits in the Tag Control Information (TCI) field. Known as the Priority (PRI) field, this 3-bit field identifies the Class of Service (CoS) markings. Three bits means that a Layer 2 Ethernet frame can be marked with one of eight levels of priority (values 0-7)
- MArking at Layer 3
    - 8-bit field for marking: the Type of Service (ToS) field for IPv4 and the Traffic Class field for IPv6.
    - DSCP: The 64 DSCP values are organized into three categories:

Best-Effort (BE) - This is the default for all IP packets. The DSCP value is 0. The per-hop behavior is normal routing. When a router experiences congestion, these packets will be dropped. No QoS plan is implemented.
Expedited Forwarding (EF) - RFC 3246 defines EF as the DSCP decimal value 46 (binary 101110). The first 3 bits (101) map directly to the Layer 2 CoS value 5 used for voice traffic. At Layer 3, Cisco recommends that EF only be used to mark voice packets.
Assured Forwarding (AF) - RFC 2597 defines AF to use the 5 most significant DSCP bits to indicate queues and drop preference. 

## Trust Boundaries
Where should markings occur? Traffic should be classified and marked as close to its source as technically and administratively feasible. This defines the trust boundary.

Trusted endpoints have the capabilities and intelligence to mark application traffic to the appropriate Layer 2 CoS and/or Layer 3 DSCP values. Examples of trusted endpoints include IP phones, wireless access points, videoconferencing gateways and systems, IP conferencing stations, and more.
Secure endpoints can have traffic marked at the Layer 2 switch.
Traffic can also be marked at Layer 3 switches / routers.
Re-marking traffic, for example, re-marking CoS values to IP Precedent or DSCP values, is typically necessary.

## Shaping and Policing
Traffic shaping retains excess packets in a queue and then schedules the excess for later transmission over increments of time. The result of traffic shaping is a smoothed packet output rate.

## WRED
Some congestion avoidance techniques provide preferential treatment for which packets will get dropped. For example, Cisco IOS QoS includes weighted random early detection (WRED) as a possible congestion avoidance solution. The WRED algorithm allows for congestion avoidance on network interfaces by providing buffer management and allowing TCP traffic to decrease, or throttle back, before buffers are exhausted. Using WRED helps avoid tail drops and maximizes network use and TCP-based application performance. There is no congestion avoidance for User Datagram Protocol (UDP)-based traffic, such as voice traffic. In case of UDP-based traffic, methods such as queuing and compression techniques help to reduce and even prevent UDP packet loss.


What happens when an edge router using IntServ QoS determines that the data pathway cannot support the level of QoS requested?
Data is not forwarded
