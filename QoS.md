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
  
