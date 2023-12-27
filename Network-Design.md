# Network Design
The Cisco Borderless Network is a network architecture that combines innovation and design. It allows organizations to support a borderless network that can connect anyone, anywhere, anytime, on any device; securely, reliably, and seamlessly. This architecture is designed to address IT and business challenges, such as supporting the converged network and changing work patterns.

### Principles:
- Hierarchical - The design facilitates understanding the role of each device at every tier, simplifies deployment, operation, and management, and reduces fault domains at every tier.
- Modularity - The design allows seamless network expansion and integrated service enablement on an on-demand basis.
- Resiliency - The design satisfies user expectations for keeping the network always on.
- Flexibility - The design allows intelligent traffic load sharing by using all network resources.

## Layers
- Access Layer
The access layer represents the network edge, where traffic enters or exits the campus network. Traditionally, the primary function of an access layer switch is to provide network access to the user. Access layer switches connect to distribution layer switches, which implement network foundation technologies such as routing, quality of service, and security.
- Distribution Layer
The distribution layer interfaces between the access layer and the core layer to provide many important functions including Aggregating large-scale wiring closet networks
Aggregating Layer 2 broadcast domains and Layer 3 routing boundaries
Providing intelligent switching, routing, and network access policy functions to access the rest of the network
Providing high availability through redundant distribution layer switches to the end user, and equal cost paths to the core
Providing differentiated services to various classes of service applications at the edge of the network
- Core Layer
The core layer is the network backbone. It connects several layers of the campus network. The core layer serves as the aggregator for all of the distribution layer devices and ties the campus together with the rest of the network. The primary purpose of the core layer is to provide fault isolation and high-speed backbone connectivity.

## 3 Tier and 2 Tier Examples
- Three-Tier Example

The figure shows a three-tier campus network design for organizations where the access, distribution, and core are each separate layers. To build a simplified, scalable, cost-effective, and efficient physical cable layout design, the recommendation is to build an extended-star physical network topology from a centralized building location to all other buildings on the same campus.

- Two-Tier Example

In some cases where extensive physical or network scalability does not exist, maintaining separate distribution and core layers is not required. In smaller campus locations where there are fewer users accessing the network, or in campus sites consisting of a single building, separate core and distribution layers may not be needed. In this scenario, the recommendation is the alternate two-tier campus network design, also known as the collapsed core network design.

## Scalable Networks
Scalability is the term for a network that can grow without losing availability and reliability.
- To support a large, medium or small network, the network designer must develop a strategy to enable the network to be available and to scale effectively and easily.
- Use expandable, modular equipment, or clustered devices that can be easily upgraded to increase capabilities.
- Design a hierarchical network to include modules that can be added, upgraded, and modified, as necessary, without affecting the design of the other functional areas of the network.
- Create an IPv4 and IPv6 address strategy that is hierarchical.
- Choose routers or multilayer switches to limit broadcasts and filter other undesirable traffic from the network. Use Layer 3 devices to filter and reduce traffic to the network core.

### Design Requirements
- Redundant Links
    - Reduce domain failure size
- Multiple Links
    - Increase Bandwidth
- Scalable Routing Protocol
    - Tune Routing Protocols
- Wireless Connectivity
    - Expand the Access Layer

