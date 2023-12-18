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

