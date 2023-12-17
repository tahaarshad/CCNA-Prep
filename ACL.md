# Access Control Lists
Packet Filtering
- Standard = Operate on Layer 3
- Extended = Layer 3 for IP Filtering and Layer 4 for TCP/UDP Filtering

## Operation
Inbound ACL and Outbound ACL
- Packet arrives at the inbound interface
- Router read all AC Entries in the ACL from top to bottom
- Once match is made, the action is performed and the rest ACE are not analyzed
- If no match, then the packet is discarded because an implicit deny is applied.

## Wildcard Mask
Same as OSPF
- For host = 0.0.0.0
- For subnet = 0.0.0.255
- For address range = 0.0.15.255

Example: In this example, assume you needed an ACE in ACL 10 to permit only networks 192.168.10.0 and 192.168.11.0. These two networks could be summarized as 192.168.10.0/23 which is a subnet mask of 255.255.254.0. Again, you subtract 255.255.254.0 subnet mask from 255.255.255.255, as shown in the table.

This solution produces the wildcard mask 0.0.1.255. Therefore, the ACE would be access-list 10 permit 192.168.10.0 0.0.1.255.

### How to Summarize
Here’s how you can do it:

Convert the network addresses to binary:

192.168.10.0: 11000000.10101000.00001010.00000000
192.168.11.0: 11000000.10101000.00001011.00000000
Determine the common prefix: The first 23 bits are common to both addresses, which gives us the summarized network address of 192.168.10.0 with a subnet mask of 255.255.254.0.

Calculate the new subnet mask:

Original subnet mask for each network: 255.255.255.0 (or /24 in CIDR notation)
New subnet mask for the summarized network: 255.255.254.0 (or /23 in CIDR notation)
Verify the summary:

The summarized network 192.168.10.0/23 includes all IP addresses from 192.168.10.0 to 192.168.11.255.

### Keywords
host = replace for 0.0.0.0 mask. Match one host
any = replace for 255.255.255.255. Any Address range
