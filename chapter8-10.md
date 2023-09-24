# Implementing VLANs and STP

## Chapter 8

> Basic VLAN concept

a broadcast sent by one host in a VLAN 
will be received and processed by all the other hosts in the VLAN—but not by hosts in a 
different VLAN. Limiting the number of hosts that receive a single broadcast frame reduces 
the number of hosts that waste effort processing unneeded broadcasts

> Reasons for using VLANs

■ To reduce CPU overhead on each device, improving host performance, by reducing the 
number of devices that receive each broadcast frame
■ To reduce security risks by reducing the number of hosts that receive copies of frames 
that the switches flood (broadcasts, multicasts, and unknown unicasts)
■ To improve security for hosts through the application of different security policies per 
VLAN
■ To create more flexible designs that group users by department, or by groups that work 
together, instead of by physical location
■ To solve problems more quickly, because the failure domain for many problems is the 
same set of devices as those in the same broadcast domain
■ To reduce the workload for the Spanning Tree Protocol (STP) by limiting a VLAN to a 
single access switch

> Diagram of VLAN trunking

When SW2 receives the frame, it understands that the frame is in VLAN 10. SW2 then removes 
the VLAN header, forwarding the original frame out its interfaces in VLAN 10 (Step 3).
For another example, consider the case when PC21 (in VLAN 20) sends a broadcast. 
SW1 sends the broadcast out port Fa0/4 (because that port is in VLAN 20) and out Gi0/1 
(because it is a trunk, meaning that it supports multiple different VLANs). SW1 adds a 
trunking header to the frame, listing a VLAN ID of 20. SW2 strips off the trunking header 
after determining that the frame is part of VLAN 20, so SW2 knows to forward the frame 
out only ports Fa0/3 and Fa0/4, because they are in VLAN 20, and not out ports Fa0/1 and 
Fa0/2, because they are in VLAN 10.

> 802.1Q header



Options of the switchport mode command

Expected trunking results based on the configuration of the 
switchport mode command

Definitions of data VLAN and voice VLAN

Summary of data and voice VLAN concepts, configuration, and 
verification

Analysis of the three VLAN lists in the output from the show 
interfaces interface-id trunk command