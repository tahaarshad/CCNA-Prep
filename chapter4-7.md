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

copy running-config startup-config

write erase
erase startup-config
erase nvram:


hostname name

passsword pass



Switch# configure terminal
Switch(config)# hostname Fred
Fred(config)# line console 0
Fred(config-line)# password hope
Fred(config-line)# interface FastEthernet 0/1
Fred(config-if)# speed 100
Fred(config-if)# exit
Fred(config)#


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