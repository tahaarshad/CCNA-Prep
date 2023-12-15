# OSPF Concept

Improvement over RIP protocol that does not only use the hop count to decide the best possible path to transfer packets.

Some characteristics of OSPF:
Link-state protocol: Networks are divided into domains known as areas for updating routing traffic. Interfaces on routers are known as Links. So are network segments. Information on these links is called link-state. this includes network prefix, prefix length and cost.

Interior Gateway Protocol: Designed to be used withing a single automonous system such as an organization with multiple departments.

Classless: Classless networks include subnet masks in their routing updates. Classful do not as they all are in the same subnet.

Cost of Path depends on Bandwidth: uses formula cost = reference bandwidth/interface bandwidth

other: Dijkstra algorithm
Builds topological map
Event-driven updates
Hierarchical design
Requires additional memory, CPU processing, and more initial bandwidth than other protocols

## Component

5 types of packets are exchanged:
- Hello - Type 1
- database description - Type 2
- LS Request - Type 3
- LS Update - Type 4
- LS Ack - Type 5
  

## Databases and Tables

3 databases store 3 different tables:
- Adjacency DB stores neighbor table - contain adjacent routers. Can be viewed using show ip ospf neighbor
- Link State db store topology table - contains all routers in an area. Can be viewed using show ip ospf database. SPF algorithm is run here
- Routing db stores forwarding table - stores routes generated from the algorithm. Can be viewed using show ip route


## 5 steps to building routing table

- Establish adjacencies by sending hello packets
- Send LS Advertisements to all nearby router
- Once every router has sent each other LSA's, then the LSDB is created
- The algorithm is exevuted
- Best route is selected

## Area

Single Area OSPF routers exist in one domain - Area 0

Multi Area have multiple domains with one backbone (Area 0). Area Border ROuters exist on the edge of each domain.

Several Advantages:
- Reduced SPF calculations
- Smaller tables
- Reduces LSU overhead


## OSPFv3

v3 is the IPv6 equivaltent of OSPFv2 which is for IPv4. Similar characteristincs and functions.


## Important Packet Information

LSU contains upto 11 differents LSA packets with different information such as routers, network etc.

Type 1 packets elect the DR and BDR. multiaccess connections like ethernet require DR and BDR but point ot point networks to do not.


## 7 OSPF States

- Down - no hello packets. Once packet is sent, move to init.
- Init - hello packet contain router id. transistion to 2 way.
- 2-way - bidirectional communications. DR and BDR are eleced.
- exstart - on ptp connection, routers will decide which one will send BDB first.
- exchange - once elected, DBD is shared.
- loading - LSR and LSU are exchanges, SPF is run. then change to full
- full - fully synchronised.


### OSPF Multicast address - 224.0.0.5