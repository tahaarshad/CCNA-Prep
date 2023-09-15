# Implementing Ethernet LAN's

## Chapter 4

### Cisco Switches

Cisco positions the 2960-XR series (family) of switches 
as full-featured, low-cost wiring closet switches for enterprises. That means that you would 
expect to use 2960-XR switches as access switches in a typical campus LAN design. 

To uniquely number each different interface, some Catalyst switches use a two-digit 
interface number (x/y), while others have a three-digit number (x/y/z). For instance, two 
10/100/1000 ports on many older Cisco Catalyst switches would be called GigabitEthernet 
0/0 and GigabitEthernet 0/1, while on the newer 2960-XR series, two interfaces would be 
GigabitEthernet 1/0/1 and GigabitEthernet 1/0/2

>Three methods to access a switch CLI

The switch CLI can be accessed through three popular methods—the console, Telnet, and 
Secure Shell (SSH). Two of these methods (Telnet and SSH) use the IP network in which the 
switch resides to reach the switch. The console is a physical port built specifically to allow 
access to the CLI

Console access requires both a physical connection between a PC (or other user device) and 
the switch’s console port, as well as some software on the PC. Telnet and SSH require software on the user’s device, but they rely on the existing TCP/IP network to transmit data. The 
next few pages detail how to connect the console and set up the software for each method 
to access the CLI

>Cabling options for a console connection

Older console connections use a PC serial port that pre-dates USB, a UTP cable, and an 
RJ-45 console port on the switch, as shown on the left side of Figure 4-3. The PC serial port 
typically has a D-shell connector (roughly rectangular) with nine pins (often called a DB-9). 
The console port looks like any Ethernet RJ-45 port (but is typically colored in blue and 
with the word console beside it on the switch).

The cabling for this older-style console connection can be simple or require some effort, 
depending on what cable you use. You can use the purpose-built console cable that ships 
with new Cisco switches and routers and not think about the details. However, you can make your own cable with a standard serial cable (with a connector that matches the PC), a standard RJ-45 to DB-9 converter plug, and a UTP cable. However, the UTP cable does not use 
the same pinouts as Ethernet; instead, the cable uses rollover cable pinouts rather than any of 
the standard Ethernet cabling pinouts. The rollover pinout uses eight wires, rolling the wire at 
pin 1 to pin 8, pin 2 to pin 7, pin 3 to pin 6, and so on.

As it turns out, USB ports became common on PCs before Cisco began commonly using 
USB for its console ports. So, you also have to be ready to use a PC that has only a USB port 
and not an old serial port, but a router or switch that has the older RJ-45 console port (and 
no USB console port). The center of Figure 4-3 shows that case. To connect such a PC to 
a router or switch console, you need a USB converter that converts from the older console 
cable to a USB connector, and a rollover UTP cable, as shown in the middle of Figure 4-3

The 2960-XR series, for instance, supports both the older RJ-45 console port and a USB 
console port. Figure 4-4 points to the two console ports; you would use only one or the 
other. Note that the USB console port uses a mini-B port rather than the more commonly 
seen rectangular standard USB Type A port.

>A Cisco switch’s default console port settings

The emulator must be configured to use the PC’s serial port to match the settings on the 
switch’s console port settings. The default console port settings on a switch are as follows. 
Note that the last three parameters are referred to collectively as 8N1:
- 9600 bits/second
- No hardware flow control
- 8-bit ASCII
- No parity bits
- 1 stop bit

>Navigation between user, enable, and global config modes

### User Mode

All three CLI access methods covered so far (console, Telnet, and SSH) place the user in 
an area of the CLI called user EXEC mode. User EXEC mode, sometimes also called user 
mode, allows the user to look around but not break anything. The “EXEC mode” part of the 
name refers to the fact that in this mode, when you enter a command, the switch executes 
the command and then displays messages that describe the command’s results.

### Enable Mode

Cisco IOS supports a more powerful EXEC mode called enable mode (also known as privileged mode or privileged EXEC mode). Enable mode gets its name from the enable command, which moves the user from user mode to enable mode, as shown in Figure 4-6. The 
other name for this mode, privileged mode, refers to the fact that powerful (or privileged) 
commands can be executed there. For example, you can use the reload command, which 
tells the switch to reinitialize or reboot Cisco IOS, only from enable mode.

### Configuration Mode

not one of the commands in user or 
privileged mode changes the switch’s configuration. Configuration mode accepts configuration commands—commands that tell the switch the details of what to do and how to do 
it.

>A list of configuration mode prompts, the name of the configuration mode, and the command used to reach each mode


user to enable: enable
enable to user: disable

enable to config: configure terminal
config to enable: end or Crtl+Z



>Configuration mode context-setting commands

Context-setting commands move you from one configuration subcommand mode, or context, to another. These context-setting commands tell the switch the 
topic about which you will enter the next few configuration commands.

For instance, the interface command is one of the most commonly used context-setting configuration commands. For example, the CLI user could enter 
interface configuration mode by entering the interface FastEthernet 0/1 configuration command.
>The names and purposes of the two configuration files in a switch or router

The following list details the four main types of memory found in Cisco switches, as well as 
the most common use of each type:
■ RAM: Working memory and running config

Flash memory: Cisco IOS Sw


■ ROM: Bootstrap program


■ NVRAM: Startp config


startup-config Stores the initial configuration used anytime the 
switch reloads Cisco IOS.

running-config Stores the currently used configuration commands. 
This file changes dynamically when someone enters 
commands in configuration mode.


### Helpful Commands

`>enable`

`>reload`

`>enable secret`

`>show running-config`

`>show mac address-table dynamic`

`>copy running-config startup-config`

<br>

`Switch# configure terminal`

`Switch(config)# hostname Fred`

`Fred(config)# line console 0`

`Fred(config-line)# password hope`

`Fred(config-line)# interface FastEthernet 0/1`

`Fred(config-if)# speed 100`

`Fred(config-if)# exit`

`Fred(config)#`


### Reference Table from Page 103-104
no debug all
undebug all
reload
copy running-config
startup-config
copy startup-config
running-config
show running-config
write erase
erase startup-config
erase nvram:
quit
show startup-config
enable
disable
configure terminal


## Chapter 5

>Three main functions of a LAN switch

LAN switches receive Ethernet frames and then make a switching decision: either forward 
the frame out some other ports or ignore the frame. To accomplish this primary mission, 
switches perform three actions:
1. Deciding when to forward a frame or when to filter (not forward) a frame, based on 
the destination MAC address
2. Preparing to forward frames by learning MAC addresses by examining the source 
MAC address of each frame received by the switch
3. Preparing to forward only one copy of the frame to the destination by creating a 
(Layer 2) loop-free environment with other switches by using Spanning Tree Protocol 
(STP)
The first action is the switch’s primary job, whereas the other two items are overhead 
functions.

>Process to forward a known unicast frame

Switches compare the frame’s destination MAC address to 
this table to decide whether the switch should forward a frame or simply ignore it

A switch’s MAC address table is also called the switching table, or bridging table, 
or even the Content-Addressable Memory (CAM) table, in reference to the type of physical memory used to store the table.


>Process to forward a known unicast, second switch

A switch’s MAC address table lists the location of each MAC relative to that one switch. In 
LANs with multiple switches, each switch makes an independent forwarding decision based 
on its own MAC address table. Together, they forward the frame so that it eventually arrives 
at the destination.

> Unknown Unicast and Boradcast
Now again turn your attention to the forwarding process, using the topology in Figure 5-5. 
What do you suppose the switch does with Fred’s first frame, the one that occurred when 
there were no entries in the MAC address table? As it turns out, when there is no matching 
entry in the table, switches forward the frame out all interfaces (except the incoming interface) using a process called flooding. And the frame whose destination address is unknown 
to the switch is called an unknown unicast frame, or simply an unknown unicast


>Process to learn MAC addresses

Switches build the address table by listening to incoming frames and examining the source 
MAC address in the frame. If a frame enters the switch and the source MAC address is not 
in the MAC address table, the switch creates an entry in the table. That table entry lists the 
interface from which the frame arrived. Switch learning logic is that simple.


>Summary of switch forwarding logic

Step 1. Switches forward frames based on the destination MAC address:

A. If the destination MAC address is a broadcast, multicast, or unknown destination unicast (a unicast not listed in the MAC table), the switch floods the 
frame.

B. If the destination MAC address is a known unicast address (a unicast 
address found in the MAC table):

i. If the outgoing interface listed in the MAC address table is different 
from the interface in which the frame was received, the switch forwards 
the frame out the outgoing interface.

ii. If the outgoing interface is the same as the interface in which the frame 
was received, the switch filters the frame, meaning that the switch simply ignores the frame and does not forward it.

Step 2. Switches use the following logic to learn MAC address table entries:

A. For each received frame, examine the source MAC address and note the 
interface from which the frame was received.

B. If it is not already in the table, add the MAC address and interface it was 
learned on.

Step 3. Switches use STP to prevent loops by causing some interfaces to block, meaning that they do not send or receive frames.

>The show mac address-table dynamic command

To see a switch’s MAC address table, use the show mac address-table command. With 
no additional parameters, this command lists all known MAC addresses in the MAC 
table, including some overhead static MAC addresses that you can ignore. To see all the 
dynamically learned MAC addresses only, instead use the show mac address-table dynamic
command

### Switch Interfaces

The first example assumes that you installed the switch and cabling correctly, and that the 
switch interfaces work. Once you do the installation and connect to the Console, you can 
easily check the status of those interfaces with the show interfaces status command

You can see the status for a single interface in a couple of ways. For instance, for 
F0/1, the command show interfaces f0/1 status lists the status in a single line of output as 
in Example 5-2. The show interfaces f0/1 command (without the status keyword) displays a 
detailed set of messages about the interface

The show interfaces command has a large number of options. One particular option, the 
counters option, lists statistics about incoming and outgoing frames on the interfaces. In 
particular, it lists the number of unicast, multicast, and broadcast frames (both the in and out 
directions), and a total byte count for those frames. Example 5-3 shows an example, again 
for interface F0/1

First, if you know the MAC address, you 
can search for it—just type in the MAC address at the end of the command, as shown in 
Example 5-4. All you have to do is include the address keyword, followed by the actual 
MAC address. If the address exists, the output lists the address. Note that the output lists 
the exact same information in the exact same format, but it lists only the line for the matching MAC address.

`SW1# show mac address-table dynamic address 0200.1111.1111`

or interface command

`SW1# show mac address-table dynamic interface fastEthernet 0/1`

or vlan

`SW1# show mac address-table dynamic vlan 1`


Switches do learn MAC addresses, but those MAC addresses do not remain in the 
table indefinitely. The switch will remove the entries due to age, due to the table filling, and 
you can remove entries using a command.

First, for aging out MAC table entries, switches remove entries that have not been used for a 
defined number of seconds (default of 300 seconds on many switches).

The aging time can be configured to a different time, globally and per-VLAN using the mac address-table aging-time
time-in-seconds [vlan vlan-number] global configuration command. The example shows a 
case with all defaults, with the global setting of 300 seconds, and no per-VLAN overrides.

The command also allows parameters to limit the types of entries cleared, 
as follows:
■ By VLAN: clear mac address-table dynamic vlan vlan-number

■ By Interface: clear mac address-table dynamic interface interface-id

■ By MAC address: clear mac address-table dynamic address mac-address


page 125 for commands reference

## Chapter 6

> Example of configuring password login security (no usernames)

> SSH configuration commands with related username login security