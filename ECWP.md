## EnGenius Certified Wireless Professional

## WLAN Fundamentals
##### Electromagnetic Wave
- frequency, number of oscillation per sec
- wavelength, length of single oscillation
- speed of light
- Frequency and wavelength have an inverse relationship, relative to the speed of light (c): 
f=c/λ
<img width="818" height="594" alt="image" src="https://github.com/user-attachments/assets/29dba1ec-cdf9-4310-bc43-ed4b5afd746e" />

##### Modulation
- Amplitude Modulation (AM): Change the amplitude (i.e. power) of the signal over time
- Frequency Modulation (FM): Change the frequency (i.e. wavelength) of the signal over time
- Phase Modulation (PM): Change the phase of the signal over time
<img width="798" height="562" alt="image" src="https://github.com/user-attachments/assets/68907467-277f-4c50-893d-e5db2912912f" />

##### Unit of Measurement
- decibals
- Power levels in Wi-Fi: 1000 mW to 10^-9 mW
- Types of Power Measurement:
  - dBm: Absolute measure of power in decibels (relative to milliwatts, where 0 dBm = 1 mW)
  - dB: Relative comparison of two power values
  - dBi: Relative gain of signal strength of an antenna (relative to a theoretical isotropic radiator
- Law of 3 dB
  - +3 dB = 2x power
  - -3 dB = 1/2 power
  - eg: 16 db = 16 mW -> 19 db = 32 mW...
- Law of 10 dB
  - +10 dB = 10x power
  - -10 dB =  0.1x power
  - eg: 10 db = 10 mW -> 20 db = 100 mW
 
##### Signal Degration
1. thermal noise
- unavoidable noice, comes from the vibration of the atoms(>absolute zero degree)
- N dbm (Thermal noise in dBm) =10 log 10(1000 kB (Boltzmann constant) Temp) + 10 log 10(∆f (channel size, Hz))
2. free space path loss (FSPL)
- degradation of electromagnetic waves signal strength when propagates through free space
- distance between a transmitter and receiver
- $$FSPL_{\text{dB}} = 20 \log_{10}(d) + 20 \log_{10}(f) + 20 \log_{10}\left(\frac{4\pi}{c}\right)$$
3. Attenuation
- loss of electromagnetic signals from interaction with objects in the environment
- Function of the material type and the wavelength:
  - Absorption: Energy absorbed by the material
  - Reflection: Energy reflected by the material (creates multipath signals)
- Lower frequency signals propagate through materials more easily (i.e. less loss) than higher frequency signals
<img width="736" height="425" alt="image" src="https://github.com/user-attachments/assets/1d21efe7-44c8-45b7-8bc7-5cda4f7572c4" />

3. Diffraction
- cause bending of eletromagnetic waves
4. Fresnel Zone (fray-NELL)
- a electromagnetic wave signal between point-to-point/multi that does not have any obstacles (line of sight)
- calculation: $$R_n = \sqrt{\frac{n \lambda d_1 d_2}{d_1 + d_2}}$$

##### Link Budget
- The link budget is estimated based on the following factors:
  - **EIRP: Effective isotropic radiated power**
    **- Transmitter power
    - Transmitter antenna gain
    - Transmitter antenna cable / connector losses
  - Free space path loss
  - Attenuation in path (e.g. walls, windows, etc.)
  - Receiver antenna gain
  - Receiver antenna cable / connector losses**
- **Received Signal Strength Indicator (RSSI)**
  - Measured signal strength at the receiver
- **Receive Sensitivity**
  - Minimum signal strength that the receiver can interpret a signal at a particular modulation
- **Fade Margin / SNR (signal to noise ratio)**
  - Difference between the link budget and the receive sensitivity (a.k.a. signal to noise ratio)
  - Good performance requires > 15 - 20 dB margin
 
 ##### Contention
- wired and wireless have same travel speed
- wired have better throughput result
- collision may occur when many devices transmit data
- **wired:**
  - full-duplex, send and receive same time
  - detect collision, pause, wait the wire clear, resume 
- **wireless:**
  - half-duplex, either send or receive same time
  - cannot detect collision when transmit data
- **Avoidance**
  - reserve a connection lifetime
  - send frame
  - received ACK?
  - no -> collision, vise versa

##### Data Rate
- connection or link-speed in a given period of time
- may be affect by AP, wireless adapter of connecting device, and RSSI to name a few

##### Standards and Regulations
* **Regulatory Bodies (FCC & CE):** 
  * Enforce rules and allocate radio spectrum for radio, television, wire, satellite, and cable communications.
  * **Licensed Spectrum:** Organizations pay to use specific frequencies in a designated area (e.g., cellular networks).
  * **Unlicensed Spectrum:** Free for public use (e.g., Wi-Fi bands) provided equipment complies with power limits and interference rules.

* **Wi-Fi Alliance:**
  * An industry association of over 350 manufacturers that conducts standardized interoperability testing.
  * Certifies key features including Quality of Service (**WMM**), Power Saving (**WMM-PS**), Security (**WPA/WPA2/WPA3**), and Voice over Wi-Fi (**VoWiFi**).

* **Standards Organizations (IEEE & ETSI):**
  * **IEEE:** Defines core technical standards for Wi-Fi technologies.
  * **ETSI:** Establishes Harmonized European Standards required for European regulations.
  * **Band Allocation:** Opening new frequency ranges (such as the $6\text{ GHz}$ band for Wi-Fi 6E) requires official approval and rule changes from these regulatory agencies.
 
## WLAN Planning and Design
##### Wifi Inteference
- common root cause of wireless issues
<img width="1693" height="794" alt="image" src="https://github.com/user-attachments/assets/13c7a60e-3277-4171-a031-e71edb2b3852" />

**Wi-Fi Spectrum (2.4 GHz)**
- each gap takes 5 MHz
- minimum channel width takes 20 MHz
- interference happens when 2 or more channels overlap, either same / adjacent
- for 5/6 GHz, min = 20, max = 160
<img width="1200" height="492" alt="image" src="https://github.com/user-attachments/assets/33086b5b-b515-4edd-b158-2e8268734c68" />

**Dynamic Frequency Selection (DFS)**
- analogy: when driving on the road, hearing police alarm need to drive away and let the police car go first.
- when receive radar signals, allows Wi-Fi routers to share certain GHz frequency channels with primary radar systems—such as weather radars, air traffic control, and military radar
- will have 1–10 minute wait time, might cause blackout

**Zero wait DFS**
- backup dfs, reduce redundancy

##### Site Survey
- A proper pre-deployment site survey ensures optimal coverage and effective channel planning to avoid interference between deployed Access Points (APs). It is typically performed during an ocular inspection or site visit.
**Key Considerations**
* **RSSI Buffer for Low-Power Devices:** Set aside a buffer when using a PC/Mac to measure RSSI to account for lower transmit power ($T_x$) devices (e.g., mobile phones, ultrabooks). 
  * *Example:* If you measure **-75 dBm** on a PC, target an RSSI that is **~5 dBm higher** for client planning.
* **Signal Strength Thresholds:**
  * **-75 dBm:** Borderline between a good and unreliable client connection. Performance varies based on environmental factors and client adapter capabilities.
  * **-65 dBm:** Recommended target ceiling if the environment requires real-time services like Voice over IP (VoIP).
* **AP Placement & Overlap:**
  * Distance between APs in multi-AP setups is determined by intermediate RSSI readings.
  * Wireless coverage overlap is required to prevent downtime during client handoffs.
  * In **Fast Roaming** enabled environments, APs must be able to "hear" one another.
  * Control RSSI level and coverage by adjusting AP physical placement or transmit power ($T_x$ power is directly proportional to RSSI level and coverage).

##### Site Survey Tools
- Survey tools range from free to licensed options, varying primarily in user experience and data collection depth.
**Recommended Software Tools**
* **PC / Mac:** inSSIDer by MetaGeek
* **Mac:** WiFi Scanner
* **iOS:** AirPort Utility
* **Android:** WiFi Analyzer
* **EnGenius:** EnGenius Cloud Frequency Spectrum *(Requires Security AP with a PRO License)*

> **Hardware Tools:** Dedicated handheld hardware survey devices are also available and serve as a reliable investment for frequent site surveys.

##### Wifi Heatmap
- used for **pre-deployment planning**, **post-deployment adjustments**, **project proposals**, and as an alternative when on-site surveys are restricted or impossible
- Cost Alternative: While c**ommercial heat map software** often requires **expensive subscriptions**, **EnGenius Cloud** provides a **built-in solution**
- EnGenius Cloud's Floor Plan View
  > Allows users to plot environmental obstacles and generate heat maps tailored to specific access point (AP) models and antenna specs.
  > Supports plotting Virtual APs to simulate and plan deployments without physical hardware.
  > Enables floor plan export via the EnGenius Cloud reporting feature.
  > Note: Plotting obstacles and virtual APs requires a PRO License.
<img width="1200" height="563" alt="image" src="https://github.com/user-attachments/assets/9f34de0f-b4a5-404c-a950-75d96d56a205" />

##### Channel Planning
> Channel planning is a **critical phase** in Wi-Fi system design. Proper channel distribution directly **minimizes post-deployment wireless interference** and **reduces troubleshooting or support requests**.

**Key Objectives**
* **Avoid Overlap:** The primary goal is to ensure adjacent or nearby Access Points (APs) do not share the same channel (Co-Channel Interference) or overlapping adjacent channels.
* **Vertical Planning (Multi-Story):** Channel planning must account for 3D space in multi-floor environments. 
  * EnGenius ceiling-mount APs feature **spherical antenna patterns** that penetrate walls and floors depending on building materials.
  * Precise penetration rates and signal boundaries should be validated through on-site surveys.

## Initialization
##### EnGenius Cloud Firewall Requirements
In high-security network environments, network administrators must ensure the following outbound ports are allowed for EnGenius Cloud devices to function properly.
<table data-header-hidden data-full-width="true"><thead><tr><th width="177">
Cloud Devices</th><th width="184">
 Cloud Services</th><th width="149">Source IP</th><th width="154">Destination IP</th><th width="324">FQDN</th><th width="107">Ports</th><th width="252">Protocol (TCP/UDP/ICMP..)</th><th width="100">Direction (Inbound / outbound / bi-direction)</th></tr></thead><tbody><tr><td>
<strong>Cloud Devices</strong></td><td>
 <strong>Cloud Services</strong></td><td><strong>Source IP</strong></td><td><strong>Destination IP</strong></td><td><strong>FQDN</strong></td><td><strong>Port Number</strong></td><td><strong>Protocol (TCP/UDP/ICMP..)</strong></td><td><strong>Direction (Inbound / outbound / bi-direction)</strong></td></tr><tr><td>AP, SW, GW, Ensky, PDU</td><td>Periodical Cloud communication,Firmware Upgrade,Real-Time Meter</td><td>Your Networks</td><td>any</td><td><p>swallow.production.engenius.ai</p><p></p><p>services.engenius.ai</p><p>               </p><p>dolphin-*.production.engenius.ai</p><p></p><p>deviceingress.production.engenius.ai</p><p> chicken.production.engenius.ai</p></td><td>443</td><td>TCP</td><td>Outbound</td></tr><tr><td>AP,SW ,GW, Ensky, PDU</td><td>Persistent Cloud communication</td><td>Your Networks</td><td>44.224.197.174</td><td>raccoon.production.engenius.ai</td><td>80</td><td>TCP</td><td>Outbound</td></tr><tr><td>AP</td><td>Cloud Radius</td><td>Your Networks</td><td>44.225.123.183</td><td>NA</td><td>1812/1813</td><td>TCP &#x26; UDP</td><td>Outbound</td></tr><tr><td>AP, SW , GW, Ensky, PDU</td><td>NTP time sychronization</td><td>Your Networks</td><td>any</td><td>NA</td><td>123</td><td>UDP</td><td>Outbound</td></tr><tr><td>AP, SW , GW, Ensky, PDU</td><td>Remote Tunnel</td><td>Your Networks</td><td>44.236.43.29</td><td>sshserver-0.production.engenius.ai</td><td>22</td><td>TCP</td><td>Outbound</td></tr><tr><td>AP, GW</td><td>Splash Page</td><td>Your Networks</td><td>any</td><td><p>s3-us-west-2.amazonaws.com</p><p>falcon.production.engenius.ai</p></td><td>80/443</td><td>TCP</td><td>Outbound</td></tr></tbody></table>

##### EnGenius Cloud setup:
- EnGenius Cloud Portal
- EnGenius Cloud To-Go App
- Create an EnGenius Cloud account (https://cloud.engenius.ai/login)
- Register Cloud device
- Assign the device to a Network

## Management
##### Access Point
- EnGenius Cloud Access Points are grouped per Network. Depending on the network administrator, the Network can be setup in multiple ways. Network segregation can be done per:
* **Branch or site** - clients with multiple branches or locations, and each site have their own wireless configuration
* **Building** - hospitality verticals usually have the same setup for all APs in multiple floors, with the exception of a few units in specific areas which can be overridden on the *Access Points* page or individual AP details page
* **Floor** - commercial or leasing establishments may have a different network layout per story
* **Department** - some clients call for specific network setups per department despite being on the same physical location; in this situation, the Org is split into several Networks for each department.
<img width="1903" height="823" alt="image" src="https://github.com/user-attachments/assets/2b1b7f98-ed27-41c9-ba1e-30cc544466b4" />

- **Configuration Overrides**
  - Each access point **can be configured to override** the Radio and SSID settings. This comes in **handy for fine tuning APs** in specific placement areas.
<img width="1901" height="940" alt="image" src="https://github.com/user-attachments/assets/5302ddbc-9979-475d-8649-d56102e44305" />

##### Radio Settings
- can only be configured when viewing a Network. These settings apply to all APs within the Network unless overridden on a specific device.
<img width="618" height="852" alt="image" src="https://github.com/user-attachments/assets/0273d51f-8fda-41ea-bed5-afe8ac6c602b" />

# Network Management - Radio Settings
**Course:** EnGenius Certified Wireless Professional (ECWP)

Radio Settings can only be configured when viewing a Network. These settings apply to all APs within the Network unless overridden on a specific device.
<img width="618" height="852" alt="image" src="https://github.com/user-attachments/assets/028e5679-917c-4d0a-8cc4-650540c4d9ea" />

| Option                      | Description                                                                                                                                                                                                                                                                                                                                   |
| :-------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Radio**                   | Enables/Disables 2.4 GHz/5/6 GHz radios.                                                                                                                                                                                                                                                                                                      |
| **Channel**                 | Specifies a frequency or set to auto.                                                                                                                                                                                                                                                                                                         |
| **Auto Channel List**       | Allows the network administrator to specify which channels the Wi-Fi system can automatically select from when operating in "Auto" mode for channel selection.                                                                                                                                                                        |
| **Exclude DFS**             | When channel selection is set to auto, the device will not scan/select DFS channels.                                                                                                                                                                                                                                                          |
| **PSC Channel**             | The standard implements a new efficient process for clients to discover nearby access points (APs). In Wi-Fi 6E, a process called fast passive scanning is being used to focus on a reduced set of channels called preferred scanning channels (PSC). PSCs are a set of 15 20-MHz channels that are spaced every 80 MHz. The APs will set their primary channel to coincide with the PSC so that it can be easily discovered by a client, and clients will use passive scanning in order to just scan PSCs to look for an AP. |
| **Channel Width**           | Sets the channel width from 20, 40, or 80 MHz. The higher channel widths support higher data rates for Wi-Fi 5 and Wi-Fi 6 models, but this subjects the AP to interference. *See:* Wi-Fi Interference.                                                                                                                                        |
| **Target Tx Power**         | Sets the target transmit power for the AP which depends on the maximum allowable EIRP per country. The actual Tx power set by the system may be higher or lower than the Target Tx set.                                                                                                                                                  |
| **Min. Bitrate**            | Sets the minimum bitrate for the AP. Adjusting this option will affect clients who have older generation devices or have low RSSI/SNR .                                                                                                                                                                                                    |
| **Client Limit**            | Limits the maximum concurrent clients on the AP per radio. 127 for Wi-Fi 5 and 500 for Wi-Fi 6 models.                                                                                                                                                                                                                                       |
| **Discard 802.11a/b/g**     | Blocks connections from older generation devices.                                                                                                                                                                                                                                                                                             |
| **Disable 11ax**            | Disables 802.11ax on Wi-Fi 6 models. This option will force the AP to run in 802.11ac mode, useful for environments where majority of client devices do not support 802.11ax yet.                                                                                                                                                          |
| **Disable 11be**            | Some legacy wireless clients are not compatible with 11be. This option allows legacy equipment to connect with your network as usual.                                                                                                                                                                                                         |
| **DCS (Dynamic Channel Selection)** | When auto channel is selected, the AP scans and changes channels on start-up or upon reboot. DCS allows the AP to scan the environment every 15 mins, and change the channel if the utilization is >50%. During the change, clients momentarily get disconnected. This option is not advisable for use in connection-sensitive applications. |
| **Client Balancing**        | In a multi-AP deployment, this option allows the AP to steer clients to neighboring units to prevent overloading or to spread clients evenly in a dense AP deployment. This function utilizes 802.11v.                                                                                                                                        |
| **Mesh**                    | Enabling Mesh unlocks *Auto Pairing* , which is a one-click setup for mesh connections.                                                                                                                                                                                                                                                       |

##### SSID Profiles
A total of **8 SSID** profiles can be created **per Network**. If all profiles are enabled with all radios selected (2.4 GHz, 5 GHz, and 6 GHz on supported APs), the APs under the Network will broadcast up to 24 BSSIDs.
<img width="1200" height="432" alt="image" src="https://github.com/user-attachments/assets/a8f8a169-3707-4707-bdd0-82ec2ffcdc85" />

> **Note:** Enabling **5 or more SSIDs** may heighten channel utilization due to the **increase in management overhead**.

---

#### Wireless Configuration Options
| Option | Description |
| :--- | :--- |
| **Name** | Sets the SSID name. |
| **Enable** | Toggles the SSID broadcast on or off. |
| **Type** | Selects between Wireless or SmartCast (Pro License Only). |
| **Multi-Link Operation (MLO)** | Allows Wi-Fi 7 clients to create multiple asynchronous links across different bands and transmit data concurrently to increase total bandwidth and stability. |
| **Hide** | Disables SSID broadcast. *Note: 6 GHz is not supported when Hide is enabled.* |
| **Radio** | Selects operating radios (2.4 GHz, 5 GHz, 6 GHz, or All). |
| **Security Type** | Selects wireless authentication mode (Open, OWE, WPA2 PSK, WPA2 MyPSK, WPA3 Personal SAE, WPA2/3 Mixed, or Enterprise options via Cloud RADIUS, Custom RADIUS, Google LDAP, my LDAP, Active Directory, or Azure AD). *Note: 6 GHz radio requires OWE, WPA3 Personal, or WPA3 Enterprise.* |
| **802.11r** | Enables Fast Roaming. Requires overlapping AP coverage and client support. |
| **802.11w** | Enables Protected Management Frames (PMF) to prevent deauthentication attacks. |
| **Default VLAN** | Tags a specific VLAN to the SSID (overridden if MyPSK user VLAN is set). |
| **Client IP Addressing** | Configures network bridging via **Bridge Mode** (external DHCP), **NAT Mode** (AP acts as DHCP; isolates wireless clients), or **Tunnel (EoGRE)** (routes traffic through an encrypted Layer 2 GRE tunnel to a remote site). |
| **Dynamic Client VLAN Pooling** | Assigns clients randomly across a designated VLAN range to prevent broadcast flooding. |
| **Application Analysis** | Enables Layer-7 application monitoring across the network or organization. |
| **L2 Isolation** | Blocks communication between wireless clients, as well as wireless to wired devices. |
| **mDNS Forwarding** | Propagates multicast DNS packets across subnets. |
| **Band Steering** | Prioritizes connecting devices to the 5 GHz radio and uses an RSSI threshold to steer low-signal clients back to 2.4 GHz. |
| **BCMC Suppression** | Blocks broadcast/multicast traffic (except DHCP and ARP) from the LAN to the wireless network. |

**Feature Modules**
**Fast Roaming**
Supports 802.11r, 802.11k, and 802.11v standards to achieve sub-50ms handoffs between APs.

**Bandwidth Lmiting**
- throttle maximum speed of wireless clients to prevent data hogs(consume unfair amount of data - can be bandwidth, storage)
- needed in bandwidth limited environments such as public Wi-Fi spaces like cafés or libraries

**Captive Portal & Splash Page**
Presents custom information, disclaimers, or user authentication prior to network access. Supports fully customizable WYSIWYG/HTML layouts and external portal integrations.
* **Click Through:** Displays a disclaimer page without login credentials.
* **Authentication Services:** Integrates with EnGenius RADIUS, Custom RADIUS (with CoA and per-user bandwidth limits), RADIUS MAC-Authentication, LDAP, Active Directory, or Azure AD.
* **Voucher Service:** Generates timed access tickets managed through an admin or front-desk portal.

**Access Control**
* **VIP List:** Whitelists specific wireless devices (printers, IoT) to bypass captive portals, or allows wired devices to be accessed through L2 Isolation.
* **Block List:** Denies network or SSID access to specified MAC addresses.

**Passpoint (Hotspot 2.0)**
Enables cellular offloading by broadcasting 802.11u information (Venue Name, Domain List, Roaming Consortium, 3GPP Info, NAI Realm) for auto-joining client devices.

**Application Control (AVXpress)**
Provides Quality of Service (QoS) prioritization for critical real-time traffic (video conferencing, streaming, gaming) into three tiers: *Express*, *Fast*, and *General*.

##### Firmware Management
EnGenius Cloud simplifies firmware management across Cloud devices. When a newly added device gains internet connectivity, EnGenius Cloud automatically pushes the latest firmware and triggers an auto-update.

**Release Tracks & Scheduling**
* **Firmware Selection:**
  * **Stable Release**
  * **Beta Release**
  * **Previous Stable Release**
* **Device-Specific Scheduling:** The firmware scheduler features separate tabs for Access Points (APs) and Switches, offering granular control over auto-update routines. All scheduled tasks execute according to the Network's configured time zone.

---

**New Firmware Trial Zone**
The **Trial Zone** feature allows network administrators to test new releases on selected devices before a full deployment:

* **Staggered Rollout:** Selected trial devices upgrade on schedule, while the remaining network hardware holds off on the update for 21 days post-release.
* **Easy Rollback:** If bugs or issues arise during the trial window, administrators can instantly revert devices to the previous firmware version simply by removing them from the Trial Zone.

##### Multitenancy
The larger the organization, the more network administrators are required depending on how the network is segregated. EnGenius Cloud's Team Members page allows for easy management of multitenancy for each Organization.
<img width="1200" height="413" alt="image" src="https://github.com/user-attachments/assets/62ce3f9f-a3f2-4545-bd2e-74cd358fc1ec" />

---

**Role Permissions**
| Role | Access Level & Scope |
| :--- | :--- |
| **Admin** | Has full control over either the entire Organization or specific Networks, as well as the Front-Desk Portal. |
| **Viewer** | Can view either the Organization or specific Networks, but cannot apply configurations or run diagnostic tests. |
| **Front-Desk** | Has access to the Front-Desk Portal specifically for voucher management. |

---

**Adding & Inviting Team Members**

* **Member Invitations:** New members are added by entering valid email addresses (supports entering multiple email addresses at once).
* **Scope Assignment:** Permissions can be set at the full Organization level or scoped down to specific Networks.
* **Account Sync:** Invited users receive a confirmation email with a link to sign in. Once signed in, the inviter's Organization will appear in the user's **Hierarchy View**.

##### Inventory & License Management
EnGenius Cloud provides centralized online management for device inventory and PRO Licenses across organizations.

---

**License Terminology**

| Term | Description |
| :--- | :--- |
| **License Key Issue Date** | The date when a license key is issued and mailed. |
| **Activation Date** | The date a license-associated device is assigned to a managed network. |
| **Forced-Activation Date** | The date the license auto-activates if unassigned for 90 days post-issue. |
| **Expiration Date** | The end date of the license duration for an associated device. |
| **Order Return** | Licenses can be returned within 1 month of issuance (subject to regional office policies). |
| **Undo License Association** | Licenses can be disassociated from a device within 7 days of association. |

---

**Core License Facts**

* **Trial Period:** All devices include a 1-year trial license (revoked only upon RMA replacement).
* **Permanence:** PRO licenses permanently attach to a device. On RMA replacements, the attached PRO license transfers automatically to the replacement unit.
* **De-registration:** De-registering a device permanently voids its attached PRO license.
* **Organization Transfers:** Licensed devices can be moved between Organizations by admins managing both Orgs.
* **License Mixing Rules:** An Organization can combine PRO APs with Basic Switches (or vice versa), but cannot mix different license levels on the same device type (e.g., mixing PRO APs and Basic APs in one Org).

> **Important (License Expiration):**
> When an Org is set to PRO and a device's license expires, the device goes offline for management. It remains functional locally, but monitoring and configuration changes become unavailable until:
> 1. The license is renewed, OR
> 2. The Organization is switched to a Basic License.

## Monitoring
1. Dashboard
- overall health of your Organization, or specific Networks
<img width="1180" height="740" alt="image" src="https://github.com/user-attachments/assets/8cfd38fe-f24a-4c9e-a9eb-cd9b5e14d10f" />
<img width="1149" height="736" alt="image" src="https://github.com/user-attachments/assets/1aaf094a-c0a5-41de-977b-719973d725d1" />

2. Access Point
<img width="1200" height="579" alt="image" src="https://github.com/user-attachments/assets/9e483a02-83a2-4b25-bc45-6ee5deed5f9d" />
<img width="1200" height="802" alt="image" src="https://github.com/user-attachments/assets/c6088bc2-a76d-4f46-b0cf-cc69f29e81f6" />

3. Topology View
- details on the network connection layout of the Cloud devices
<img width="1200" height="600" alt="image" src="https://github.com/user-attachments/assets/ac4827c3-0407-493c-9cb4-b95a9a36e68e" />

4. Client List
<img width="1823" height="734" alt="image" src="https://github.com/user-attachments/assets/5ca72e8a-680d-4181-9b0b-c964634abb75" />

- can control the access permission of each client
**Troubleshooting Tools:**
> Client Timeline
<img width="1823" height="765" alt="image" src="https://github.com/user-attachments/assets/6e29c311-2394-401b-b10e-8601ee5668c3" />
<img width="1066" height="520" alt="image" src="https://github.com/user-attachments/assets/c96b5318-a1fa-40fb-967f-d94540e04987" />

> Exposure Analysis
<img width="1279" height="835" alt="image" src="https://github.com/user-attachments/assets/df3e4ab4-cd65-4b0d-bc73-80279ee39d60" />

> Application Analysis
<img width="554" height="821" alt="image" src="https://github.com/user-attachments/assets/3ef503b7-f95b-44a2-b4e4-9891a3350e6f" />

5. Reports

6. Notifications & Alerts

7. SNMP Monitoring

8. API Integration

9. Syslog & Traffic Logs
