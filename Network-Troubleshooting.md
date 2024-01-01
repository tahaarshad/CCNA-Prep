# Network Troubleshooting
## Documentation
Common network documentation includes the following:

- Physical and logical network topology diagrams
- Network device documentation that records all pertinent device information
- Network performance baseline documentation

### Network Topology
- Physical Topology:
Device name
Device location (address, room number, rack location)
Interface and ports used
Cable type
- Logical IPv4 Topology
Device identifiers
IP addresses and prefix lengths
Interface identifiers
Routing protocols / static routes
Layer 2 information (i.e., VLANs, trunks, EtherChannels)
- Logical IPv6 Topology

### Device Documentation
- Router Device Documentation

| Device | Model | Description | Location | IOS | License |
| --- | --- | --- | ----- | ------ | ---- |
| Central   | ISR 4321 | Central Edge Router | Building A Rm: 137 | Cisco IOS XE Software, Version 16.09.04 flash:isr4300-universalk9_ias.16.09.04.SPA.bin | pbasek9 securityk9 |



Interface | Description	| IPv4 Address	| IPv6 Address	| MAC Address | Routing

- LAN Switch Device Documentation

| Device | 	Model |	Description | Mgt. IP Address	| IOS |	VTP |
| --- | --- | --- | --- | --- | --- |
| S1 |	Cisco Catalyst WS-C2960-24TC-L |	Branch-1 LAN1 switch |	192.168.77.2/24 |	IOS: 15.0(2)SE7 Image: C2960-LANBASEK9-M	| Domain: CCNA Mode: Server

Port	| Description	| Access	| VLAN	| Trunk | 	EtherChannel | 	Native |	Enabled

- End System Documentation

| Device	| OS | Services | 	MAC Address |	IPv4 / IPv6 Addresses |	Default Gateway |	DNS |
| --- | --- | --- | --- | --- | --- | --- |
| SRV1 |	MS Server 2016 |	SMTP, POP3, File services, DHCP |	5475.d08e.9ad8	| 10.0.0.2/30 2001:db8:acad:1::2/64 |	10.0.0.1 2001:db8:acad:1::1 |	10.0.0.1 2001:db8:acad:1::1 |

### Establishing Network Baseline
Questions to ask:
- How does the network perform during a normal or average day?
- Where are the most errors occurring?
- What part of the network is most heavily used?
- What part of the network is least used?
- Which devices should be monitored and what alert thresholds should be set?
- Can the network meet the identified policies?

***Step 1 - Determine What Types of Data to Collect***
***Step 2 - Identify Devices and Ports of Interest***
***Step 3 - Determine the Baseline Duration***

### Data Measurement
ping, traceroute, and telnet, as well as show commands.

show version
show ip interface [brief] 
show ipv6 interface [brief]
show interfaces 
show ip route
show ipv6 route 
show cdp neighbors detail
show arp
show ipv6 neighbors
show running-config
show vlan
show port
show tech-support

## Toublesooting Process
***Process***
Stage 1: Gather Symptoms
Stage 2: Isolate the Problem
Stage 3: Implement Corrective Action
Problem Fixed?
No - If it did not fix the problem or it it
created another problem, undo
corrective action and start agaim
Yes - Stage 4: Document solution and
save changes.

***7-Step Process***
Define Problern
Gather Information
Analyze Information
Eliminate Possible Causes
Propose Hypothesis
Test Hypothesis
Solve the Problem and
Doctnnent Solution


###Question End Users
| Guidelines | Questions |
| --- | --- |
| Ask pertinent questions.	| What does not work? What exactly is the problem? What are you trying to accomplish?|
| Determine the scope of the problem | Who does this issue affect? Is it just you or others? What device is this happening on? |
| Determine when the problem occurred / occurs. | When exactly does the problem occur? When was the problem first noticed? Were there any error message(s) displayed? |
| Determine if the problem is constant or intermittent. | Can you reproduce the problem? Can you send me a screenshot or video of the problem? |
| Determine if anything has changed. | What has changed since the last time it did work ? |
| Use questions to eliminate or discover possible problems. | What works? What does not work? |

***Gather Information using IOS Commands***
***Troubleshooting with Layered Models***
- Bottom-Up = hw oriented
- Top-Down = sw oriented
- Divide-and-Conquer = experienced before
- Follow-the-Path
- Substitution
- Comparison
- Educated Guess

## Troubleshooting Tools
***Software:***
Network Management System Tools

Knowledge Bases

Baselining Tools

***Protocol Analyzers:***
Wireshark

***Hardware:***
Digital Multimeters: measure electrical values of voltage, current, and resistance.

Cable Testers: detect broken wires, crossed-over wiring, shorted connections, and improperly paired connections. These devices can be inexpensive continuity testers, moderately priced data cabling testers, or expensive time-domain reflectometers (TDRs)

Cable Analyzers: test and certify copper and fiber cables for different services and standards.

Portable Network Analyzers: troubleshooting switched networks and VLANs.

Cisco Prime NAM: includes hardware and software for performance analysis in switching and routing environments.

***Syslog Server***
In the command output, system messages from level 0 (emergencies) to 5 (notifications) are sent to the syslog server at 209.165.200.225.

R1(config)# logging host 209.165.200.225 
R1(config)# logging trap notifications 
R1(config)# logging on
R1(config)#

## Symptoms and Causes of Network Problems

### Physical Layer


| Symptom                    | Description                        |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Performance lower than baseline | Requires previous baselines for comparison. The most common reasons for slow or poor performance include overloaded or underpowered servers, unsuitable switch or router configurations, traffic congestion on a low-capacity link, and chronic frame loss.                                                                                                                                                                                                 |
| Loss of connectivity       | Loss of connectivity could be due to a failed or disconnected cable. Can be verified using a simple ping test. Intermittent connectivity loss can indicate a loose or oxidized connection.                                                                                                                                                                                                                                              |
| Network bottlenecks or congestion | If a router, interface, or cable fails, routing protocols may redirect traffic to other routes that are not designed to carry the extra capacity. This can result in congestion or bottlenecks in parts of the network.                                                                                                                                                                                                                   |
| High CPU utilization rates | High CPU utilization rates are a symptom that a device, such as a router, switch, or server, is operating at or exceeding its design limits. If not addressed quickly, CPU overloading can cause a device to shut down or fail.                                                                                                                                                                                                            |
| Console error messages     | Error messages reported on the device console could indicate a physical layer problem. Console messages should be logged to a central syslog server.                                                                            |


| Problem Cause             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Power-related             | This is the most fundamental reason for network failure. Check the operation of the fans and ensure that the chassis intake and exhaust vents are clear. If other nearby units have also powered down, suspect a power failure at the main power supply.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Hardware faults           | Faulty network interface cards (NICs) can be the cause of network transmission errors due to late collisions, short frames, and jabber. Jabber is often defined as the condition in which a network device continually transmits random, meaningless data onto the network. Other likely causes of jabber are faulty or corrupt NIC driver files, bad cabling, or grounding problems.                                                                                                                                                                                                                                                                                                                                                                    |
| Cabling faults            | Many problems can be corrected by simply reseating cables that have become partially disconnected. When performing a physical inspection, look for damaged cables, improper cable types, and poorly crimped RJ-45 connectors. Suspect cables should be tested or exchanged with a known functioning cable.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Attenuation               | Attenuation can be caused if a cable length exceeds the design limit for the media, or when there is a poor connection resulting from a loose cable, or dirty or oxidized contacts. If attenuation is severe, the receiving device cannot always successfully distinguish one bit in the data stream from another bit.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Noise                     | Local electromagnetic interference (EMI) is commonly known as noise. Noise can be generated by many sources, such as FM radio stations, police radio, building security, and avionics for automated landing, crosstalk (noise induced by other cables in the same pathway or adjacent cables), nearby electric cables, devices with large electric motors, or anything that includes a transmitter more powerful than a cell phone.                                                                                                                                                                                                                                                                                                                     |
| Interface configuration errors | Many things can be misconfigured on an interface to cause it to go down, such as incorrect clock rate, incorrect clock source, and interface not being turned on. This causes a loss of connectivity with attached network segments.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Exceeding design limits   | A component may be operating sub-optimally at the physical layer because it is being utilized beyond specifications or configured capacity. When troubleshooting this type of problem, it becomes evident that resources for the device are operating at or near the maximum capacity and there is an increase in the number of interface errors.                                                                                                                                                                                                                                                                                                                                                                                                 |
| CPU overload              | Symptoms include processes with high CPU utilization percentages, input queue drops, slow performance, SNMP timeouts, no remote access, or services such as DHCP, Telnet, and ping are slow or fail to respond. On a switch the following could occur: spanning tree reconvergence, EtherChannel links bounce, UDLD flapping, IP SLAs failures. For routers, there could be no routing updates, route flapping, or HSRP flapping. One of the causes of CPU overload in a router or switch is high traffic. If one or more interfaces are regularly overloaded with traffic, consider redesigning the traffic flow in the network or upgrading the hardware. |



### Data Link Layer

| Symptom                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|--------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| No functionality or connectivity at the network layer or above | Some Layer 2 problems can stop the exchange of frames across a link, while others only cause network performance to degrade.                                                                                                                                                                                                                                                                                                                                                                    |
| Network is operating below baseline performance levels | There are two distinct types of suboptimal Layer 2 operation that can occur in a network. First, the frames take a suboptimal path to their destination but do arrive causing the network to experience unexpected high-bandwidth usage on links. Second, some frames are dropped as identified through error counter statistics and console error messages that appear on the switch or router. An extended or continuous ping can help reveal if frames are being dropped. |
| Excessive broadcasts                        | Operating systems use broadcasts and multicasts extensively to discover network services and other hosts. Generally, excessive broadcasts are the result of a poorly programmed or configured applications, a large Layer 2 broadcast domain, or an underlying network problem (e.g., STP loops or route flapping).                                                                                                                                                                            |
| Console messages                           | A router recognizes that a Layer 2 problem has occurred and sends alert messages to the console. Typically, a router does this when it detects a problem with interpreting incoming frames (encapsulation or framing problems) or when keepalives are expected but do not arrive. The most common console message that indicates a Layer 2 problem is a line protocol down message.                                                                                                         |


| Problem Cause         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Encapsulation errors  | An encapsulation error occurs because the bits placed in a field by the sender are not what the receiver expects to see. This condition occurs when the encapsulation at one end of a WAN link is configured differently from the encapsulation used at the other end.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Address mapping errors| In topologies, such as point-to-multipoint or broadcast Ethernet, it is essential that an appropriate Layer 2 destination address be given to the frame. This ensures its arrival at the correct destination. To achieve this, the network device must match a destination Layer 3 address with the correct Layer 2 address using either static or dynamic maps. In a dynamic environment, the mapping of Layer 2 and Layer 3 information can fail because devices may have been specifically configured not to respond to ARP requests, the Layer 2 or Layer 3 information that is cached may have physically changed, or invalid ARP replies are received because of a misconfiguration or a security attack. |
| Framing errors        | Frames usually work in groups of 8-bit bytes. A framing error occurs when a frame does not end on an 8-bit byte boundary. When this happens, the receiver may have problems determining where one frame ends, and another frame starts. Too many invalid frames may prevent valid keepalives from being exchanged. Framing errors can be caused by a noisy serial line, an improperly designed cable (too long or not properly shielded), faulty NIC, duplex mismatch, or an incorrectly configured channel service unit (CSU) line clock.                                                                                                                                                                                                                      |
| STP failures or loops | The purpose of the Spanning Tree Protocol (STP) is to resolve a redundant physical topology into a tree-like topology by blocking redundant ports. Most STP problems are related to forwarding loops that occur when no ports in a redundant topology are blocked and traffic is forwarded in circles indefinitely. This causes excessive flooding because of a high rate of STP topology changes. A topology change should be a rare event in a well-configured network. When a link between two switches goes up or down, there is eventually a topology change when the STP state of the port is changing to or from forwarding. However, when a port is flapping (oscillating between up and down states), this causes repetitive topology changes and flooding, or slow STP convergence or re-convergence. This can be caused by a mismatch between the real and documented topology, a configuration error, such as an inconsistent configuration of STP timers, an overloaded switch CPU during convergence, or a software defect. |


## Network Layer

| Symptom             | Description                                                                                                                                                                                                                                               |
|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Network failure     | Network failure is when the network is nearly or completely non-functional, affecting all users and applications on the network. These failures are usually noticed quickly by users and network administrators and are obviously critical to the productivity of a company. |
| Suboptimal performance | Network optimization problems usually involve a subset of users, applications, destinations, or a type of traffic. Optimization issues can be difficult to detect and even harder to isolate and diagnose. This is because they usually involve multiple layers, or even a single host computer. Determining that the problem is a network layer problem can take time. |


| Problem Cause       | Description                                                                                                                                                                                                                                                                                                                                                       |
|---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| General network issues | Often a change in the topology, such as a down link, may have effects on other areas of the network that might not be obvious at the time. This may include the installation of new routes, static or dynamic, or removal of other routes. Determine whether anything in the network has recently changed, and if there is anyone currently working on the network infrastructure. |
| Connectivity issues | Check for any equipment and connectivity problems, including power problems such as outages and environmental problems (for example, overheating). Also check for Layer 1 problems, such as cabling problems, bad ports, and ISP problems.                                                                                                                         |
| Routing table      | Check the routing table for anything unexpected, such as missing routes or unexpected routes. Use debug commands to view routing updates and routing table maintenance.                                                                                                                                                                                            |
| Neighbor issues    | If the routing protocol establishes an adjacency with a neighbor, check to see if there are any problems with the routers forming neighbor adjacencies.                                                                                                                                                                                                            |
| Topology database  | If the routing protocol uses a topology table or database, check the table for anything unexpected, such as missing entries or unexpected entries.                                                                                                                                                                                                                 |


## Transport Layer - ACL
| Misconfigurations                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Selection of traffic flow         | Traffic is defined by both the router interface through which the traffic is traveling and the direction in which this traffic is traveling. An ACL must be applied to the correct interface, and the correct traffic direction must be selected to function properly.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Order of access control entries   | The entries in an ACL should be from specific to general. Although an ACL may have an entry to specifically permit a type of traffic flow, packets never match that entry if they are being denied by another entry earlier in the list. If the router is running both ACLs and NAT, the order in which each of these technologies is applied to a traffic flow is important. Inbound traffic is processed by the inbound ACL before being processed by outside-to-inside NAT. Outbound traffic is processed by the outbound ACL after being processed by inside-to-outside NAT.                                                                                                                                                 |
| Implicit deny any                 | When high security is not required on the ACL, this implicit access control element can be the cause of an ACL misconfiguration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Addresses and IPv4 wildcard masks | Complex IPv4 wildcard masks provide significant improvements in efficiency but are more subject to configuration errors. An example of a complex wildcard mask is using the IPv4 address 10.0.32.0 and wildcard mask 0.0.32.15 to select the first 15 host addresses in either the 10.0.0.0 network or the 10.0.32.0 network.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Selection of transport layer protocol | When configuring ACLs, it is important that only the correct transport layer protocols be specified. Many network administrators, when unsure whether a type of traffic flow uses a TCP port or a UDP port, configure both. Specifying both opens a hole through the firewall, possibly giving intruders an avenue into the network. It also introduces an extra element into the ACL, so the ACL takes longer to process, introducing more latency into network communications.                                                                                                                                                                                                                                                                              |
| Source and destination ports      | Properly controlling the traffic between two hosts requires symmetric access control elements for inbound and outbound ACLs. Address and port information for traffic generated by a replying host is the mirror image of address and port information for traffic generated by the initiating host.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Use of the established keyword    | The established keyword increases the security provided by an ACL. However, if the keyword is applied incorrectly, unexpected results may occur.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Uncommon protocols                | Misconfigured ACLs often cause problems for protocols other than TCP and UDP. Uncommon protocols that are gaining popularity are VPN and encryption protocols.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

## Transport Layer - NAT

| Protocol                        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| BOOTP and DHCP                  | Both protocols manage the automatic assignment of IPv4 addresses to clients. Recall that the first packet that a new client sends is a DHCP-Request broadcast IPv4 packet. The DHCP-Request packet has a source IPv4 address of 0.0.0.0. Because NAT requires both a valid destination and source IPv4 address, BOOTP and DHCP can have difficulty operating over a router running either static or dynamic NAT. Configuring the IPv4 helper feature can help solve this problem.                                                                 |
| DNS                             | Because a router running dynamic NAT is changing the relationship between inside and outside addresses regularly as table entries expire and are recreated, a DNS server outside the NAT router does not have an accurate representation of the network inside the router. Configuring the IPv4 helper feature can help solve this problem.                                                                                                                                                                                                 |
| SNMP                            | Like DNS packets, NAT is unable to alter the addressing information stored in the data payload of the packet. Because of this, an SNMP management station on one side of a NAT router may not be able to contact SNMP agents on the other side of the NAT router. Configuring the IPv4 helper feature can help solve this problem.                                                                                                                                                                                                                   |
| Tunneling and encryption protocols | Encryption and tunneling protocols often require that traffic be sourced from a specific UDP or TCP port, or use a protocol at the transport layer that cannot be processed by NAT. For example, IPsec tunneling protocols and generic routing encapsulation protocols used by VPN implementations cannot be processed by NAT.                                                                                                                                                                                                                     |


## Application Layer
| Applications            | Description                                                                                                                                                                                                                                                                                                                                                             |
|-------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SSH/Telnet              | Enables users to establish terminal session connections with remote hosts.                                                                                                                                                                                                                                                                                               |
| HTTP                    | Supports the exchanging of text, graphic images, sound, video, and other multimedia files on the web.                                                                                                                                                                                                                                                                     |
| FTP                     | Performs interactive file transfers between hosts.                                                                                                                                                                                                                                                                                                                       |
| TFTP                    | Performs basic interactive file transfers typically between hosts and networking devices.                                                                                                                                                                                                                                                                                |
| SMTP                    | Supports basic message delivery services.                                                                                                                                                                                                                                                                                                                                |
| POP                     | Connects to mail servers and downloads email.                                                                                                                                                                                                                                                                                                                            |
| SNMP                    | Collects management information from network devices.                                                                                                                                                                                                                                                                                                                    |
| DNS                     | Maps IP addresses to the names assigned to network devices.                                                                                                                                                                                                                                                                                                              |
| Network File System (NFS) | Enables computers to mount drives on remote hosts and operate them as if they were local drives. Originally developed by Sun Microsystems, it combines with two other application layer protocols, external data representation (XDR) and remote-procedure call (RPC), to allow transparent access to remote network resources. |



## Troubleshoot IP COnnectivity

***Verify problem***
- IPv4 ping

- IPv4 traceroute - The tracert command is used with Windows operating systems. If the data fails at some hop along the way, the address of the last router that responded to the trace is known. This address is an indication of where the problem or security restrictions reside.

- IPv6 ping and traceroute

***When there is no end-to-end connectivity, and the administrator chooses to troubleshoot with a bottom-up approach, the following are common steps the administrator can take:***

- Step 1. Check physical connectivity at the point where network communication stops. This includes cables and hardware. The problem might be with a faulty cable or interface, or involve misconfigured or faulty hardware.
    - The most commonly used Cisco IOS commands for this purpose are show processes cpu, show memory, and show interfaces. This topic discusses the show interfaces command.
    - Input queue drops: more traffic was delivered to the router than it could process.it could be an indication that the CPU cannot process packets in time, so if this number is consistently high, it is worth trying to spot at which moments these counters are increasing and how this relates to CPU usage.
    - Output queue drops:  packets were dropped due to congestion on the interface.
    - Input errors: CRC errors. High numbers of CRC errors could indicate cabling problems, interface hardware problems, or, in an Ethernet-based network, duplex mismatches.
    - Output errors: collisions (especially late collisions) often indicate duplex mismatches

- Step 2. Check for duplex mismatches.
    - Using the show interfaces fa 0/20 command, the network administrator examines the interface. The network administrator corrects the setting to duplex auto to automatically negotiate the duplex. Because the port on S1 is set to full-duplex, S2 also uses full-duplex.


- Step 3. Check data link and network layer addressing on the local network. This includes IPv4 ARP tables, IPv6 neighbor tables, MAC address tables, and VLAN assignments.
    - Windows IPv4 ARP Table: arp -a to view entries and arp -d to clear cache.
    - Windows IPv6 Neighbor Table: netsh interface ipv6 show neighbor
    - IOS IPv6 Neighbor Table: show ipv6 neighbors
    - Switch MAC Address Table: show mac address-table (view vlan assignment)


- Step 4. Verify that the default gateway is correct.
    - R1# show ip route | include Gateway|0.0.0.0
    - C:\> route print (for windows)
Step 5. Ensure that devices are determining the correct path from the source to the destination. Manipulate the routing information if necessary.
Step 6. Verify the transport layer is functioning properly. Telnet can also be used to test transport layer connections from the command line.
Step 7. Verify that there are no ACLs blocking traffic.
Step 8. Ensure that DNS settings are correct. There should be a DNS server that is accessible.