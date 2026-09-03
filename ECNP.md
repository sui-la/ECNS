## OSI Model
##### 1. layer 1 - physical
- media used to receive or send signal to a network device
- physical: ethernet cable (8 strand / 4 twisted pairs)
  - specs (5e, 6 (noice reduction), 6a, 7a/8)
  - maximum length: 100m for 5e and 6a, 55m for 6, 8 for data center
  - speed: 1Gbps for 5e, 10Gbps for 6 & 6a, 40Gbps for 8
- wireless: radio frequency, electromagnetic spectrum (wave length, frequency, energy)
- internet: Fiber, coax cable, telephone cable, Ethernet, wireless, etc
##### 2. layer 2 - data link
- Local Link Control (LLC) - encode/decode information & transmit to layer 3 (network layer)
- Media Access Control (MAC) - encode/decode information & transmit to layer 1 (physical)
- every MAC is unique & have 48 bits hexadecimal (0-f) - `00:00:00` (Organizational Unique Identifier):00:00:00
- 2^48 = 281.5 trillion unique addresses
##### 3. layer 3 - network
- IP address - standard network protocol - 2^32 ip addr only
- 32 bit 0.0.0.0 -> 00000000.00000000.00000000.00000000 (4 octet)
- 1s part = network id, 0s part = host id, determine LAN or WAN using network id
- 10, 172, 192 -> private
- CIDR Notation - indicate number of network id) - (class a(255...), b(255.255..), c(255.255.255.))
- subnet more, device more
- 2^(32−CIDR) = number of devices on the local network

2^32 ip addr not enough (solution)
- ipv6 - 2^128 ipv6 addr
- 128 bit of hexadecimal - 0000:0000:0000:0000:0000:0000:0000:0000:
- mostly public network - internet backbone

##### Port Forwarding
- Network Address Translator (NAT)
  - maps WAN stream ip and port to LAN stream ip and port
  - useful when accessing a LAN from a WAN
  - Mapping is defined in the router / gateway
  - Examples:<WAN IP>:6123 ➡ 192.168.1.61:23'

##### 4. layer 4 - transport
- multiple streams of data from a single network device
- stream take place in different ports (1-65535) - a 16-bit number
- 21,22,23,25,53,80,139,443,445,3389,5985,8080...
Common Protocol
- Transmit Control Protocol (TCP)
  - tcp/ip -> tcp handshake -> stable connection
  - reliable
  - complete data transmission
  - for file transfer, internet browsing
- User Datagram Protocol (UDP)
  - fast
  - no waiting of data completion before sending, once receive then send
  - for phone calls, streaming
##### 5. layer 5 - session

##### 6. layer 6 - presentation

##### 7. layer 7 - application

## Networking Metrix
##### 1. Bandwidth / throughput
- amount of data can transfer within a unit of time
##### 2. Latency
- time delay btw source and destination (more consistance)
- mainly cause by: distance, interference/noise, routing
##### 3. Jitter
- a type of latency cause when transmitting (real-time applications like voice calling and video streaming)
- less consistance
- inbound more, outbound less

## Network Component
##### 1. Modem
- external internet connection provided by ISP to a building
- Optical Network Terminal(ONT) a hardware device that can translates the incoming media (fiber) into digital data your router and devices can use
- translate (coax and telephone) into Ethernet
- Bandwidth expressed as downstream speed / upstream speed in Mbps
  - 100M, 500M, 1G, 10G (fiber)
  - 50/5M, 50/10M, 100/10M (cable)
  - 1.5M / 1.5 (T1 , SDSL)
  - 7 / 768k, 12 / 1.5M, 18 / 1.5M (ADSL)
##### 2. Router/Gateway
- control access between 2 network (LAN/WAN)
- Router vs Gateway (with NAT, active in layer 3-7)
- provide DNS and DHCP function
##### 3. Switches
- Central nervous system of the internal network
- connect multiple wired Ethernet devices to intercommunicate within a network
- Power over Ethernet (PoE): Supplies power as well as a data connection over a single Ethernet cable:
  - Access Points
  - Cameras
  - Keycard access readers
  - Other wired network appliances
##### 4. Access Points
- connect wireless devices to a wired network
- Translates wireless communication over radio waves to wired communication over Ethernet
##### 5. Private Network Applications
a. Dynamic Host Configuration Protocol (DHCP)
- assigns an IP address, subnet mask, gateway, and DNS servers to a client device when it first connects to the network
- DORA process (discovery-broadcast, offer-unicast, request-broadcast, acknowledge-unicast)
- Allows mobile client devices to freely move between networks
- Best Practice: assign static ip to any devices 'owned' the network, dynamic ip for client devices - for easier monitor and troubleshooting
b. Domain Name Service (DNS)
- a phonebook that can translate the fully qualified domain name(FQDN) to a ip addr
- Bandwidth provider -> private DNS servers
- Gateways are typically are setup to relay/forward DNS requests -> for first time no cache in recursive dns server
- Best Practice: use DNS from different source provider

## Cabling Infrastructure
- describe how network cables, bandwidth limits, and physical mediums are designed to prevent network bottlenecks.
##### BottleNecks
- any component within the transmission path that limits the speed of transmission
- Most switches and cables deployed today are capable of 1 Gbps
- 802.11ac and later pushes wireless bandwidth above 1 Gbps
- Wave 1 has theoretical max capacity of 1.3 Gbps
- Wave 2 has theoretical max capacity of 6.9 Gbps
- WiFi 6 has theoretical max capacity of 9.6 Gbps
- Note corresponding wired bandwidth is 40% - 50% of wireless bandwidth due to Wi-Fi overhead
##### Cabling Best Practices & Standards
1. Vertical / Inter-Building Cabling (Backbone)
- Used to connect different floors, server rooms, or separate buildings where longer distances and higher data loads are required:
- Multi-Mode Fiber: Supports up to 10 Gbps full duplex for distances up to 300 meters (1,000 ft).
- Single-Mode Fiber: Supports up to 40 Gbps full duplex for long-distance runs (up to ~60 miles).
- Copper (CAT6a): Can be used for shorter vertical runs under 100 meters (328 ft).

2. Horizontal Cabling
- Used to connect patch panels/switches on the same floor directly to end-user wall outlets, access points, and desktop computers:
- CAT5e: Supports up to 2.5 Gbps (via IEEE 802.3bz) up to 100m.
- CAT6: Supports up to 5 Gbps up to 100m.
- CAT6a: Industry recommendation for modern deployments; supports 10 Gbps up to 100m.
- CAT7a / CAT8: Future-proofing standard supporting 40 Gbps+ up to 100m.

## Network Switch
##### 1. Unmanaged
- Dumb switch - plug and play
- no GUI and configuration needed
- Directs traffic between ports based on MAC addresses (LAN)
##### 2. Managed
a. layer 2
- Full Layer 2 capabilities (VLANs, dynamic MAC address table, link aggregation with LACP, spanning tree protocol, SNMP, ACL, etc.)
b. layer 3
- Operates as a managed switch plus it has functions usually available on routers such as a DHCP server and routing capabilities
c. Smart
- Limited Layer 2 capabilities (e.g. only VLANs, static link aggregation, dynamic MAC address table)
##### 3. switch interface
a. ethernet port - usually up to 100 m
- 8, 24, 48 ports
- have different speeds
  - 10/100 Mbps
  - 1000 Mbps or Gigabit
  - 2.5 Gbps / 5 Gbps or Multi-G
  - 10 Gbps
  - 100 Gbps
b. Small Form-factor Pluggable (SFP) Port
- use to slot in Fiber or digital-to-analog converter(DAC) connections used for uplinks
- DAC - convert digital data -> electrical signal -> sound that can play by device
- speed: 1 Gbps or 10 Gbps (SFP+)
- range: > 100m
- Fiber SFP Types:
  - Single mode
    - shorter wavelength
    - longer distance, up to 100 km
    - costly
 
  - Multi mode
    - short distance, up to 2 km
    - cost-effective solution for uplink  - means transmit data from smaller network to larger network
c. Power over Ethernet (PoE)
- use to power up device through ethernet connection
- cost effective - can transmit data and power up device to a device
- There are multiple PoE standards available:
  - PoE or 802.3af - provides up to 15.4 W of power
  - PoE+ or 802.3at - provides up to 25.5 W of power
  - PoE++ or 802.3bt - provides up to 71.3 W of power
 
## Initialization
EnGenius Cloud Portal (web)
- for larger, or controlled networks
- https://cloud.engenius.ai/ezm/dashboard
EnGenius Cloud To-Go Application (mobile)

##### Firewall
- most of the ports for device communication are open
- some networks have tighter security
- ports need to be allowed by the network administrator to ensure that the Cloud devices function accordingly\
| Cloud Devices     | Cloud Services                                                    | Source IP    | Destination IP | Ports     | Protocol  | Direction |\
| :---------------- | :---------------------------------------------------------------- | :----------- | :------------- | :-------- | :-------- | :-------- |\
| AP, Switch, EnSky | Periodical Cloud communication, Firmware Upgrade, Real-Time Meter | Your Network | Any            | 443       | TCP       | Outbound  |\
| AP, Switch, EnSky | Persistent Cloud communication                                    | Your Network | 44.224.197.174 | 80        | TCP       | Outbound  |\
| AP                | Cloud RADIUS                                                      | Your Network | 44.225.123.183 | 1812/1813 | TCP & UDP | Outbound  |\
| AP, Switch, EnSky | NTP Synchronization                                               | Your Network | Any            | 123       | UDP       | Outbound  |\
| AP, Switch, EnSky | Remote Tunnel                                                     | Your Network | 44.236.43.29   | 22        | TCP       | Outbound  |\
| AP                | Splash Page                                                       | Your Network | Any            | 80/443    | TCP       | Outbound  |

##### Cloud Setup
- register a account
- register the devices on the desired organizations
- assign the device to the network

## Network Management
##### Hirarchy
- can create multiple organizations, companies, departments, locations
- can group and assign policy to devices
- Networks can be branched from the main Org or placed in "sub-folders"
- devices follow a general policy setting set by the administrator
- parameters may be overridden when running a specific configuration for a device. I.e. Tx Power, Channel, SSID, etc
<img width="953" height="743" alt="image" src="https://github.com/user-attachments/assets/10917e1b-4638-4dfd-87ef-4788d8c9aec7" />

##### Switches
<img width="838" height="200" alt="image" src="https://github.com/user-attachments/assets/50fa2560-f74a-471b-ada8-4385967b3525" />

- able to remotely power-cycle a specific PoE (Power over Ethernet) port directly from the cloud management interface

##### Vlan
- segmentation of network, allows to create multiple segment in a physical network interface
- native vlan = vlan 1
- VLANs span from VLAN ID 1-4096
- standard of tagging & untagging of ethernet frames for vlan management: IEEE 802.1Q
