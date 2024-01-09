# 2.3 Configure and verify Layer 2 discovery protocols (Cisco Discovery Protocol and LLDP)
# 4.2 Configure and verify NTP operating in a client and server mode

# 4.5 Describe the use of syslog features including facilities and levels

# Network Management
## Cisco Discovery Protocol
Layer 2. Discover cisco devices, their names and type of interfaces. Send advertisements periodically.
By default, CDP messages are sent once every 60 seconds.
By default, the CDP holdtime is 180 seconds. If a message isn’t received from a neighbor for 180 seconds, the neighbor is removed from the CDP neighbor table.
CDP messages are periodically sent to multicast MAC address 0100.0CCC.CCCC.
### Configure and verify
- cdp run
- no cdp run
- show cdp: global info such as time and version
- show cdp traffic: number of packets transmitted

To disable or enable on specifici interfaces:
- int g0/0
- cdp enable or no cdp enable

view:
- show cdp neighbors: neighbors
- show cdp neighbors detail: vtp, vlan and duplex info, ip address
- show cdp interface: for only cdp enabled interfaces
- show cdp entry R2: specific device

Device identifiers - This is the host name of the neighbor device (S1).
Port identifier - This is the name of the local and remote port (G0/0/1 and F0/5, respectively).
Capabilities list - This shows whether the device is a router or a switch (S for switch; I for IGMP is beyond scope for this course)
Platform - This is the hardware platform of the device (WS-C3560 for Cisco 3560 switch).

The network administrator uses show cdp neighbors detail to discover the IP address for S1

- R1(config)# cdp timer seconds
- R1(config)# cdp holdtime seconds
  

## Link Layer Discovery Protocol
Same as CDP but vendor-neutral
LLDP messages are periodically sent to multicast MAC address 0180.C200.000E.

LLDP messages are sent once every 30 seconds.
By default, the LLDP holdtime is 120 seconds.
LLDP has an additional timer called the ‘reinitialization delay’. If LLDP is enabled (globally or on an interface), this timer will delay the actual initialization of LLDP. 2 seconds by default.

### Configure and Verify
- lldp run
- no lldp run
- lldp timer seconds
- lldp holdtime seconds
- lldp reinit seconds

Specific interface
- int g0/0
- lldp transmit
- lldp receive

verify
- show lldp
- show lldp neighbors
- show lldp neighbors detail
- show lldp traffic
- show lldp entry R2

in LLDP, the switch is shown as Bridge
## NEtwork Time Protocol
Configure date and time on devices

Manually configure without ntp
- R1# clock set 16:01:00 sept 25 2020 

NTP will allow all devices to sync their time rather than manually configure each device.
NTP uses UDP port 123

NTP networks use a hierarchical system of time sources. Each level in this hierarchical system is called a stratum. The stratum level is defined as the number of hop counts from the authoritative source. The synchronized time is distributed across the network by using NTP. The figure displays a sample NTP network.

NTP servers are arranged in three levels showing the three strata. Stratum 1 is connected to Stratum 0 clocks.
Smaller stratum numbers indicate that the server is closer to the authorized time source than larger stratum numbers. The larger the stratum number, the lower the stratum level. The max hop count is 15. Stratum 16, the lowest stratum level, indicates that a device is unsynchronized. Time servers on the same stratum level can be configured to act as a peer with other time servers on the same stratum level for backup or verification of time.

### Configure and verify
- first check clock
    - R1# show clock detail 
20:55:10.207 UTC Fri Nov 15 2019
Time source is user configuration

- configure ntp server
    - R1(config)# ntp server 209.165.200.225 
R1(config)# end 
R1# show clock detail 
21:01:34.563 UTC Fri Nov 15 2019
Time source is NTP

- use ntp association and ntp status to verify
    - R1# show ntp associations   
  address         ref clock       st   when   poll reach  delay  offset   disp
*~209.165.200.225 .GPS.           1     61     64   377  0.481   7.480  4.261
 
R1# show ntp status 
Clock is synchronized, stratum 2, reference is 209.165.200.225

- configure switch with router ip as ntp
    - S1(config)# ntp server 192.168.1.1
S1(config)# end

### extra info
A router has hardware clock and software clock. The hardware clock can be set using the calendar command: "calendar set 16:01:00 sept 25 2020".
***synchronize clock and calendar***
Use the command clock update-calendar to sync the calendar to the clock’s time.
Use the command clock read-calendar to sync the clock to the calendar’s time.

***set timezone:*** R2(config)#clock timezone JST 9

***set Daylight Saving Time (Summer):*** R1(config)# clock summer-time recurring name start end [offset]

can configure multiple ntp servers and use the ***"prefer" ***command at the end to specify preference.

***update calendar after ntp config:*** R1(config)#ntp update-calendar

***configure loopback address of router as source for other routers to sync:***
R1(config)#interface loopback0
R1(config-if)#ip address 10.1.1.1 255.255.255.255
R1(config-if)#exit
R1(config)#ntp source loopback0

***configure device as ntp master:*** R1(config)#ntp master ?
default stratum for ntp master is 8 so it should show as 7

***configure peers:*** R2(config)#ntp peer 10.0.23.2 and "" 10.0.23.1 on other end.

***NTP Authentication***
ntp authenticate
ntp authentication-key key-number md5 key
ntp trusted-key key-number
ntp server ip-address key key-number (not for the server but other devices)
R2(config)#ntp authenticate
R2(config)#ntp authentication-key 1 md5 jeremysitlab
R2(config)#ntp trusted-key 1
R2(config)#ntp server 10.0.12.1 key 1
R2(config)#ntp peer 10.0.23.2 key 1

## Simple Network Management Protocol
SNMP is an application layer protocol that provides a message format for communication between managers and agents. The SNMP system consists of three elements:

SNMP manager
SNMP agents (managed node)
Management Information Base (MIB)

The SNMP manager can collect information from an SNMP agent by using the “get” action and can change configurations on an agent by using the “set” action. In addition, SNMP agents can forward information directly to a network manager by using “traps”.

### SNMP Operations
- get-request:Retrieves a value from a specific variable.

- get-next-request: Retrieves a value from a variable within a table; the SNMP manager does not need to know the exact variable name. A sequential search is performed to find the needed variable from within a table.

- get-bulk-request: Retrieves large blocks of data, such as multiple rows in a table, that would otherwise require the transmission of many small blocks of data. (Only works with SNMPv2 or later.)

- get-response: Replies to a get-request, get-next-request, and set-request sent by an NMS.

- set-request: Stores a value in a specific variable.

The SNMP agent responds to SNMP manager requests as follows:

Get an MIB variable - The SNMP agent performs this function in response to a GetRequest-PDU from the network manager. The agent retrieves the value of the requested MIB variable and responds to the network manager with that value.
Set an MIB variable - The SNMP agent performs this function in response to a SetRequest-PDU from the network manager. The SNMP agent changes the value of the MIB variable to the value specified by the network manager. An SNMP agent reply to a set request includes the new settings in the device.

### SNMP Agent Traps
To mitigate these disadvantages, it is possible for SNMP agents to generate and send traps to inform the NMS immediately of certain events. Traps are unsolicited messages alerting the SNMP manager to a condition or event on the network. Examples of trap conditions include, but are not limited to, improper user authentication, restarts, link status (up or down), MAC address tracking, closing of a TCP connection, loss of connection to a neighbor, or other significant events. Trap-directed notifications reduce network and agent resources by eliminating the need for some of SNMP polling requests.

### SNMP Version
SNMPv1 - This is the Simple Network Management Protocol, a Full Internet Standard, that is defined in RFC 1157.
SNMPv2c - This is defined in RFCs 1901 to 1908. It uses a community-string-based Administrative Framework.
SNMPv3 - This is an interoperable standards-based protocol originally defined in RFCs 2273 to 2275. It provides secure access to devices by authenticating and encrypting packets over the network. It includes these security features: message integrity to ensure that a packet was not tampered with in transit, authentication to determine that the message is from a valid source, and encryption to prevent the contents of a message from being read by an unauthorized source.


SNMPv1 is the original version of the protocol and provides the most basic functionality required for data polling without using significant resources. However, SNMPv1 has very basic security and doesn’t include any encryption algorithms. SNMPv2c is nearly identical to SNMPv1, except for different version number in the encoding, new data type(s), and Get-Bulk requests that are not supported by SNMPv1. SNMPv3 is the most recent version and offers advanced security features, including authentication and encryption, to protect SNMP communication
## Syslog
Accessing System Messages. Syslog uses UDP port 514 to send event notification messages across IP networks to event message collectors.

The syslog logging service provides three primary functions, as follows:
- The ability to gather logging information for monitoring and troubleshooting
- The ability to select the type of logging information that is captured
- The ability to specify the destinations of captured syslog messages

On Cisco network devices, the syslog protocol starts by sending system messages and debug output to a local logging process that is internal to the device.

As shown in the figure, popular destinations for syslog messages include the following:

- Logging buffer (RAM inside a router or switch)
- Console line
- Terminal line
- Syslog server

Levels:
Each syslog level has its own meaning:

- Warning Level 4 - Emergency Level 0: These messages are error messages about software or hardware malfunctions; these types of messages mean that the functionality of the device is affected. The severity of the issue determines the actual syslog level applied.
- Notification Level 5: This notifications level is for normal, but significant events. For example, interface up or down transitions, and system restart messages are displayed at the notifications level.
- Informational Level 6: This is a normal information message that does not affect device functionality. For example, when a Cisco device is booting, you might see the following informational message: %LICENSE-6-EULA_ACCEPT_ALL: The Right to Use End User License Agreement is accepted.
- Debugging Level 7: This level indicates that the messages are output generated from issuing various debug commands.

Some common syslog message facility codes reported on Cisco IOS routers include:

IF - Identifies that the syslog message was generated by an interface.
IP - Identifies that the syslog message was generated by IP.
OSPF - Identifies that the syslog message was generated by the OSPF routing protocol.
SYS - Identifies that the syslog message was generated by the device operating system.
IPSEC - Identifies that the syslog message was generated by the IP Security encryption protocol.
By default, the format of syslog messages on the Cisco IOS Software is as follows:

%facility-severity-MNEMONIC: description 
For example, sample output on a Cisco switch for an EtherChannel link changing state to up is:

%LINK-3-UPDOWN: Interface Port-channel1, changed state to up

### COnfigure syslog timestamp
use the command service timestamps log datetime to force logged events to display the date and time. As shown in the command output, when the R1 GigabitEthernet 0/0/0 interface is reactivated, the log messages now contain the date and time.

R1(config)# service timestamps log datetime



## File Maintenance

### ROuter
The Cisco IOS File System (IFS) allows the administrator to navigate to different directories and list the files in a directory.

- show file systems
    - This command provides useful information such as the amount of total and free memory, the type of file system, and its permissions. Permissions include read only (ro), write only (wo), and read and write (rw). The permissions are shown in the Flags column of the command output.

- dir 
    - command for current directory items

- cd nvram
    - pwd to view current directory and then dir to view its contents

### Switch
- show file systems

### Backup COnfiguration
Configuration files can be saved to a text file by using Tera Term
- Step 1. On the File menu, click Log.
- Step 2. Choose the folder location and filename to save the file and click Save. Tera Term will open Tera Term: Log window and will now capture all commands and output generated in the terminal window.
- Step 3. To capture the current configuration, enter the show running-config or show startup-config command privileged EXEC command. The text displayed in the terminal window will also be directed to the chosen file.
- Step 4. When the capture is complete, select Close in the Tera Term: Log window.
- Step 5. Open the file to verify that the configuration was captured properly and not corrupt.

### Restore COnfiguration
A configuration can be copied from a file and then directly pasted to a device. The IOS executes each line of the configuration text as a command. This means that the file will require editing to ensure that encrypted passwords are in plaintext, and that non-command text such as --More-- and IOS messages are removed. In addition, you may want to add enable and configure terminal to the beginning of the file or enter global configuration mode before pasting the configuration. This process is discussed in the lab later is this topic.

Instead of copying and pasting, a configuration can be restored from a text file by using Tera Term

- Step 1. On the File menu, click Send file.
- Step 2. Locate the file to be copied into the device and click Open.
- Step 3. Tera Term will paste the file into the device.

### TFTP to backup and restore
- R1# copy running-config tftp
Remote host []?192.168.10.254
Name of the configuration file to write[R1-config]? R1-Jan-2019
Write file R1-Jan-2019 to 192.168.10.254? [confirm]
Writing R1-Jan-2019 !!!!!! [OK]

### usb
- verify usb is there: show file systems
- R1# copy running-config usbflash0: 
- check contents: R1# dir usbflash0:/ 
- restore: copy usbflash0:/R1-Config running-config

## Password Recovery
- Step 1. Enter the ROMMON mode.

With console access, a user can access the ROMMON mode by using a break sequence during the boot up process or removing the external flash memory when the device is powered off. When successful, the rommon 1 > prompt displays, as shown in the example.

Note: The break sequence for PuTTY is Ctrl+Break. A list of standard break key sequences for other terminal emulators and operating systems can be found by searching the internet.

- Step 2. Change the configuration register.

The ROMMON software supports some basic commands, such as confreg. The confreg 0x2142 command allows the user to set the configuration register to 0x2142. With the configuration register at 0x2142, the device will ignore the startup config file during startup. The startup config file is where the forgotten passwords are stored. After setting the configuration register to 0x2142, type reset at the prompt to restart the device. 

- Step 3. Copy the startup-config to the running-config.

After the device has finished reloading, copy the startup config to the running config by using the copy startup-config running-config command, as displayed in the example.

- Step 4. Change the password.
- Step 5. Save the running-config as the new startup-config.

R1(config)# config-register 0x2102
R1(config)# end
R1# copy running-config startup-config


- Step 6. Reload the device.

R1(config)# config-register 0x2102
R1(config)# end
R1# copy running-config startup-config

### Managing IOS Cisco Image
- ping tftp
    - R1# ping 172.16.1.100
- verify image size
    - R1# show flash0: 
- copy image to tftp
    - R1# copy flash: tftp: 
Source filename []? isr4200-universalk9_ias.16.09.04.SPA.bin
Address or name of remote host []? 172.16.1.100
Destination filename [isr4200-universalk9_ias.16.09.04.SPA.bin]? 

- or copy ios to flash
    - R1# copy tftp: flash: 
Address or name of remote host []?2001:DB8:CAFE:100::99
Source filename []?  isr4200-universalk9_ias.16.09.04.SPA.bin
Destination filename [isr4200-universalk9_ias.16.09.04.SPA.bin]? 

- selec file as boot file
    - R1# configure terminal
R1(config)# boot system flash0:isr4200-universalk9_ias.16.09.04.SPA.bin
R1(config)# exit
R1#
R1# copy running-config startup-config
R1#
R1# reload
Proceed with reload? [confirm] 