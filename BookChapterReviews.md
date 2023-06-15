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
> Key Terms: adjacent-layer interaction, de-encapsulation, encapsulation, frame, networking model, packet, protocol data unit (PDU), same-layer interaction, segment

## Chapter 2