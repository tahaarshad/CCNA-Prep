# Network Address Translation
Private addresses are translated to a public ip address becuase of the lack of ipv4 public ip addresses available.

## Terms
- Inside local address
- inside global address
- outside local address
- outside global address


## Types
- Static: One to one mapping
- Dynamic: First come first serve basis from a pool of available public IP addresses.

## Port Address Translation
- NAT Overload.
- Maps multiple private addresses to the one or few public addresses by adding a port number to uniquely identify each session.

### Next Available Port
Possiblity of the port being already used, so the global port number is changed to the next available port.

Some protocols dont use ports, e.g ICMPv4. So it uses QueryID to identify the session.

### Notes
he forwarding delays caused by the NAT process becomes more of an issue as the pools of public IPv4 addresses for ISPs become depleted. Many ISPs are having to assign customers a private IPv4 address instead of a public IPv4 address. This means the customer's router translates the packet from its private IPv4 address to the private IPv4 address of the ISP. Before forwarding the packet to another provider, the ISP will then perform NAT again, translating its private IPv4 addresses to one of its limited number of public IPv4 addresses. This process of two layers of NAT translation is known as Carrier Grade NAT (CGN).


If a private ip is already mapped to a public ip in static nat, then a new command that maps a different private ip to the same public ip will be rejected.

clear ip nat translations only clears dynamic translations, THe static ones remain.


Private IP Ranges
10.0.0.0/8 (10.0.0.0 to 10.255.255.255) - class a
172.16.0.0/12 (172.16.0.0 to 172.31.255.255) - class b
192.168.0.0/16 (192.168.0.0 to 192.168.255.255) - class c


the subnet of private and public addresses in dynamic nat needs to be same. 

default timeout is 24hrs for dynamic entries
other protocol entries are cleared after 1 minute
all entries are cleared when clear command is used.

view access list in show ip nat statistics

the access list does not discard the packet but does not translate them.