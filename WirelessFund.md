# Wireless Fundamentals

Standard for Wireless LAN: 802.11

## Wireless Network Issues
- All devices within range receive all frames, like devices connected to an Ethernet hub.
    - Privacy of data within the LAN is a greater concern.
    - CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance) is used to facilitate half-duplex communications. A device will wait for others to transmit before transmitting itself.
    - CSMA/CD is for wired networks.
- Wireless communications are regulated by various international and national bodies.
- Wireless signal coverage area must be considered.
    - Signal range.
    - Signal absorption: passing through material weakens signal
    - reflection: signal bounces off metal surfaces
    - refraction: waves are bent when passing through different materials.
    - diffraction:travels around obstacle
    - scattering: scatters signal in various signals
- Other devices using the same channels can cause interference.
    - For example, a wireless LAN in your neighbor’s house/apartment.

## Radio Frequency
- To send wireless signals, the sender applies an alternating current to an antenna.
→This creates electromagnetic fields which propagate out as waves.
- Electromagnetic waves can be measured in multiple ways for example amplitude and 
frequency.
- Amplitude is the maximum strength of the electric and magnetic fields.
-  Frequency measures the number of up/down cycles per a given unit of time.
- The most common measurement of frequency is hertz.
→ Hz (Hertz) = cycles per second
→ kHz (Kilohertz) = 1,000 cycles per second
- Another important term is period, the amount of time of one cycle.
→ If the frequency is 4 Hz, the period is 0.25 seconds.

### Range
- The visible frequency range is about 400 THz to 790 THz.
- The radio frequency range is from 30 Hz to 300 GHz and is used for many purposes

## Wi-Fi
Two Bands:
2.4 GHz: 2.400 GHz to 2.4835 GHz
5 GHz: 5.150 GHz to 5.825 GHz

2.4 provides further reach but more interference cause of large quantity of devices.

Wifi 6 (802.11ax) introduced 6 GHz band


### Channels
Bands are further divided into channels. Devices are configure to transmit and receive from one or more channels.

Small Wireless LAN with Single AP, use any channel.

Larger WLANs with multiple AP's, use non overlapping channels.
For 2.4 GHz, use channels 1,6,11
5 GHz has non-overlapping channels.

Channels 1,6,11 can be arranged in honeycomb pattern.
1-6/11 or 1-5/9-13

## Service Set
802.11 defines different kinds of service sets which are groups of 
wireless network devices.
- There are three main types:
→ Independent
→ Infrastructure
→ Mesh
- All devices in a service set share the same SSID (service set 
identifier).
- Does not have to be unique

**IBSS**
Independant Basic Service Set.
two or more wireless devices connected without AP.
Ad hoc network.

**BSS**
Connected via AP only not direct.
BSSID used to identify the AP.
Can have same SSID but not BSSID.
BSSID is usually the MAC Address

Signal Area is called BSA Basic Service Area
Devices in BSS are called clients or stations.


**ESS**
Extended Service Set.
Multiple BSS connected using Wired Network.
→ Each BSS uses the same SSID.
→ Each BSS has a unique BSSID.
→ Each BSS uses a different channel to avoid interference.
Clients can pass between APs without having to reconnect, 
providing a seamless Wi-Fi experience when moving 
between APs.
→ This is called roaming.
● The BSAs should overlap about 10-15%.

**MBSS**
Mesh Basic Service Set
Root Access Point connected to Wired Network.
Mesh Access Points connected to each other and the RAP.
Mesh AP use 2 radios. One to transmit and one to form a backhaul networ for bridging traffic between AP's.
A protocol is used to determine the best path through the mesh.

**Distribution System**
Most Wireless networks are connected to a wired network.
The wired network is know as the Distribution system.
Each Wireless BSS or ESS is mapped to a VLAN in the wired network.

Possible for AP to provide multiple WLANS with unique SSID.
Each WLAN is mapped to difference VLAN and connected to wired network via Trunk.
Each WLAN uses unique BSSID by incrementing the last digit of BSSID by one.

## Additional AP Operational Modes
- AP can have repeater mode to extend the range of BSS.
It retransmits signals. If the repeater has one radio, then it can operate on the same channel as the AP. If it has two radios, then one channel to receive and one channel to transmit.

- AP can act as a workgroup bridge that connects wired devices to the wireless network.
Two kinds of WGB. Universal WGB is 802.11 standard whereas WGB is Cisco Proprietory.

- APs with specialized antennas can send signal over longer distances making them an outdoor bridge. It can be point to point or point to multipoint connection.
