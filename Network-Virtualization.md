# Network Virtualization

## Cloud Computing
Pay-as-you-go-model

***Services***
- Software as a Service (SaaS) - The cloud provider is responsible for access to applications and services, such as email, communication, and Office 365 that are delivered over the internet. The user does not manage any aspect of the cloud services except for limited user-specific application settings. The user only needs to provide their data.
- Platform as a Service (PaaS) - The cloud provider is responsible for providing users access to the development tools and services used to deliver the applications. These users are typically programmers and may have control over the configuration settings of the cloud provider’s application hosting environment.
- Infrastructure as a Service (IaaS) - The cloud provider is responsible for giving IT managers access to the network equipment, virtualized network services, and supporting network infrastructure. Using this cloud service allows IT managers to deploy and run software code, which can include operating systems and applications.
- Cloud service providers have extended this model to also provide IT support for each of the cloud computing services (ITaaS), as shown in the figure. For businesses, ITaaS can extend the capability of the network without requiring investment in new infrastructure, training new personnel, or licensing new software. These services are available on demand and delivered economically to any device anywhere in the world without compromising security or function.

***Models***
Public,Private, Hybrid, Community

### Virtualization
Virtualization separates the operating system (OS) from the hardware

Pros:
less equipments, energy, space

Benfits:
Easier prototyping, faster provisioning, increased uptime, imrpoved disaster recovery, legacy support.

### Type 2 Hypervisor
A Type 2 hypervisor is software that creates and runs VM instances.

### Type 1 Hypervisor
the hypervisor is installed directly on the hardware.
Type 1 hypervisors require a “management console” to manage the hypervisor. Management software is used to manage multiple servers using the same hypervisor. The management console can automatically consolidate servers and power on or off servers as required. Can move an instance from one server to another. Overallocation is usually performed because at any given time, the resources are not utilized under their full capacity.

### Virtual Networking
Network functions can be virtualized. Each network device can be segmented into multiple virtual devices that operate as independent devices. Examples include subinterfaces, virtual interfaces, VLANs, and routing tables. Virtualized routing is called virtual routing and forwarding (VRF).

### Software Defined Networking
Terms: Network Programming, SDN, Controllers

- Control Plane: the brains of a device. It is used to make forwarding decisions. The control plane contains Layer 2 and Layer 3 route forwarding mechanisms, such as routing protocol neighbor tables and topology tables, IPv4 and IPv6 routing tables, STP, and the ARP table. Information sent to the control plane is processed by the CPU.
- Data Plane: Also called the forwarding plane, this plane is typically the switch fabric connecting the various network ports on a device. The data plane of each device is used to forward traffic flows. 

***Cisco Express FOrwardind***
CEF is an advanced, Layer 3 IP switching technology that enables forwarding of packets to occur at the data plane without consulting the control plane. In CEF, the control plane’s routing table pre-populates the CEF Forwarding Information Base (FIB) table in the data plane. The control plane’s ARP table pre-populates the adjacency table. Packets are then forwarded directly by the data plane based on the information contained in the FIB and adjacency table, without needing to consult the information in the control plane.

***Management Plane***
Is responsible for managing a device through its connection to the network. Network administrators use applications such as Secure Shell (SSH), Trivial File Transfer Protocol (TFTP), Secure FTP, and Secure Hypertext Transfer Protocol (HTTPS) to access the management plane and configure a device.

### Technologies
***Architectures***
- Software-Defined Networking (SDN) - A network architecture that virtualizes the network, offering a new approach to network administration and management that seeks to simplify and streamline the administration process.
- Cisco Application Centric Infrastructure (ACI) - A purpose-built hardware solution for integrating cloud computing and data center management.

Components of SDN:

- OpenFlow - This approach was developed at Stanford University to manage traffic between routers, switches, wireless access points, and a controller. The OpenFlow protocol is a basic element in building SDN solutions. Search for OpenFlow and the Open Networking Foundation for more information.
- OpenStack - This approach is a virtualization and orchestration platform designed to build scalable cloud environments and provide an IaaS solution. OpenStack is often used with Cisco ACI. Orchestration in networking is the process of automating the provisioning of network components such as servers, storage, switches, routers, and applications. Search for OpenStack for more information.
- Other components - Other components include Interface to the Routing System (I2RS), Transparent Interconnection of Lots of Links (TRILL), Cisco FabricPath (FP), and IEEE 802.1aq Shortest Path Bridging (SPB).


***Note*** a traditional router or switch architecture, the control plane and data plane functions occur in the same device. Routing decisions and packet forwarding are the responsibility of the device operating system. In SDN, management of the control plane is moved to a centralized SDN controller.
The SDN controller uses northbound APIs to communicate with the upstream applications. These APIs help network administrators shape traffic and deploy services. The SDN controller also uses southbound APIs to define the behavior of the data planes on downstream switches and routers. OpenFlow is the original and widely implemented southbound API.

The figure illustrates the complete SDN framework. The figure has three sections: the application layer, control plane and data plane. At the application layer, there are business applications, cloud orchestration, and SDN applications. At the control plane, there is the SDN controller. The SDN controller is providing routing, traffic engineering and mobility. Between the application layer and the control are arrows indicating the Northbound APIs used to communicate between the SDN and applications. The data plane has a hub and spoke topology of eight routers and switches. Between the control plane and the data plane is an arrow indicating the Southbound APIs used between the SDN and the routers and switches.

## SDN Controllers
The SDN controller defines the data flows between the centralized control plane and the data planes on individual routers and switches.

Each flow traveling through the network must first get permission from the SDN controller, which verifies that the communication is permissible according to the network policy. If the controller allows a flow, it computes a route for the flow to take and adds an entry for that flow in each of the switches along the path.

All complex functions are performed by the controller. The controller populates flow tables. Switches manage the flow tables.

Flow Table - This table matches incoming packets to a particular flow and specifies the functions that are to be performed on the packets. There may be multiple flow tables that operate in a pipeline fashion.
Group Table - A flow table may direct a flow to a Group Table, which may trigger a variety of actions that affect one or more flows
Meter Table - This table triggers a variety of performance-related actions on a flow including the ability to rate-limit the traffic.

## Cisco ACI
Cisco developed the Application Centric Infrastructure (ACI) to meet these objectives in more advanced and innovative ways than earlier SDN approaches.

Cisco ACI is a hardware solution for integrating cloud computing and data center management. At a high level, the policy element of the network is removed from the data plane. This simplifies the way data center networks are created.

***Components of the ACI architecture:***

- Application Network Profile (ANP) - An ANP is a collection of end-point groups (EPG), their connections, and the policies that define those connections. The EPGs shown in the figure, such as VLANs, web services, and applications, are just examples. An ANP is often much more complex.
- Application Policy Infrastructure Controller (APIC) - The APIC is considered to be the brains of the ACI architecture. APIC is a centralized software controller that manages and operates a scalable ACI clustered fabric. It is designed for programmability and centralized management. It translates application policies into network programming.
- Cisco Nexus 9000 Series switches - These switches provide an application-aware switching fabric and work with an APIC to manage the virtual and physical network infrastructure.

***Spine-Leaf Topology***
The Cisco ACI fabric is composed of the APIC and the Cisco Nexus 9000 series switches using two-tier spine-leaf topology, as shown in the figure. The leaf switches always attach to the spines, but they never attach to each other. Similarly, the spine switches only attach to the leaf and core switches (not shown). In this two-tier topology, everything is one hop from everything else.

The Cisco APICs and all other devices in the network physically attach to leaf switches.

***SDN Types***
- Controller-based SDN: In this type of SDN, the devices are programmable by applications running on the device itself or on a server in the network.
- Policy-based SDN: his type of SDN uses a centralized controller that has knowledge of all devices in the network.
- Device-based SDN: This type of SDN is similar to controller-based SDN where a centralized controller has a view of all devices in the network. Policy-based SDN includes an additional Policy layer that operates at a higher level of abstraction. It uses built-in applications that automate advanced configuration tasks via a guided workflow and user-friendly GUI.

***APIC-EM Features***
Each type of SDN has its own features and advantages. Policy-based SDN is the most robust, providing for a simple mechanism to control and manage policies across the entire network.

Cisco APIC-EM is an example of policy-based SDN. Cisco APIC-EM provides a single interface for network management including:

discovering and accessing device and host inventories,
viewing the topology,
tracing a path between end points, and
setting policies.

APIC-EM Path Trace
The APIC-EM Path Trace tool allows the administrator to easily visualize traffic flows and discover any conflicting, duplicate, or shadowed ACL entries. This tool examines specific ACLs on the path between two end nodes, displaying any potential issues. You can see where any ACLs along the path either permitted or denied your traffic,
