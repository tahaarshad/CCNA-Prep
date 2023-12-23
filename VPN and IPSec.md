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

# IPSec
Protects and authenticates IP packets between source and destination.
## FUnctions
- Protocol: The choices for IPsec Protocol include Authentication Header (AH) or Encapsulation Security Protocol (ESP). AH authenticates the Layer 3 packet. ESP encrypts the Layer 3 packet.
- Confidentiality: Layer 3 packet. Choices include Data Encryption Standard (DES), Triple DES (3DES), Advanced Encryption Standard (AES), or Software-Optimized Encryption Algorithm (SEAL). No encryption is also an option.
- Integrity: hash algorithm, such as message-digest 5 (MD5) or Secure Hash Algorithm (SHA).Hashed Message Authentication Code (HMAC)
- Authentication: IPsec uses Internet Key Exchange (IKE) to authenticate users and devices that can carry out communication independently. IKE uses several types of authentication, including username and password, one-time password, biometrics, pre-shared keys (PSKs), and digital certificates using the Rivest, Shamir, and Adleman (RSA) algorithm.
- Diffie-Hellman: IPsec uses the DH algorithm to provide a public key exchange method for two peers to establish a shared secret key. There are several different groups to choose from including DH14, 15, 16 and DH 19, 20, 21 and 24. DH1, 2 and 5 are no longer recommended.

When establishing a VPN link, the peers must share the same SA to negotiate key exchange parameters, establish a shared key, authenticate each other, and negotiate the encryption parameters. Notice that SA Example 1 is using no encryption.

AH does not provide Confidentiality
