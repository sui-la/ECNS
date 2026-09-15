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

#### Configure ESG LAN DHCP Client Addressing Mode
* **Configuration navigation**: Select the target VLAN under *Configure > Gateway > Interface > LAN* and locate the *DHCP* settings section.
* **Server Mode setup**: Choose *DHCP Server* to configure the local IP pool, lease time, gateway IP, and primary/secondary DNS options directly on the gateway.
* **Relay Mode setup**: Select *Relay DHCP* and specify the target IP address of your central external DHCP server so the gateway can forward client requests across subnets.
* **Relay IP verification**: Ensure the destination Relay IP address is reachable from the gateway interface to prevent cross-subnet DHCP request drops.
<img width="593" height="314" alt="image" src="https://github.com/user-attachments/assets/e26c3f05-7568-4c56-9762-8aaba80b0493" />

```
**The Big Risk: "Rogue DHCP Servers"**
If you accidentally run two independent DHCP servers on the same VLAN that aren't synced or configured for failover, they will race to assign IP addresses. This causes IP address conflicts, wrong default gateways, and broken internet access for your devices.
```

#### Configure ESG LAN Captive Portal
* **Captive portal definition**: Intercepts user HTTP/HTTPS requests on public-access or guest networks, forcing interaction with a web landing page before granting internet access.
* **DNS configuration prerequisite**: Requires client DNS to be set to the ESG LAN IP to ensure web URL redirection functions correctly.
* **Click-through mode**: Redirects clients to an ESG landing page where clicking "Continue to Internet" grants access, redirecting to the original URL or a designated landing page.
<img width="768" height="443" alt="image" src="https://github.com/user-attachments/assets/886e81a1-8d04-4338-a13d-2adf72ffbbc3" />

* **Custom RADIUS authentication mode**: Uses an external RADIUS server (supports up to 2 for redundancy) to authenticate users via a credential prompt before granting access.
<img width="768" height="553" alt="image" src="https://github.com/user-attachments/assets/18b020fd-e47f-4184-86c6-34f7cf9a841a" />

* **Session and idle timeouts**: Re-enforces portal authentication when session limits (default 60 min) or inactivity thresholds (default 30 min) are reached.

## Configure Static Route
* **Layer 3 switch interworking**: Integrates ESG in routed mode with downstream external L3 switches to handle complex internal subnet routing requirements.
* **Static route declaration**: Directs traffic for internal subnets (e.g., `10.10.1.0/24` and `10.10.2.0/24`) by setting the ESG static route next-hop IP to the L3 switch interface (`192.168.1.2`).
* **Default route return path**: Requires configuring a default route (`0.0.0.0/0`) on the external L3 switch pointing to the ESG LAN IP (`192.168.1.1`) for outbound internet access.
* **Configuration navigation**: Create static routing rules by navigating to *Configure > Gateway > Interface > Static Route* and selecting *+Add Rule*.
<img width="768" height="285" alt="image" src="https://github.com/user-attachments/assets/fdaaa167-cf61-4d74-ac5a-d340130a9c54" />

## Policy Routes
#### Layer 3 and Layer 7 Policy-Based Routing
> Layer 3 Policy-Based Routing (PBR):
- Definition: Utilizes IP addresses and network masks to make routing decisions.
- Use Cases: Enables routing of traffic based on source and destination IP, protocol type.
- Advantages: Enhances network performance and control by directing traffic to preferred paths.

> Layer 7 Policy-Based Routing:
- Definition: Makes routing decisions based on application-level information, such as HTTP headers.
- Use Cases: Prioritizes specific application traffic like streaming or VoIP, providing quality of service.
- Advantages: Offers granular control and improved service levels based on content types.

* **Layer 3 PBR**: Makes routing decisions using IP addresses, network masks, and protocol types to direct traffic over preferred paths for optimized performance.
* **Layer 7 PBR**: Uses application-level parameters (e.g., HTTP headers) to prioritize traffic like VoIP or streaming, enforcing granular Quality of Service (QoS).
* **Key PBR benefits**: Optimizes bandwidth usage, enhances security by isolating sensitive traffic, enables dynamic path selection, and cuts costs by steering non-critical traffic to cheaper links.
* **Network efficiency & QoS**: Optimizes overall bandwidth utilization by directing critical traffic across preferred links while preventing network congestion.
* **Enhanced path security**: Enforces security policies by explicitly routing sensitive internal data traffic across dedicated secure paths or security appliances.
* **Cost management**: Reduces operational costs by steering non-critical background traffic over lower-cost WAN links while saving primary links for priority traffic.
* **PBR vs. Static Routing**: Static routing makes decisions based strictly on destination IP address using fixed tables, whereas PBR evaluates multi-criteria policies (source IP, application type, QoS requirements) for flexible traffic control.
<img width="676" height="366" alt="image" src="https://github.com/user-attachments/assets/00cc706f-d404-4514-a9be-ff1c9ad54f1a" />

| | Routing method | Routing decisions | Flexibility | Control & use cases | Limitations |
| ----- | ----- | ----- | ----- | ----- | ----- |
| 1 | Policy-based routing (PBR) | Based on defined policies using source/destination IP, application types, and protocols | High flexibility; dynamically adapts to changing network conditions and reroutes traffic | Provides granular control to prioritize mission-critical applications (VoIP, streaming) and enforce security | — |
| 2 | Static routing | Based on fixed routing tables configured manually by network administrators | Low flexibility; routes are predefined and remain constant unless manually adjusted | Simple and predictable routing for small, stable networks | Lacks dynamic failover; requires manual intervention if a link goes down |

#### Configure Policy Routes in Cloud Gateway
* **Configuration path**: Access Layer 7 policy routes via *Configure > Gateway > Interface > Policy Route > Layer 7 > Add Rule*.
* **SaaS traffic prioritization**: Optimize network efficiency by prioritizing essential cloud applications (e.g., Gmail, Windows 365, Salesforce) over general web browsing.
* **Dual WAN traffic steering**: Route standard enterprise traffic over WAN1 (primary link) while establishing WAN2 as an active failover or backup interface to ensure business continuity during WAN1 congestion or link failure.
* **Granular L7 rule application**: Direct traffic based on broad application categories or target specific applications within a category to route through designated WAN interfaces.
<img width="768" height="348" alt="image" src="https://github.com/user-attachments/assets/0466dde0-01f2-4f40-a4b1-7789e03b0bd1" />
<img width="768" height="372" alt="image" src="https://github.com/user-attachments/assets/55885651-3e72-44b1-a294-c91d7576c35d" />

## Site-to-Site VPN
#### Site-to-Site VPN Basic Concept and Applications
* **Private connection over Internet**: Encrypts traffic between two or more distinct networks (e.g., corporate HQ and branch offices) to securely share resources as a single unified network over standard Internet connections.
* **Cost-effective Multiprotocol Label Switching(MPLS) alternative**: Leverages public Internet infrastructure for private traffic routing instead of relying on expensive dedicated private MPLS circuits.
* **Packet encapsulation & encryption**: Encapsulates and encrypts internal private IP packets inside an outer public IP header at the firewall/VPN gateway before transmitting securely across the Internet.
* **Multi-office resource sharing**: Enables continuous cross-geographic communication and resource sharing for organizations operating multiple remote office locations.

#### Configure Site-to-Site VPN for ESGs in Different Organizations or 3rd Party
* **Non-EnGenius gateway configuration**: Navigate to *Configure > Gateway > Site to Site VPN > Add Non-EnGenius Gateway* to establish IPsec tunnels between ESGs in different organizations or with third-party VPN devices.
<img width="768" height="359" alt="image" src="https://github.com/user-attachments/assets/0061bb11-e432-4497-b04d-30997afac7a6" />

* **Public WAN IP specification**: Enter the peer device's native public WAN IP, or its mapped public NAT IP if the peer sits behind an external NAT router or firewall.
* **Remote ID consistency**: Match the Remote ID strictly to the peer's public WAN IP address; never use the peer's private WAN IP as the Remote ID when behind NAT.
* **Bidirectional setup requirement**: Perform identical peer configuration steps on both local and remote VPN devices to complete IPsec tunnel setup.
* **Tunnel status verification**: Check *Manage > VPN Status > Non-EnGenius Peers* for a green vertical bar indicating an active tunnel, or inspect *Analyze > Event Log > Device Event* for connection logs.
<img width="768" height="346" alt="image" src="https://github.com/user-attachments/assets/5c4ab5a4-812a-4f8f-a401-5ccacf0d78b6" />

#### Auto VPN: Configure Site-to-Site VPN with Few Clicks
* **Auto VPN simplification**: Provides rapid, automated Site-to-Site VPN provisioning for ESGs within the same organization without requiring manual IPsec Phase 1 and Phase 2 configurations.
* **Subnet VPN enablement**: Requires checking the *Use VPN* option for any local subnets that need to be accessible across the VPN tunnels.
* **ESG participation configuration**: Toggle *Site to Site VPN* on each ESG and define the topology type (*Mesh VPN* as a Hub or *Hub-and-Spoke* as a Spoke), local subnets, and NAT Traversal settings.
<img width="748" height="727" alt="image" src="https://github.com/user-attachments/assets/5dc3194f-9d3f-44e6-a545-d130fb3020f6" />

* **NAT Traversal modes**: Supports *Automatic* NAT traversal (requires PRO License) or *Manual: Port Forwarding*.
* **Supported VPN topologies**: Supports **Mesh VPN** (all participating ESGs configured as Hub nodes), **Hub-and-Spoke** (1 central Hub node with multiple Spoke nodes), or a **Mixed Topology** combining both structures across an organization.
<img width="768" height="316" alt="image" src="https://github.com/user-attachments/assets/bcadbd74-bfe5-4bf8-aac4-994eaa3cc5df" />

* **Full subnet connectivity**: Automatically establishes IPsec tunnels connecting all selected, directly connected local LAN subnets across participating gateway nodes once deployed.
<img width="768" height="382" alt="image" src="https://github.com/user-attachments/assets/f5db2aa1-43c7-4b2b-b8c7-a3500a99ed7a" />

#### EnGenius Auto VPN NAT Traversal: Auto WAN IP Refresh
* **Dynamic WAN IP flexibility**: Supports ESG deployments using fixed or dynamic public WAN IPs directly, or positioned behind external NAT devices.
* **Cloud-managed IP tracking**: EnGenius Cloud dynamically tracks each ESG’s public WAN IP and port mapping table, automatically pushing updates to VPN peers if a dynamic IP changes to maintain continuous tunnel connectivity.
* **Auto VPN setup path**: Enable Site-to-Site VPN via *Configure > Gateway > Site to Site VPN*, select the network topology (Mesh Hub or Hub-and-Spoke Spoke), assign local subnets with *Use VPN*, and set *NAT Traversal* to *Automatic*.
<img width="768" height="365" alt="image" src="https://github.com/user-attachments/assets/befb03ff-3078-40b2-ba05-07e259cba63e" />
<img width="768" height="365" alt="image" src="https://github.com/user-attachments/assets/265a0dd7-9066-484e-a35a-dda61bd2039c" />

* **Tunnel verification**: Verify active VPN tunnels in *Manage > VPN Status > EnGenius Peers* (indicated by a green vertical status bar) or inspect events in *Analyze > Event Log > Device Event*.
<img width="768" height="355" alt="image" src="https://github.com/user-attachments/assets/3e1420b7-3dd6-49fe-bdab-9085cb937ea2" />
<img width="768" height="321" alt="image" src="https://github.com/user-attachments/assets/6e7411c8-8ce5-4de2-92c9-e8d49821b1d2" />
<img width="768" height="428" alt="image" src="https://github.com/user-attachments/assets/2d9fb00a-e3c3-4f47-8768-da11de70360c" />

* **License requirement**: Automatic NAT Traversal strictly requires an EnGenius **PRO License** and is not supported on the Basic License.

#### Permissive and Symmetric NAT
* **Permissive vs. Symmetric NAT**: Permissive NAT reuses the same public IP address and port mapping for different destinations, whereas Symmetric NAT assigns unique IP:Port mappings per destination, preventing mapping reuse.
<img width="768" height="381" alt="image" src="https://github.com/user-attachments/assets/8b3d5c14-9fc2-494a-894e-3242cac35beb" />

* **Automatic NAT Traversal limitation**: ESG Auto VPN with Automatic NAT Traversal fails when operating behind an external Symmetric NAT device.
* **Manual Port Forwarding fallback**: Devices behind Symmetric NAT must set NAT Traversal to *Manual: Port Forwarding*, set the Public IP & Port to `External NAT Public IP: 500`, and forward inbound **UDP 500** and **UDP 4500** on the external router to the ESG WAN IP.
* **Control and data plane firewall requirements**: ESG utilizes source UDP 500/4500 and destination UDP 500/4500 for IPsec control plane and data plane sessions; external NAT devices must explicitly permit outbound traffic on these UDP ports.
<img width="768" height="338" alt="image" src="https://github.com/user-attachments/assets/06cbe9d3-9724-4f5a-87d6-378498a023ca" />

#### Site-to-Site VPN Outbound Rules
* **Default VPN traffic routing**: Establishes full cross-subnet communication across all selected local LAN subnets (with *Use VPN* enabled) by default once a Site-to-Site VPN tunnel connects participating ESGs.
* **Access control enforcement**: Restricts unauthorized or undesired cross-site traffic by configuring granular firewall policies via *Configure > Gateway > Site to Site VPN > Setting > VPN Outbound Rules*.
* **Protocol-level blocking example**: Enables target IP- and service-specific restrictions (e.g., blocking Telnet access to an L2 switch at `192.168.66.200` on *Site#2* from any host inside *Site#1*'s `192.168.67.0/24` subnet).

## Client VPN
#### Firewall Basics: IPsec Remote Access
* **Remote user connectivity**: Establishes secure, encrypted IPsec tunnels for roaming users to access internal corporate network resources remotely over standard Internet connections.
* **Client IP pool requirement**: Requires configuring a dedicated IP address pool on the firewall to dynamically assign private IP addresses to authenticated remote client PCs.
* **Unified user experience**: Grants remote devices direct private network access via client VPN software, matching the on-premise office network experience once authentication passes.
<img width="768" height="321" alt="image" src="https://github.com/user-attachments/assets/bff129ef-4247-4ae0-8819-a2fa807f64eb" />

#### Configure ESG Client VPN
* **Configuration path**: Access Client VPN settings via *Configure > Gateway > Client VPN* with support for **IPsec** or **EnGenius SecuPoint**.
<img width="768" height="376" alt="image" src="https://github.com/user-attachments/assets/59b90833-f8e1-4f1d-a30a-350040678375" />
<img width="768" height="382" alt="image" src="https://github.com/user-attachments/assets/657114bf-5149-4aee-b9dd-ebe93a05838d" />

* **Hostname & NAT forwarding**: Automatically displays the Primary WAN Public IP or FQDN; if the WAN is behind an external NAT router, configure 1:1 NAT or forward **UDP 500/4500** (IPsec) or **TCP 443 / UDP 1194** (SecuPoint) to the ESG WAN IP.
* **VPN Client Subnet allocation**: Requires a non-overlapping subnet dedicated to assigning IP addresses to remote clients upon successful tunnel establishment.
* **DNS configuration**: Requires setting DNS servers (Google Public DNS or corporate internal DNS) to handle remote intranet name resolution.
* **Authentication setup**: Supports local ESG user authentication (**ESG VPN User**) configured via *Configure > Users > ESG VPN Users*, along with a Pre-Shared Key for IPsec tunnel authentication.
<img width="768" height="382" alt="image" src="https://github.com/user-attachments/assets/cdfea037-a75d-4941-a31b-ba5a4e6d7459" />

* **SecuPoint client routing modes**:
  * **Send all client traffic through VPN (Full Tunnel)**: Routes all internet and internal traffic through the tunnel for total security compliance, though it increases server bandwidth and latency.
  * **Only send traffic to ESG LAN through VPN (Split Tunnel)**: Routes only corporate internal traffic through the tunnel while keeping standard internet browsing on the client's local gateway.
<img width="768" height="441" alt="image" src="https://github.com/user-attachments/assets/d7e4a6fd-a1f2-486c-8c86-7cc92fd5abe6" />

#### VPN Client using Shrew VPN Client on Windows 10 as an example
Markdown
#### 10.3 VPN Client Setup using Shrew VPN Client on Windows 10
* **DDNS for dynamic WAN IP**: Configures dynamic DNS (e.g., `ntkevinshao.ddns.net`) on the ESG so remote clients can establish connections without needing a static public WAN IP address.
* **Host Name entry**: Uses the ESG DDNS domain name in the Shrew VPN Client host configuration field to automatically target the gateway's active public IP address.
* **Split Tunneling configuration**: Disables *Obtain Topology Automatically* / *Tunnel All* in Shrew VPN Client and manually specifies the *Remote Network Resource* to route only targeted intranet subnets through the tunnel.
* **Routing table behavior**: Assigns a client IP (e.g., `10.10.11.1/24`) and adds a dedicated static route to the internal network (e.g., `192.168.66.0/24`) via the IPsec tunnel interface while leaving the default internet route unchanged.
<img width="768" height="357" alt="image" src="https://github.com/user-attachments/assets/c2085693-0d54-441b-a10a-9b5b9d02aadf" />
<img width="768" height="355" alt="image" src="https://github.com/user-attachments/assets/213bfac3-edfb-4a66-bccd-dc5ba101acca" />
<img width="900" height="420" alt="image" src="https://github.com/user-attachments/assets/ee515257-0121-413d-9d4d-7402d11408e3" />
<img width="768" height="406" alt="image" src="https://github.com/user-attachments/assets/81cff99d-f1f2-4c80-9be7-8a203ae48b3e" />
<img width="768" height="376" alt="image" src="https://github.com/user-attachments/assets/69fab2c3-c070-4e1e-87c0-f013bb5f9e0d" />

#### VPN Client Setup using iPad native VPN client as an example
* **Native iOS/iPadOS integration**: Establishes remote IPsec client VPN connections directly through the iPad's built-in native VPN settings without requiring third-party client software.
* **On-premise user experience**: Delivers seamless remote access identical to being physically connected on-site once the client VPN tunnel is established.
* **Intranet utility testing**: Enables iOS network tools to perform direct internal management tasks across the tunnel, such as using *iNetTools* to ICMP ping internal devices (e.g., L2 Switch at `192.168.66.200`) or *iTerminal* to Telnet directly into LAN switch management interfaces.
<img width="768" height="380" alt="image" src="https://github.com/user-attachments/assets/f9a1360f-dc68-473d-bd71-925fb3ac1300" />
<img width="768" height="376" alt="image" src="https://github.com/user-attachments/assets/a47f3307-44be-4bda-88e7-3c1c4957c67f" />

#### EnGenius SecuPoint VPN Client Setup
* **Automated profile provisioning**: Pushes VPN configurations automatically from the EnGenius gateway to the SecuPoint client app, eliminating complex manual IPsec/SSL setup.
* **Profile creation**: Click **Add** in the SecuPoint client and enter a custom profile name alongside the domain, Primary WAN Public IP, or FQDN displayed on the EnGenius Cloud VPN Client page.
* **User authentication**: Click **Connect** and enter the cloud-configured ESG VPN user credentials (e.g., `johndoe`) to authenticate and establish the VPN connection.
* **Dynamic address acquisition**: Displays real-time status transitions (*Connecting to Server* -> *Acquiring IP*) until full tunnel connectivity and client IP assignment are complete.
<img width="585" height="365" alt="image" src="https://github.com/user-attachments/assets/aed808d0-b0f2-4c1b-a01a-df5991375f32" />
<img width="463" height="306" alt="image" src="https://github.com/user-attachments/assets/18386c97-9cb3-4160-bd98-85d31e4b7547" />
<img width="582" height="368" alt="image" src="https://github.com/user-attachments/assets/d54db077-320b-440c-ae45-6452a0f4af84" />
<img width="323" height="287" alt="image" src="https://github.com/user-attachments/assets/499753af-927c-49bd-a1d7-82bcc5b24404" />
<img width="456" height="245" alt="image" src="https://github.com/user-attachments/assets/5d838ad0-0a4c-4fb6-939f-680abcf203f1" />
<img width="460" height="246" alt="image" src="https://github.com/user-attachments/assets/49183296-ff42-4031-9837-e70a070a9dbc" />
<img width="527" height="685" alt="image" src="https://github.com/user-attachments/assets/3c790bfd-a093-4b7d-818f-4f32440cab53" />

## Configure ESG Firewall Rules
#### Firewall Basics: Enforcing Access Control
> For example, a company has three servers: General Web Server, Restricted File Server and a Restricted ERP Server. If the security policy is: John can access General Web Server only; Mary can access all three servers. Then you should configure your firewall rules like the example diagram below.
<img width="768" height="392" alt="image" src="https://github.com/user-attachments/assets/7d7c9f3c-72d0-41c4-acb3-2ccd6628201a" />

#### Firewall Basics: NAT Router
**NAT** - translate a local private IP address to a public WAN address of the router
<img width="768" height="302" alt="image" src="https://github.com/user-attachments/assets/8199f909-1378-4694-b443-07f0b04ab445" />

#### Firewall Basics: NAPT (Network Address Port Translation)
* **Multi-host IP sharing**: Translates and maps both IP addresses and port numbers, allowing multiple internal private IP clients to share a single public IP address for simultaneous Internet access.
* **Public IP conservation**: Minimizes the number of public IP addresses required by dynamically multiplexing traffic across unique source ports.
* **NAT vs. Access Control**: Operating strictly as a translation mechanism at the edge (like a standard NAT router), NAPT handles port translation without enforcing traffic access control policies on its own.
* **Translation table mapping**: Maintains a NAPT table tracking internal source IP/port combinations and mapping them to the single translated public IP with unique source ports to properly route incoming return traffic.
<img width="768" height="314" alt="image" src="https://github.com/user-attachments/assets/ab5ce98e-e6e8-4687-9a0a-62728dd42aa0" />

#### Firewall Basics: Internal/DMZ/External
* **Network zone isolation**: Serves as a security boundary providing managed connectivity between networks with varying trust levels (Internal, DMZ, External).
* **Security policy enforcement**: Controls and regulates all traffic flows passing between distinct network security zones according to corporate policy.
* **Outbound network access**: Allows clients inside the trusted internal network to freely initiate outbound connections to the Internet.
* **Inbound traffic restriction**: Blocks external clients on the public Internet from initiating unauthorized inbound connections directly into the internal network.
* **DMZ server hosting**: Isolates publicly accessible services (e.g., corporate web servers, FTP servers) inside a Demilitarized Zone (DMZ) so external users can access them without exposing the internal private network.
<img width="768" height="396" alt="image" src="https://github.com/user-attachments/assets/dd07afbd-f6f1-4d21-85c7-4d1043238820" />

#### Firewall Basics: 1:1 NAT
* **DMZ server accessibility**: Uses 1:1 NAT to allow external Internet clients to securely access DMZ servers hosted on private IP addresses via a Virtual IP (VIP).
* **Destination IP translation**: Translates only the external destination Virtual IP (e.g., `200.2.2.3`) to the target server's internal private IP (e.g., `10.1.1.1`) upon receiving inbound packets.
* **Destination port preservation**: Keeps the destination port completely unchanged during translation without modifying port parameters.
* **ESG WAN IP restriction**: Avoid using the ESG’s primary WAN IP as the external Virtual IP for 1:1 NAT, as doing so will disrupt the gateway’s own network communications.
<img width="768" height="198" alt="image" src="https://github.com/user-attachments/assets/36ace225-ac76-42d7-9e28-de00e582879c" />

#### Firewall Basics: Create a DMZ on ESG
<img width="544" height="438" alt="image" src="https://github.com/user-attachments/assets/646ae87c-db9c-4bf9-ae91-60cafffdc28a" />

#### Configure firewall outbound rules on ESG
* **Configuration path**: Manage traffic rules via *Configure > Gateway > Firewall > Outbound Rules*.
* **Outbound & inter-VLAN control**: Manages outbound Internet access and enforces access control across inter-VLAN traffic (which is allowed by default).
* **Rule evaluation order**: Evaluates custom rules sequentially before the default **Allow Any** rule; outbound rules apply to all ingress traffic across all VLANs.
* **Deny All precaution**: Adding a broad *Deny Any* rule blocks local client network and Internet access while leaving the ESG connected to EnGenius Cloud (recovery requires deleting the rule via an alternate connection).
> In case this happens, you have to do the following:
  - Login to EnGenius Cloud and delete the deny any rule before the default “allow any” rule via another Internet source as the local one was blocked by the rule.
  - Wait for 5-10 minutes for the configuration changes to take effect.
  - Local clients should be able to regain access to the network and the internet.
<img width="768" height="389" alt="image" src="https://github.com/user-attachments/assets/fddcd232-c1fc-428c-b051-6b53f2e5a46a" />

* **Layer 7 outbound blocking (PRO License)**: Blocks application traffic by category or specific application (e.g., streaming, Apple Music) without relying on fixed IP addresses or ports.
* **Encrypted traffic limitations**: Layer 7 inspection fails to block applications using encrypted tunnels (e.g., client VPNs or iCloud Private Relay).
<img width="768" height="310" alt="image" src="https://github.com/user-attachments/assets/f696c545-e959-4523-b9f4-ace02ca748fb" />
<img width="768" height="380" alt="image" src="https://github.com/user-attachments/assets/0bbd1dc6-c7eb-4dd5-8ed9-880390037112" />

#### Configure Firewall Inbound Port Forwarding Services on ESG
* **Configuration path**: Set up inbound destination port translation via *Configure > Gateway > Firewall > Port Forwarding*.
* **Remote management access**: Allows external users to connect to internal devices (e.g., Telnet into a switch at `192.168.66.200`) via WAN public IPs without requiring a client VPN connection.
* **Destination port translation**: Supports keeping the original external destination port unchanged or translating it to a different internal port (e.g., mapping external TCP 80 to internal TCP 8080).
* **Dynamic WAN IP integration**: Pairs with ESG DDNS (e.g., `ntkevinshao.ddns.net`) to maintain reliable remote domain access when the gateway's public WAN IP changes dynamically.
  > ISP gives router new IP → Router detects its own new IP → Router pushes the update to DDNS server
<img width="768" height="382" alt="image" src="https://github.com/user-attachments/assets/9bd887f7-bd36-440a-82e1-6b2244a10722" />

* **Public IP efficiency**: Shares a **single public WAN IP** across **multiple internal servers** by assigning unique external service ports (e.g., mapping port 80 to Server 1 and port 81 to Server 2).
* **Multi-WAN binding options**: Binds port forwarding rules to WAN1, WAN2, or WAN1 & WAN2 (where the secondary WAN automatically activates as a failover if the primary link goes down).
* **Gateway service port conflicts**: Port forwarding rules override internal ESG services using the same port (e.g., forwarding WAN IP TCP 80 to an internal server disables local ESG Web Status access on port 80).
<img width="768" height="395" alt="image" src="https://github.com/user-attachments/assets/38580e9a-0c37-4119-8ebd-ef8c19ab789b" />

#### Configure Firewall 1:1 NAT Services on ESG
* **Configuration path**: Manage dedicated single-IP mappings via *Configure > Gateway > Firewall > 1:1 NAT*.
* **Scalability over Port Forwarding**: Eliminates destination port management complexity when hosting multiple internal servers by assigning dedicated public IP addresses provided by your ISP.
* **Dedicated IP allocation**: Assigns individual public IP addresses to mission-critical servers (e.g., mapping external `200.2.2.3` directly to internal server `192.168.66.100/24`).
* **Destination IP translation**: Translates inbound packets targeting the Virtual IP (`200.2.2.3`) to the private IP (`192.168.66.100`) while keeping the destination port number completely unchanged.
* **Simplified user access**: Allows clients to access services via standard protocols (e.g., `http://200.2.2.3` or assigned domain names) without appending custom port numbers.
<img width="768" height="386" alt="image" src="https://github.com/user-attachments/assets/79ec2128-f166-4515-ad1d-a4ea6b64eec4" />

#### Configure Firewall Allowed Services on ESG
* **Configuration path**: Manage remote gateway service access via *Configure > Gateway > Firewall > Allowed Services*.
* **Supported WAN access services**: 
  * **ICMP Ping**: Allows the ESG WAN interface IP to respond to ping requests from external networks.
  * **Web (local status & configuration)**: Allows remote access to the ESG Local Status Page (LSP) over the WAN interface.
* **Allowed Remote IP restriction**: Restricts WAN access for ICMP Ping and Web status to specified remote IP addresses; remote IP addresses is set to *none* by default for maximum security.
* **Port forwarding collision restriction**: Overriding TCP Port 80 via Port Forwarding (e.g., mapping `Primary WAN IP:80` to an internal server) disables remote Web status page access even if the feature is enabled.
<img width="768" height="286" alt="image" src="https://github.com/user-attachments/assets/dbf48b39-f97d-4bed-bf78-6287c347d3c1" />
