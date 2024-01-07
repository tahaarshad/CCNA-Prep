# 1.2.d WAN


# Wide Area Network
## Logical Topologies
- Point-to-point : dedicated leased line
- Hub and Spoke : Multiple spoke router connected through a single hub router.
- Dual Homed : Hub and Spoke but with 2 hub routers for redundancy
- Fully Meshed: all routers connected to each other
- Paritally meshed: not all sites are connected to each other

## Carrier Connections
How an organization connects to the internet as specified in the SLA.
- Single carrier: connect to one service provider
- Dual Carrier: seperate slas with different service providers

## Evolution
Small > campus > branch > distributed

## WAN Standards
Managed by 3 organization:
- TIA/EIA - Telecommunications Industry Association and Electronic Industries Alliance
- ISO - International Organization for Standardization
- IEEE - Institute of Electrical and Electronics Engineers

## OSI Model
Layer 1 Optical Fiber Standards
- Synchronous Digital Hierarchy (SDH)
- Synchronous Optical Networking (SONET)
- Dense Wavelength Division Multiplexing (DWDM)

Layer 2 Protocols
Broadband (i.e., DSL and Cable)
Wireless
Ethernet WAN (Metro Ethernet)
Multiprotocol Label Switching (MPLS)
Point-to-Point Protocol (PPP) (less used)
High-Level Data Link Control (HDLC) (less used)
Frame Relay (legacy)
Asynchronous Transfer Mode (ATM) (legacy)

## WAN Terms
- DTE - Data Terminal Equipment - Link between LAN and WAN
- DCE - Data Communications Equipment - Communicates with the provider
- CPE - Customer Premises Equipment - All DTE and DCE are here
- POP - Point of Presence - The point where subscriber connects to the service provider network
- Demarcation Point - Physical location that seprate CPE and service provider equipment
- Local Loop - Line that connects CPE to CO
- Central Office - Service Provider facility
- Toll Network - all communication devices inside the WAN provider network
- Backhaul network - these networks connect multiple access nodes to the service provider network
- Backbone Network - high capacity network to create redundancy

## Devices
- Voiceband Modem
- DSL Cable Modem
- CSU/DSU - connects digital device to digital line
- Optical COnverter
- WAP/Router
- WAN COre devices

## Serial and Parallel Communication
Serial is data that is sent sequentially where parallel are multiple bits of data trasferred at the same time through multiple channels and then syncronised.

## Circuit Switched Communication
This network establishes a dedicated circuit when communicating between endpoints. It uses the same path for the whole communication. Not suited for data communication.
- PSTN limit the rate of the signal to less than 56 kbps
- ISDN provides for data rates from 45 Kbps to 2.048 Mbps.

## Packet Switched COmmunication
Used in network communication. Data is divided into packets and sent across a shared network without any dedicated line. MPLS is example.
- Frame Relay: support data rates up to 4 Mbps
- ATM cells are always a fixed length of 53 bytes
- Ethernet WAN - Using optical fiber and replacing the upper two technologies.
- Multiprotocol Label Switching (MPLS) is a high-performance service provider WAN routing technology to interconnect clients without regard to access method or payload.

## Optical Fiber Standards
- SDH - Synchronous Digital Hierarchy (SDH) is a global standard for transporting data over fiber-optic cable.
- SONET - Synchronous Optical Networking (SONET) is the North American standard that provides the same services as SDH.
- Dense Wavelength Division Multiplexing (DWDM) is a newer technology that increases the data-carrying capacity of SDH and SONET by simultaneously sending multiple streams of data (multiplexing) using different wavelengths of light. 80 channels, 10Gbps each.

## Leased Serial Lines
- T-carrier - Used in North America, T-carrier provides T1 links supporting bandwidth up to 1.544 Mbps and T3 links supporting bandwidth up to 43.7 Mbps.
- E-carrier – Used in Europe, E-carrier provides E1 links supporting bandwidth up to 2.048 Mbps and E3 links supporting bandwidth up to 34.368 Mbps.

Simplicity, quality availablity but costly and limited flexibility.

## Internet Based Connectivity
- DSL: A Digital Subscriber Line (DSL) is a high-speed, always-on, connection technology that uses existing twisted-pair telephone lines to provide IP services to users. 
Point to point protocol over ethernet. Either with host or router having the PPPoE client.
- Cable Technology: Using coaxial cable.

- Fiber Technology
  - Fiber to the Home (FTTH) - Fiber reaches the boundary of the residence. Passive optical networks and point-to-point Ethernet are architectures that can deliver cable TV, internet, and phone services over FTTH networks directly from an the service provider central office.
  - Fiber to the Building (FTTB) - Fiber reaches the boundary of the building, such as the basement in a multi-dwelling unit, with the final connection to the individual living space being made via alternative means, like curb or pole technologies.
  - Fiber to the Node/Neighborhood (FTTN) – Optical cabling reaches an optical node that converts optical signals to a format acceptable for twisted pair or coaxial cable to the premise.
  
- Wireless
  - Municipal Wi-Fi
  - Cellular
  - Satellite Internet
  - WiMAX

- VPN: site to site or remote access

## ISP Connectivity Option
- Single Homes
- DUal Homed - two links to one isp
- Multi Homed - one link to two isp each
- Dual Multihomed

## Comparison
Some factors to consider include the following:

Cable - Bandwidth is shared by many users. Therefore, upstream data rates are often slow during high-usage hours in areas with over-subscription.
DSL - Limited bandwidth that is distance sensitive (in relation to the ISP central office). Upload rate is proportionally lower compared to download rate.
Fiber-to-the-Home - This option requires fiber installation directly to the home.
Cellular/Mobile - With this option, coverage is often an issue, even within a small office or home office where bandwidth is relatively limited.
Municipal Wi-Fi - Most municipalities do not have a mesh Wi-Fi network deployed. If is available and in range, then it is a viable option.
Satellite - This option is expensive and provides limited capacity per subscriber. Typically used when no other option is available.

Private WAN infrastructure - such as dedicated point-to-point leased lines, PSTN, ISDN, Ethernet WAN, ATM, or Frame Relay
Public WAN infrastructure - such as digital subscriber line (DSL), cable, satellite access, municipal Wi-Fi, WiMAX, or wireless cellular including 3G/4G