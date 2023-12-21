# NAT Configuration

## Static
- Create mapping:
- -  R2(config)# ip nat inside source static 192.168.10.254 209.165.201.5
- Specify inside and outside interface
- - R2(config)# interface serial 0/1/0
R2(config-if)# ip address 192.168.1.2 255.255.255.252
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface serial 0/1/1
R2(config-if)# ip address 209.165.200.1 255.255.255.252
R2(config-if)# ip nat outside

### Verify
- show ip nat translations: Only shows mappings
- show ip nat statistics: active translations, interfaces and stats
- clear ip nat statistics: when testing with a new connection

## Dynamic
- Define pool: starting address, ending address, netmast.
- - R2(config)# ip nat pool NAT-POOL1 209.165.200.226 209.165.200.240 netmask 255.255.255.224
- create ACL to permit the translated address
- - R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
- Bind ACL to pool
- - R2(config)# ip nat inside source list 1 pool NAT-POOL1
- identify inside interface
- - R2(config)# interface serial 0/1/0
R2(config-if)# ip nat inside
- indentify outside outside interface
- - R2(config)# interface serial 0/1/1
R2(config-if)# ip nat outside

### Verify
R2# show ip nat translations
R2# show ip nat translation verbose
- translation entries timeout after 24 hrs. This can be changed using:
- ip nat translation timeout timeout-seconds
  
To clear dynamic entries, use clear ip nat transation:
- clear ip nat translation * - clears all
- clear ip nat translation insideglobal-ip local-ip [outside local-ip global-ip] - clears a simple entry containing an inside entry or both inside and out
- clear ip nat translation protocolinsideglobal-ip global-port local-ip local-port [ outsidelocal-ip local-port global-ip global-port] - Clears an extended dynamic translation entry.

Show ip nat statistics for displaying information
Show running config | include nat

