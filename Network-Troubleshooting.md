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

