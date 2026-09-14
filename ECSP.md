# EnGenius Certified Security Professional

## EnGenius Security Gateway Series
- **ESG510** - focus in this course
- ESG610
- ESG620 models

## Front view of ESG510
<img width="759" height="379" alt="image" src="https://github.com/user-attachments/assets/cc2a5a34-b02f-43d3-a06d-61a312566e68" />

* **Core hardware specs**: Features four 2.5G copper ports delivering up to 2.35Gbps firewall throughput and 970Mbps VPN throughput.
* **Dual WAN capability**: Supports load balancing or failover by configuring the dual-purpose WAN2/P3 port as a secondary WAN link.
* **Cellular backup option**: Includes a USB 3.0 slot supporting 3G/4G dongles for WAN backup if primary connections fail.
* **PoE capability**: Designated LAN port P1 supports 802.3af PoE and PoE+ standards to power connected network devices.
* **Flexible deployment modes**: Operates in either routing mode or passthrough mode depending on your specific network topology.
  > #### 1. Routing Mode (Standard Setup)
    * **When to use:** Primary edge router/gateway for new deployments or complete router replacements.
    * **Function:** Handles NAT, DHCP server (`192.168.66.1/24`), DNS, local subnet routing, and firewall policies directly.
    * **Topology:**
  `Internet (ISP) ──> [WAN1] ESG510 Gateway (NAT/DHCP/Firewall) [LAN P1-P3] ──> Local Switch / Devices`

  > #### 2. Passthrough Mode (Bridge Setup)
    * **When to use:** Adding the ESG510 behind an existing core router/firewall without changing the existing IP scheme or creating double-NAT.
    * **Function:** Acts as a transparent Layer 2 bridge, passing traffic straight through while retaining security inspection and gateway features.
    * **Topology:**
  `Internet (ISP) ──> Core Router (NAT/DHCP) ──> [WAN1] ESG510 (L2 Bridge) [LAN P1] ──> Local Switch / Devices`

## Initial Setup and Verification
#### Power LED, Reset Button
<img width="763" height="393" alt="image" src="https://github.com/user-attachments/assets/80bb1cfc-8a5e-4ca3-bb1a-eb5cda7fcc20" />

#### ESG510 Default Settings for Plug & Play
<img width="358" height="388" alt="image" src="https://github.com/user-attachments/assets/2356b05d-7cec-46d0-8ed0-42d7a5a098da" />

* **WAN1 configuration**: Obtains its IP address dynamically via DHCP from the upstream ISP or router by default.
* **WAN2/P3 assignment**: Functions as a local network port (LAN P3) out of the box rather than a secondary WAN interface.
* **Default gateway IP**: Assigned to `192.168.66.1/24` to serve as the client gateway across local switch ports.
* **Integrated LAN services**: Ships with built-in LAN DHCP and DNS servers enabled by default at `192.168.66.1`.
* **Client IP scope**: Automatically leases IP addresses to connected clients on ports P1–P3 within the `192.168.66.2` to `192.168.66.254/24` range.

#### Access Local Status Page for Static IP Configuration
* **Static IP and PPPoE support**: Use the Local Status Page (LSP) to manually configure WAN settings if your ISP requires a static IP or PPPoE connection.
* **Local access URL**: Connect a PC to port P1, P2, or P3 and navigate to `http://192.168.66.1` or `http://local.engenius` in a web browser.
* **Default credentials**: Access the management interface using the default username and password combination (`admin` / `admin`).
* **VLAN tagging**: Input the required VLAN ID under the connection settings if your ISP requires VLAN-tagged WAN traffic.
* **Web proxy support**: Enter proxy details in the Web Proxy Settings section if your network environment requires a web proxy for internet access.

#### Double Check Device Status on the Local Status Page
* **WAN Network status**: A green indicator confirms an IP address is assigned to WAN1; if inactive, check the physical cable, DHCP server status, and potential IP conflicts.
* **Internet connection verification**: A green indicator verifies WAN1 can access the internet; if inactive, check default gateway reachability and upstream ISP service.
* **EnGenius Cloud status**: A green indicator confirms active cloud management connectivity; if inactive, verify DNS resolution or test ping response to `cloud.engenius.ai`.
* **DNS troubleshooting**: Switch the primary DNS server address to `8.8.8.8` if the device fails to reach the cloud management servers.
* **Device registration options**: Register unlinked gateways using either the EnGenius Cloud To-Go mobile app or the [EnGenius Cloud](https://cloud.engenius.ai) web interface.
<img width="768" height="692" alt="image" src="https://github.com/user-attachments/assets/a04baba3-db20-4a70-932a-5cbfa9a41c96" />

## ESG510 EnGenius Cloud Management
#### Login EnGenius Cloud to Start Management/Provisioning
* **Registration requirement**: Register the ESG510 via the EnGenius Cloud web portal or the Cloud To-Go mobile app before assigning it to an organization.
* **Network assignment**: Assign the registered gateway to a specific network within your organization to initiate cloud management and configuration.
* **Single gateway limit**: Strict limitation of allowing only one ESG security gateway per defined network.
* **Multi-device architecture**: Create separate networks for each gateway if installing multiple ESGs on the same physical site.
* **Portal management**: Select the designated Organization and Network from the EnGenius Cloud portal menu to start configuring gateway features.


#### View Gateway General and Detail Information
* **WAN IP status distinctions**: Access *Manage > Gateway* to view WAN details; if behind a NAT device, Public WAN1 IP reflects the upstream NAT device's address, whereas directly connected setups show identical Public WAN and local WAN IPs.
<img width="759" height="337" alt="image" src="https://github.com/user-attachments/assets/f4596eec-105b-4382-a466-39e2d835e52c" />

* **Sync and topology verification**: Check the device *Details* pane to verify *Configuration Up-to-date* status (confirming synchronization with EnGenius Cloud) and click *Show* next to *Topology* to view network structure.
<img width="768" height="116" alt="image" src="https://github.com/user-attachments/assets/05977d78-a41f-46b2-a5cf-f83425347c2c" />
<img width="768" height="280" alt="image" src="https://github.com/user-attachments/assets/512b569a-6fac-468c-a13f-3ea2c2c5a07f" />

* **WAN performance monitoring**: Navigate to *Manage > Gateway > Detail > WAN* to inspect connection type, uplink/downlink bandwidth, latency, throughput, and historical packet loss data.
<img width="768" height="434" alt="image" src="https://github.com/user-attachments/assets/d253748a-e55e-4407-9b83-8695d786e034" />

* **LAN and DHCP pool tracking**: Review interface IP/subnets under *Manage > Gateway > Detail > LAN* to monitor leased versus free IP counts, and check *DHCP Lease* to track client MAC address assignments and expiration times.
<img width="768" height="185" alt="image" src="https://github.com/user-attachments/assets/bc357a01-33e8-4df7-b057-aae43031f423" />

* **Device location and logs**: View physical placement details and uploaded photos under *Location*, or review time-stamped system logs under *Logs* to troubleshoot uptime and connectivity events.
<img width="550" height="376" alt="image" src="https://github.com/user-attachments/assets/09299d14-ad62-4038-8982-af99afc3f1cd" />
<img width="768" height="278" alt="image" src="https://github.com/user-attachments/assets/6436f871-2725-4355-b65c-3b382966ef0e" />

#### Firmware Management: Beta/Stable/Previous Stable
* **Upgrade scheduling**: Navigate to *Configure > Firmware > Gateway* to view release information and set an automatic upgrade maintenance time window.
* **Beta release access**: Upgrade to Beta firmware immediately by selecting it and clicking *Upgrade Now* to access new features and early bug fixes.
* **Stable version transition**: Beta firmware transitions to Stable after successfully passing testing with at least 10% of Beta users; it upgrades automatically during your scheduled window or via *Upgrade Now*.
* **Firmware rollback**: Select the *Previous Stable* version and click *Upgrade Now* to revert to the prior stable firmware if issues arise with the current release.
<img width="768" height="685" alt="image" src="https://github.com/user-attachments/assets/e11a3f6c-00b6-4a2e-a802-3e40f6785736" />

## Routed and Passthrough Mode
#### ESG Can be Deployed in Routed or Passthrough Mode
* **High-throughput performance**: Delivers 2.5Gbps full-duplex uplink/downlink bandwidth and 2.35Gbps firewall throughput in both deployment modes without creating performance bottlenecks.
* **Routed mode operation**: Functions as a Layer 3 routing device supporting multiple interfaces across different subnets while performing NAT between WAN and LAN.
* **Passthrough mode operation**: Functions as a transparent Layer 2 device that integrates into existing networks without needing IP readdressing.
* **Simplified maintenance**: Reduces troubleshooting complexity in Passthrough mode by eliminating intricate routing setups.

| Feature / Attribute | Routed Mode | Passthrough Mode |
| :--- | :--- | :--- |
| **OSI Layer** | Layer 3 | Layer 2 |
| **Network Role** | Primary edge router / gateway | Transparent bridge |
| **Uplink / Downlink Bandwidth** | 2.5Gbps full-duplex | 2.5Gbps full-duplex |
| **Firewall Throughput** | 2.35Gbps | 2.35Gbps |
| **Key Characteristics** | Performs NAT between WAN and LAN, supports multiple subnets across interfaces, and handles routing. | Integrates into existing networks without IP readdressing or complex routing setup. |

#### One-Arm VPN Concentrator
* **HQ aggregation role**: Deploys typically in data centers or headquarters as a central VPN hub for connecting remote branch offices to local resources.
<img width="768" height="349" alt="image" src="https://github.com/user-attachments/assets/a564a29a-3bb4-4486-b048-088bd3f2b2eb" />

* **Firewall port forwarding**: Requires the external firewall to forward IPsec UDP ports 500 and 4500 directly to the VPN gateway.
* **Upstream static routing**: Demands static routes on the external firewall pointing to the VPN gateway as the next hop for peer site subnets.
* **Simplified gateway routing**: Operates using only a default gateway configuration on the One-Arm VPN gateway without requiring extra static routes.
* **Passthrough benefits**: Combines with Passthrough mode to deliver easy deployment with zero existing network layout changes and up to 970Mbps VPN performance.
<img width="709" height="479" alt="image" src="https://github.com/user-attachments/assets/dfadcb14-8e38-4015-a4a4-9aa2cce41450" />

| Feature / Aspect | Diagram 1 (Standard One-Arm VPN Setup) | Diagram 2 (Passthrough One-Arm VPN Setup) |
| :--- | :--- | :--- |
| **Gateway Mode** | Routed / Standard Mode | Passthrough Mode |
| **Network Integration** | Functions as a dedicated internal VPN gateway behind the firewall. | Integrates transparently as a Layer 2 bridge into the existing network. |
| **IP & Routing Setup** | Requires static routing on the main firewall to direct traffic to the VPN gateway subnet. | Requires minimal to no structural network re-configuration or IP readdressing. |
| **Primary Advantage** | Standard central VPN aggregation hub setup for HQ/Data Centers. | Simplified deployment with zero network layout changes while delivering up to 970 Mbps VPN performance. |

## ESG WAN Configurations
#### Configure WAN1 Configurations
* **Configuration navigation**: Access settings by navigating to *Configure > Gateway > Interface > WAN* in the EnGenius Cloud portal.
* **Operating mode selection**: Toggle between Layer 3 Routed mode and Layer 2 Passthrough mode based on network architecture needs.
* **Connection protocol choices**: Choose between Static IP, PPPoE, or DHCP dynamic assignment depending on ISP requirements.
* **Flexible DNS options**: Select between ISP-provided DNS servers, Google Public DNS (`8.8.8.8` / `8.8.4.4`), or custom-specified nameservers.
* **ISP bandwidth parameter**: Input exact download and upload speeds to accurately calculate bandwidth utilization and Dual WAN load balancing.
<img width="768" height="454" alt="image" src="https://github.com/user-attachments/assets/9c513fb0-ca8e-4d51-acb6-ee2d1cf05271" />

#### Configure WAN2 for Dual WAN Failover/Load Balance Configuration
* **Outbound failover mode**: Configures either WAN as primary for internet access; the secondary WAN stays in standby mode and activates automatically only when the primary WAN link fails.
* **Outbound load balancing**: Uses Weighted Round Robin (WRR) based on ISP upload bandwidth ratios (e.g., 20Mbps vs 6Mbps yields a 10:3 distribution ratio) to balance outbound client sessions.
* **Cellular failover hierarchy**: Automatically activates the USB 3.0 cellular dongle interface as a tertiary backup only when both WAN1 and WAN2 connections fail simultaneously.
<img width="768" height="386" alt="image" src="https://github.com/user-attachments/assets/091aa332-1445-4cef-be84-4b8d303bc83e" />

* **Inbound active/standby services**: Maintains primary WAN dominance for Port Forwarding, 1:1 NAT, and Local Status Page access, automatically switching to standby WAN if primary fails.
* **Inbound VPN manual failover**: Restricts Client VPN and Site-to-Site VPN services to active primary WAN only; secondary WAN requires manual reconfiguration as primary during an outage.
* **Interface configuration path**: Set connection protocols (DHCP/PPPoE/Static), DNS servers, primary WAN interface, and load policy under *Configure > Gateway > Interface > WAN*.
<img width="768" height="341" alt="image" src="https://github.com/user-attachments/assets/bba71414-0bff-44a6-af3b-42ba9fb945db" />
<img width="589" height="547" alt="image" src="https://github.com/user-attachments/assets/9717ea01-98a0-483b-8d61-1e6c51a0357a" />

#### Configure ESG Dynamic DNS Service
* **Automated DNS updates**: DDNS automatically updates A (IPv4) or AAAA (IPv6) DNS records without human intervention when your ISP changes the WAN IP address.
* **Remote access support**: Allows external clients to reach internal servers (via port forwarding) using a fixed hostname instead of a changing public IP address.
* **Provider integration**: Configure preset DDNS services like No-IP or custom providers by navigating to *Configure > Gateway > Interface > WAN*.
* **Custom URL support**: Select *Custom* from the provider menu to manually enter the Update URL according to non-listed provider specifications.
* **Dual WAN failover behavior**: Uses the primary WAN IP for DDNS updates when healthy, and automatically switches to update using the secondary WAN IP if the primary WAN goes down.
<img width="768" height="260" alt="image" src="https://github.com/user-attachments/assets/3f78a2ac-ca4c-4bd4-bfac-d0389a672123" />
<img width="768" height="270" alt="image" src="https://github.com/user-attachments/assets/ab9792fe-35e0-4da8-b075-ff74ca7f7033" />

## ESG LAN/VLAN Configurations
- two modes for the LAN Interface:
  - hybrid
  - multiple bridge
* **Subnet network separation**: Partition downstream hosts into separate broadcast domains using VLANs to isolate network segments and enhance overall security.
* **Multi-gateway operation**: Assign multiple LAN IP addresses to the gateway so each address serves as the default gateway for its respective VLAN.
* **Hybrid port mode**: Supports a single bridge alongside multiple VLANs, allowing the same physical LAN port to be assigned to both a bridge and a VLAN simultaneously.
<img width="505" height="349" alt="image" src="https://github.com/user-attachments/assets/31446984-b7f9-4ba8-94bb-a686f3f989bf" />

* **Multiple bridge mode**: Provides flexibility for multi-untagged subnet environments by operating across multiple untagged subnets (bridges) and tagged subnets (VLANs).
<img width="559" height="348" alt="image" src="https://github.com/user-attachments/assets/9056b9df-546c-4ddb-9c65-42fb3a1e9747" />

* **Port assignment restriction**: Restricts physical LAN ports in Multiple Bridge mode from being assigned to both a bridge and a VLAN at the same time.

```
* **Port capacity constraint**: A single physical port can only carry one untagged subnet (Bridge) because untagged frames lack VLAN headers, preventing the gateway from distinguishing multiple subnets on the same wire.
* **Multiple Bridge port requirement**: Assign each untagged subnet to its own dedicated physical port when using Multiple Bridge mode to avoid IP conflicts and routing failures.
* **Hybrid mode port efficiency**: Combine one untagged network (Bridge) with multiple tagged VLANs on a single physical port in Hybrid Port mode to connect multi-SSID Access Points or managed switches over a single cable.
```

#### Configure LAN Settings
* **Interface navigation**: Access LAN parameters by navigating to *Configure > Gateway > Interface > LAN* and clicking the specific network entry (default is `LAN`).
<img width="764" height="403" alt="image" src="https://github.com/user-attachments/assets/fb8f50f9-306e-421f-99ab-d017910058b5" />

* **Addressing & subnet validation**: Assign the interface *Name* and host *IP Address* (e.g., `192.168.66.1/24`); avoid entering subnet network addresses (e.g., `192.168.66.0/24`).
* **Site-to-Site VPN integration**: Enable *Use VPN* to automatically include the selected LAN subnet within Site-to-Site VPN configurations.
* **Port membership allocation**: Assign or remove physical ports associated with the LAN by toggling the target port icons on the configuration page.
* **Default LAN VLAN constraint**: The factory default LAN is strictly untagged, meaning no VLAN ID customization options are available for it.
<img width="768" height="489" alt="image" src="https://github.com/user-attachments/assets/58270ca6-4d1a-468f-a43f-5327f3d0b4e2" />

#### Configure Multiple Subnets(VLANs)
* **Multi-VLAN topology support**: Create and assign multiple subnets (e.g., VLAN 2 and VLAN 3 alongside default LAN) across gateway physical ports (P1, P2, P3) connected to downstream switches.
<img width="768" height="362" alt="image" src="https://github.com/user-attachments/assets/90f75a07-377b-462c-acf4-8f5d0af12909" />

* **Link aggregation restriction**: Do not connect multiple gateway physical ports simultaneously to the same downstream switch, even if IEEE 802.3ad is enabled, to prevent loop broadcast storms or spanning tree port blocking.
* **VLAN interface creation**: Add new VLANs via *Configure > Gateway > Interface > LAN > (+ Add Interface)* by defining the *Name*, gateway host *IP Address* (e.g., `192.168.30.1/24`), *VLAN ID*, and port assignments.
<img width="581" height="441" alt="image" src="https://github.com/user-attachments/assets/4f02ecf1-e252-4d97-ad1e-a849eceb0b22" />

* **Automatic trunk port mode**: Adding two or more VLANs automatically transforms all gateway LAN ports into VLAN trunk ports.
* **Untagged frame handling**: The default LAN strictly handles untagged Ethernet frames, while all additional VLANs require IEEE 802.1Q VLAN ID tagging; non-default VLAN ports drop incoming untagged frames.
<img width="768" height="461" alt="image" src="https://github.com/user-attachments/assets/de1f1af7-35b9-4e1e-ace6-531fa7e064c4" />

```
You cannot plug an end-user device directly into a port configured only for a non-default VLAN unless a managed switch sits between them to handle the VLAN tagging.
```

#### Firewall Basics: DHCP and DHCP Relay
* **DHCP DORA transaction**: Assigns IP addresses dynamically via a four-step broadcast handshake (**D**iscover, **O**ffer, **R**equest, **A**cknowledge) between the host and a local DHCP server within the same broadcast domain.
<img width="694" height="412" alt="image" src="https://github.com/user-attachments/assets/a77324af-6051-48ef-bc91-c543dbf70ad0" />

* **DHCP Relay necessity**: Eliminates the requirement for dedicated DHCP servers on every VLAN by forwarding DHCP requests across different subnets to a centralized DHCP server.
* **Gateway packet modification**: Sets the gateway interface address (*giaddr*) field on the router interface to the primary IP address of the receiving subnet before relaying unicast requests to external DHCP servers.
* **Subnet pool matching**: Enables the centralized DHCP server to allocate appropriate IP addresses from specific pools (e.g., `10.0.10.x/24`, `10.0.20.x/24`, `10.0.30.x/24`) based on the incoming *giaddr* tag.
<img width="768" height="397" alt="image" src="https://github.com/user-attachments/assets/312091e7-6322-4ac8-b963-8c41d4bdc6f8" />

#### ESG510 DHCP (Client Addressing Mode)
* **DHCP Server mode**: Enables the ESG gateway LAN IP to act as the primary local DHCP server for the specified VLAN.
* **Disable DHCP Server mode**: Turns off internal DHCP server functions on the VLAN to allow a local external DHCP server on the same subnet to handle IP assignments.
* **Relay DHCP mode**: Configures the gateway LAN IP as a DHCP Relay agent to forward client requests across subnets to one or more external DHCP servers for redundancy.
* **Relay co-existence restriction**: Requires all other VLANs to either disable DHCP or run DHCP Relay if at least one VLAN on the gateway has DHCP Relay enabled.
<img width="768" height="358" alt="image" src="https://github.com/user-attachments/assets/eb5f6167-facb-427f-b6f6-01130ddc0889" />





