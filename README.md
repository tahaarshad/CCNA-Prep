# CCNA-Prep

## Network Fundamentals
> Explain the role and function of network components

### Routers
Enables interconnection between networks.

**Useful Commands**
`show ip route`
shows all routes.
**(S*)** means static - manually configured.

### Layer 2 and Layer 3 Switches
Enables intterconnection between devices inside a network.

Switches reside in Layer-2 but Layer-3 switches also possess routing capabilities.

**Useful Commands**
`show mac address-table`
shows all connected devices.

### Next Generation Firewalls and IPS
These are secuirty appliances that inspect network traffic enforce network security policies in order to protect the network from threats.
Next Gen FW reside in Layer 7.
They perform deep packet inspection that can be useful in tasks such as viewing bandwidth usage.

IPS (Intrusion Prevention System) - A proactive system that detects and responds to threats. Can even inspect encrypted traffic.

IPS Sensors - A standalone appliance.

### Access Points
Enable wireless devices to gain access to a wired network or the internet.
*Mesh Wireless LAN* - Receives a signal and regenerates it for broadccast.

**A wireless LAN controller is configured to manage multiple access points.** - WLC

### Endpoint and Servers
Endpoint devices request for services whereas servers provide services
(Client-server and peer-to-peer architecture)

### Cisco DNA Center
Cisco's centralized network management and orchestration tool. It uses AI and machine learning to proactively manage and troubleshoot network issues.
Design, add, configure, monitor, troubleshoot, assurance, policy, provision.

### Explain virtualization fundamentals (server virtualization, containers, and VRFs)
This technology allows you to create multiple simulated environments or dedicated resources from a single physical hardware system. It's used to optimize resource usage and create flexible and scalable network architectures.
<br>
**Server Virtualization**
<br>
Hypervisor = Software that can create, start, stop and monitor virtual machines.
- Type-1  = Native or Baremetal  - Runs directly on the hardware.
- Type-2 = Hosted - Runs on the OS.

A virtual switch (vSwitch) is a software-based switch that allows virtual machines (VMs) to communicate with each other and with the physical network. A virtual network interface controller (vNIC) is a software-based network adapter that is used to connect a VM to a vSwitch.

Virtual switches are created on the hypervisor host, which is the physical machine that runs the VMs. Virtual switches can be configured to support different types of networks, such as bridged networks, isolated networks, and private networks.

Bridged networks allow VMs to communicate with each other and with the physical network as if they were connected to the same physical switch. Isolated networks allow VMs to communicate with each other, but they are isolated from the physical network. Private networks allow VMs to communicate with each other and with the hypervisor host, but they are isolated from the physical network and from other VMs.

**Container**

Containers are a way of isolating and managing applications. They are similar to virtual machines, but they share the same operating system kernel. This makes them more lightweight and efficient than virtual machines.
Containers are often used to deploy microservices, which are small, self-contained applications. Microservices can be easily scaled and deployed, making them ideal for cloud-based applications.
(Refer to Adrian Cantril Docker Fundamentals)

**VRF**

<br>

> Describe characteristics of network topology architectures

**Two-tier**

**Three-tier**
**Spine-leaf**
**WAN**
**Small office/home office (SOHO)**
**On-premise and cloud**
