# OSPF Practical

### Wildcard mask = subtract subnet mask from 255.255.255.255

## Network Command

- conf t
- router opsf 10
- network 10.1.2.0 0.0.0.4 area 0

## Quad zero mask

- netwokr 10.10.2.1 0.0.0.0 area 0

## IP ospf command

- router ospf 10
- interface g0/0/0
- ip ospf 10 area 0

## remove config
- no network 10.0.1.0 0.0.0.0 area 0

### end


## Passive-interface

- passive-interface loopback 0
- router ospf 10

## Interface priority

- interface g0/0/0
- ip ospf priority 255
- end

clear ip ospf process

## Debug
debug ip ospf adj

## Adjust reference bandwidth
- auto-cost reference-bandwith Mbps
- for gigbit "" 1000
- for 10gig "" 10000
- for default "" 100

## Manually configure cost
- int g0/0/0
- ip ospf cost 30

## hello and dead interval
- ip ospf hello/dead-interval (seconds)

## Deafault route
- int lo1
- ip address 10.2.12.3 255.255.255.0
- exit
- ip route 0.0.0.0 0.0.0.0 lo1
- router ospf 10
- deault-information originate
- end

## Verify

- show ip interface brief = correct ip addressing
- show ip route = correct routing table
- show ip ospf neighbor = adjacencies
- show ip protocols = ospf cofig
- show ip ospf = ospf info
- show ip ospf interface = interface details


## Exam Feedback 

Each interface on the link connecting the OSPF routers must be in the same subnet for an adjacency to be established. The IP address subnet mask on FastEthernet interface 0/0 must be changed to 255.255.255.0. The FastEthernet interface 0/0 is not passive. The 10.0.1.0/24 network is only connected to Router2 so should not be advertised by Router1. The clear ip ospf process command will start the OPSF process on Router1 but will not cause an adjacency to be established if the subnet mask mismatch on the connecting interfaces still exists.

ntering the command network 192.168.1.1 0.0.0.0 area 0 will turn on only the interface with that IP address for OSPF routing. It does not change the router ID. Instead, OSPF will use the network that is configured on that interface.

ff a LAN network is not advertised using OSPFv2, a remote network will not be reachable. The output displays a successful neighbor adjacency between router R1 and R2 on the interface S0/0 of both routers.

The command show ip ospf interface verifies the active OSPF interfaces. The command show ip interface brief is used to check that the interfaces are operational. The command show ip route ospf displays the entries that are learned via OSPF in the routing table. The command show ip protocol s checks that OSPF is enabled and lists the networks that are advertised.

The show ip ospf interface serial 0/0/0 command will display the configured hello and dead timer intervals on a point-to-point serial WAN link between two OSPFv2 routers. The show ipv6 ospf interface serial 0/0/0 command will display the configured hello and dead timer intervals on a point-to-point serial link between two OSPFv3 routers. The show ip ospf interface fastethernet 0/1 command will display the configured hello and dead timer intervals on a multiaccess link between two (or more) OSPFv2 routers. The show ip ospf neighbor command will display the dead interval elapsed time since the last hello message was received, but does not show the configured value of the timer.

OSPF router ID does not contribute to SPF algorithm calculations, nor does it facilitate the transition of the OSPF neighbor state to Full. Although the router ID is contained within OSPF messages when router adjacencies are being established, it has no bearing on the actual convergence process.