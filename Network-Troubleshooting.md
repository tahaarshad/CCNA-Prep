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




