# ACL Configuration

## Standard ACL Syntax
### Numbered
Router(config)# access-list access-list-number {deny | permit | remark text} source [source-wildcard] [log]

- Use the no access-list access-list-number global configuration command to remove a numbered standard ACL.
- source wildcard is optional
- log keyword generates a message when ACE is matched

### Named
Router(config)# ip access-list standard access-list-name

### Apply to interface
Router(config-if) # ip access-group {access-list-number | access-list-name} {in | out}

### Example

- ACE
- R1(config)# access-list 10 remark ACE permits ONLY host 192.168.10.10 to the internet
R1(config)# access-list 10 permit host 192.168.10.10
R1(config)# do show access-lists
Standard IP access list 10
    10 permit 192.168.10.10
R1(config)#

- Apply to outbound interface
- R1(config)# interface Serial 0/1/0
R1(config-if)# ip access-group 10 out
R1(config-if)# end
R1#

### Named
R1(config)# no access-list 10
R1(config)# ip access-list standard PERMIT-ACCESS
R1(config-std-nacl)# remark ACE permits host 192.168.10.10
R1(config-std-nacl)# permit host 192.168.10.10
R1(config-std-nacl)#

## Modify
R1# conf t
R1(config)# ip access-list standard 1
R1(config-std-nacl)# no 10
R1(config-std-nacl)# 10 deny host 192.168.10.10
R1(config-std-nacl)# end
R1# show access-lists
Standard IP access list 1
    10 deny   192.168.10.10
    20 permit 192.168.10.0, wildcard bits 0.0.0.255
R1#

## MOdify ACL using Sequence Number
- Each ACE in an ACL has a sequence number automatically assigned
- R1# conf t
R1(config)# ip access-list standard 1
R1(config-std-nacl)# no 10
R1(config-std-nacl)# 10 deny host 192.168.10.10
R1(config-std-nacl)# end
R1# show access-lists
Standard IP access list 1
    10 deny   192.168.10.10
    20 permit 192.168.10.0, wildcard bits 0.0.0.255
R1#

- Assume that host 192.168.10.5 from the 192.168.10.0/24 network should also have been denied. If you entered a new ACE, it would be appended to the end of the ACL. Therefore, the host would never be denied because ACE 20 permits all hosts from that network.

The solution is to add an ACE denying host 192.168.10.5 in between ACE 10 and ACE 20, such as ACE 15, as shown in the example. Also notice that the new ACE was entered without using the host keyword. The keyword is optional when specifying a destination host.

Use the show access-lists command to verify the ACL now has a new ACE 15 inserted appropriately before the permit statement.

Notice that sequence number 15 is displayed prior to sequence number 10. We might expect the order of the statements in the output to reflect the order in which they were entered. However, the IOS puts host statements in an order using a special hashing function. The resulting order optimizes the ACL to search by host entries first, and then by network entries.

## Securing VTY Ports
R1(config-line)# access-class {access-list-number | access-list-name} { in | out } 

### Example
R1(config)# username ADMIN secret class
R1(config)# ip access-list standard ADMIN-HOST
R1(config-std-nacl)# remark This ACL secures incoming vty lines
R1(config-std-nacl)# permit 192.168.10.10
R1(config-std-nacl)# deny any
R1(config-std-nacl)# exit
R1(config)# line vty 0 4
R1(config-line)# login local
R1(config-line)# transport input telnet
R1(config-line)# access-class ADMIN-HOST in
R1(config-line)# end
R1#

In a production environment, you would set the vty lines to only allow SSH, as shown in the example.

R1(config)# line vty 0 4
R1(config-line)# login local
R1(config-line)# transport input ssh
R1(config-line)# access-class ADMIN-HOST in
R1(config-line)# end
R1#

## Extended ACL
Also have both numbered and named ACL

Router(config)# access-list access-list-number {deny | permit | remark text} protocol source source-wildcard [operator {port}] destination destination-wildcard [operator {port}] [established] [log]

- operator (optional) - compares source or destination ports. lt,gt,eq,neq
- established (optional) - TCP only. Used in 1st Gen FW

Can use either port name or port number

### Established Keyword
TCP can also perform basic stateful firewall services using the TCP established keyword. The keyword enables inside traffic to exit the inside private network and permits the returning reply traffic to enter the inside private network


R1(config)# access-list 120 permit tcp any 192.168.10.0 0.0.0.255 established
R1(config)# interface g0/0/0 
R1(config-if)# ip access-group 120 out 
R1(config-if)# end
R1# show access-lists 
Extended IP access list 110
     10 permit tcp 192.168.10.0 0.0.0.255 any eq www
     20 permit tcp 192.168.10.0 0.0.0.255 any eq 443 (657 matches)
Extended IP access list 120
     10 permit tcp any 192.168.10.0 0.0.0.255 established (1166 matches)
R1#

### Named
Router(config)# ip access-list extended access-list-name 

### Editing
Same as standard. Remove ACE with the sequence number.
R1(config)# ip access-list extended SURFING 
R1(config-ext-nacl)# no 10
R1(config-ext-nacl)# 10 permit tcp 192.168.10.0 0.0.0.255 any eq www


## Verify
- show access-lists
- show running-config
- show ip interface


## ACL Resequencing
The command is ip access-list resequence acl-id starting-seq-num increment


## Important Port numbers
TCP
● FTP data (20)
● FTP control (21)
● SSH (22)
● Telnet (23)
● SMTP (25)
● HTTP (80)
● POP3 (110)
● HTTPS (443)
UDP
● DHCP server (67)
● DHCP client (68)
● TFTP (69)
● SNMP agent (161)
● SNMP manager (162)
● Syslog (514)
TCP & UDP
● DNS (53)
