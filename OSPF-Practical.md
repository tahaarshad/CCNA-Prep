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

