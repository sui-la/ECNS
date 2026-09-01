## EnGenius Certified Network Specialist

### EnGenius Cloud
- a dashboard that can use to manage different network devices (switches, APs, End Devices) from company and departments

1. register the APs and Switches
- find <img width="92" height="87" alt="Screenshot 2026-09-01 160353" src="https://github.com/user-attachments/assets/f71ab4a2-e039-41a2-bd62-13856303cde0" />

- manual key in or scan qr to register the network device

2. manage access point
- need to register the AP

3. SSID configuration

4. Captive Portal & Authentication Methods
- Click-through:
  - Users must view and acknowledge your splash page before being allowed on the network.
- EnGenius Authentication:
  - Users must enter a username and password before being allowed on the network. You could edit user settings through Configure > Cloud RADIUS User.
- Custom RADIUS:
  - Enter the host (IP address of your RADIUS server, reachable from the access points), port (UDP port the RADIUS server listens on for access requests, 1812 by default), and secret (RADIUS client shared secret). Optionally, the Accounting Server can be enabled on an SSID that's using WPA2-Enterprise with RADIUS authentication.
- Voucher Service:
  - Edit the access plan for guests for the front-desk manager.
- Social Login:
  - Allows users to use a Facebook account to access WiFi.
- Facebook WiFi:
  - Allows users to use a Facebook page account to access WiFi, You can use your Facebook page as the sign-in page when they first log in to your network. Users can then check in with their Facebook credentials, update their status, and ‘like’ the Facebook page.

5. Radio Settings
- Minimum Bit Rate / Roaming
  - kick weak RSSI devices so client roam to stronger APs
  - High bit-rate thresholds require higher AP density,  

- Client Limit
  - maximum of 254 client per AP

- Discard 802.11a/b/g
  - to increase the performance of 802.11ac/ax clients

- Disabling 11ax on 2.4 GHz
  - for clients that incompatible with Wi-Fi 6 (11ax)
- Dynamic Channel Selection (DCS)
  - Monitors traffic/noise via background scanning
  - automatically shifts AP to a cleaner channel WHEN noise/utilization > 50% for 15 minutes
  - Use Case: High-interference environments with unpredictable RF conditions
  - Key Considerations:
    - Causes brief client disconnections during channel hops (can impact real-time traffic like VoIP/video).
    - Requires AP Radio Channel to be set to Auto
    - Supported on firmware V1.X.35 or higher
6. Switch Configuration
- need to register the switch

7. VLAN setup
- tagged (trunk)
  - normally connected between switches, routers

- untagged (Access Ports)
  - normally connected to the end users

8. Pro Feature
a. client timeline
- can track and troubleshoot client network problems by timelines
- in the client list

b. MyPSK (pre-shared key)
- 1 LAN 1 key
- to secure and prevent interruption of WIFI within a VLAN
- in the ssid configuration (security type) can `tick the mypsk box`
- max 500 users can be created

c. AirGuard
- wireless security system 24/7
- protect enterprise network from threats
- WIDS, WIPS
- set rules
- 
