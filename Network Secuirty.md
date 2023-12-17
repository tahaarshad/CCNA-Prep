# Network Security

## Terms
- Asset = Something of vlue
- Threat = A potential danger to the asset.
- Vulnerability = A defect in the system that can be used by attackers.
- Exploit = mechanism by which the vulnerability be used
- Mitigation = counter measure
- Risk = likelihood of vulnerability being exploited

## Vectors
- Internal and External

## Hackers
- White = Ethical hackers
- Gray = Perform unethical actions but inform the company later.
- Black = Unethical Hackers

## Tools
- Password Crackers
- Wireless Hacking
- Network Scanning and Hacking
- Packet Crafting - Testing firewall
- Packet Sniffers
- Rootkit Detectors
- Fuzzers to Search Vulnerabilities
- Forensic Tools
- Debuggers - for reverse engineering
- Hacking OS
- Encryption Tools
- Vulnerability Exploitation Tools
- Vulnerability Scanners

## Attack Types
- Eavesdropping
- Data Modification
- IP Spoofing
- Password-Based
- DoS
- MitM
- Compromised Key
- Sniffer

### Trojan Horses - Act like legitemate applications but perform various actions behind the scenes

### Rootkits are used to gain admin level access to computers

## Common Attacks
- Reconnaissance
- Access
- Social Engineering
- Amplification and reflection attacks	Threat actors attempt to prevent legitimate users from accessing information or services using DoS and DDoS attacks.


## TCP Control Bits

6 bits that indicate:
- URG - Urgent pointer field significant
- ACK - Acknowledgment field significant
- PSH - Push function
- RST- Reset the connection
- SYN - Synchronize sequence numbers
- FIN - No more data from sender

## TCP Attacks
- TCP SYN Flood - Results in the legitimate use unable to access the web server
- TCP RST Attack - Causing aprubt disruption of connection between endpoints
- TCP Session Hijacking - Performed by spoofing IP and predicting the next sequence number. He can send data but not receive

## UDP Attacks
UDP Flood - Result is very similar to DoS Attack. After spoofing the IP address of the host, a flood UDP packets are sent to the server and the server has to reply with ICMP host unreachable for the closed ports. And there are a lot of closed ports usually. Therefore, a lot bandwidth is used in the process.

## ARP Poisoning
- Threat Actor can send a gratitous ARP reply with its MAC address and redirect traffic to his PC.
- Passive = Only viewing information
- Active = Modifying data and injecting malicious code

## DNS Attacks
- DNS Open Resolver Attacks - Open Resover provide responses to queries, so they can be trageted by cache poisoning, amplification and reflection, resource ultilization.
- DNS Stealth - Continuously changing IP addressing and Domain names to prevent being detected.
- Domain Shadowing - Gaining credentials and creating sub domains for illicit purposes wihtout owners knowledge

### DNS Tunneling
- The command data is split into multiple encoded chunks.
- Each chunk is placed into a lower level domain name label of the DNS query.
- Because there is no response from the local or networked DNS for the query, the request is sent to the ISP’s recursive DNS servers.
- The recursive DNS service will forward the query to the threat actor’s authoritative name server.
- The process is repeated until all the queries containing the chunks of are sent.
- When the threat actor’s authoritative name server receives the DNS queries from the infected devices, it sends responses for each DNS query, which contain the encapsulated, encoded CnC commands.
- The malware on the compromised host recombines the chunks and executes the commands hidden within the DNS record.
- Mitigation - To stop DNS tunneling, the network administrator must use a filter that inspects DNS traffic. Pay close attention to DNS queries that are longer than average, or those that have a suspicious domain name. DNS solutions, like Cisco OpenDNS, block much of the DNS tunneling traffic by identifying suspicious domains.

## DHCP Attacks
Through Spoofing
- Wrong default gateway - MiTM
- Wrong DNS - Malicious website
- Wrong IP Address

## Best Practices
Following CIA Triad
- Confidentiality
- Inegrity
- Availability

Defense In-Depth Approach - Multi-layers security infrasturcture utilizing a combination of devices and services

- Firewall
- IPS
- Content Security Appliance = Web and Email

