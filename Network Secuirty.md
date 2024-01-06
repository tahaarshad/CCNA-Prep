# 5.1 Define key security concepts (threats, vulnerabilities, exploits, and mitigation techniques)

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

### Trojan Horses - Act like legitemate applications but perform various actions behind the scenes. Worms are standable. Do not require host.

***Watering hole attacks compromise sites that the target victim frequently visits. If a malicious link is placed 
on a website the target trusts, they might not hesitate to click it.***

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

## Cryptography
### Data integrity
- MD5 128-bit
- SHA-1 160-bit
- SHA-2 = 224, 256, 384 and 512 bits
- SHA-3 = 224, 256, 384 and 512 bits

### Orign Auth
- HMAC - Keyed Hash Message Authentication Code
- The hash value and secret key are used to create this code.

### Confidentiality
Symmetric Key - One Key for all
- DES, 3DES, AES, SEAL, RC

Assymetric - public and private keys = SSL, SSH
- DH, DSS, DSA, RSA


## Extra
5.2 Describe security program elements (user awareness, training, and physical access control)
5.4 Describe security password policies elements, such as management, complexity, and 
password alternatives (multifactor authentication, certificates, and biometrics)
5.8 Compare authentication, authorization, and accounting concepts

***Multi-factor authentication ***
involves providing more than just a username/password to prove your identity.
● It usually involves providing two of the following (=two-factor authentication):
● Something you know
→ a username/password combination, a PIN, etc.
● Something you have
→ pressing a notification that appears on your phone, a badge that is scanned, etc.
● Something you are
→ biometrics

****Digital certificates****
another form of authentication used to prove the identity of the holder of the 
certificate.
● They are used for websites to verify that the website being accessed is legitimate.
● Entities that want a certificate to prove their identity send a CSR (Certificate Signing Request) to a CA (Certificate Authority), which will generate and sign the certificate

***AAA (triple-A)***
stands for Authentication, Authorization, and Accounting.
● It is a framework for controlling and monitor users of a computer system (ie. a network).
● Authentication is the process of verifying a user’s identity.
→ logging in = authentication
● Authorization is the process of granting the user the appropriate access and permissions.
→ granting the user access to some files/services, restricting access to other files/services = authorization
● Accounting is the process of recording the user’s activities on the system.
→ logging when a user makes a change to a file = accounting
● Enterprises typically use a AAA server to provide AAA services.

***Security Program Elements***
**User awareness** programs are designed to make employees aware of potential security threats and risks.
→ For example, a company might send out false phishing emails to make employees click a link and sign in 
with their login credentials.
**User training** programs are more formal than user awareness programs.
→ For example, dedicated training sessions which educate users on the corporate security policies, how to 
create strong passwords, and how to avoid potential threats.
**Physical access control** protects equipment and data from potential attackers by only allowing authorized 
users into protected areas such as network closets or data center floors.