# Virtual Private Network
## Benefits
- Cost Savings
- Security
- Scalability
- Compatibility

## Types
- Site to Site: Preconfigured VPN gateways that encrypt the traffic between two branches. End host are not aware of this.
- Remote Access: Dynamically created to establish connection to a VPN gateway.
  - Clientless: HTTPS using SSL
  - CLient-based: Using a software
- SSL VPN:
  - IPsec: Extensive(Supports all types of apps), Strong authentication and encryption, requires pre installed client and only works on certain devices.
  - SSL: On web based products, moderate authentication and encyrption, no installation required, any device with a browser can connect.


## Deployment
- Enterprise VPN: Managed by the enterprise using IPSec and SSL VPN.
- Service Provider: The service provider uses Layer 2 or Layer 3 MPLS to create virtual paths between sites.
    - Layer 3 MPLS VPN - The service provider participates in customer routing by establishing a peering between the customer’s routers and the provider’s routers. Then customer routes that are received by the provider’s router are then redistributed through the MPLS network to the customer’s remote locations.
    - Layer 2 MPLS VPN - The service provider is not involved in the customer routing. Instead, the provider deploys a Virtual Private LAN Service (VPLS) to emulate an Ethernet multiaccess LAN segment over the MPLS network. No routing is involved. The customer’s routers effectively belong to the same multiaccess network.

## GRE over IPSec
Generic Routing ENcapsulation is non-secure site to stie vpn protocol that supports multicast and broadcast traffic. IPsec is only unicast.
So to share routing information such as OSPF over the network securely, first encapsulate the packet with GRE and then encapsulate it with IPSec to forward it to the VPN gateway.
- Passenger protocol - original packet
- Carrier - GRE
- Transport - IPSec

## Dynamic Multipoint VPN
Upper solution are hard to maintain when multiple sites require it. So DMVPN is used.
IPSec is used and configuration is in hub and spoke manner. Each site is configured with Multipoint GRE. SPokes can create virtual spoke to spoke tunnels.

