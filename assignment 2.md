1. Split MAC architecture & how it improves AP performance

Split MAC means the Wi-Fi MAC functions are divided between AP and controller.

AP handles time-critical tasks (beacons, ACKs, encryption)
WLC handles decision tasks (authentication, policies, roaming)

Improvement:
AP is less loaded → better performance
Centralized control → easier management
Faster roaming → better user experience
AP does fast work, WLC does smart work

2. CAPWAP & flow between AP and Controller

CAPWAP = protocol used for communication between AP and WLC.

Uses:
UDP 5246 → Control
UDP 5247 → Data
Flow:
AP gets IP (DHCP)
AP discovers WLC (DHCP option 43 / DNS / broadcast)
AP sends Join Request
WLC authenticates AP (certificate)
CAPWAP tunnel forms
AP downloads config and becomes active

3. CAPWAP in OSI model + tunnels
 CAPWAP works at:

Application layer (L7) but runs over UDP (Transport layer)
Two tunnels:
Control Tunnel
AP ↔ WLC communication
Config, join, heartbeat
Data Tunnel
Client traffic
Used in central switching mode

4. Lightweight AP vs Cloud AP
Lightweight AP:
Needs local controller (WLC)
Uses CAPWAP
Used in enterprises
Cloud AP:
Controller is in cloud
Managed via dashboard
No CAPWAP (usually HTTPS)

Simple:
Lightweight → Controller in office
Cloud → Controller in internet

5. How CAPWAP tunnel is maintained
Uses keepalive/heartbeat messages
AP and WLC continuously exchange control packets
If no response:
AP assumes WLC is down
Tries to rejoin or find another controller

6. Sniffer mode vs Monitor mode
Sniffer Mode:
Captures packets on a specific channel
Used for debugging traffic (Wireshark)
Use case:
Packet analysis
Troubleshooting client issues
Monitor Mode:
Scans all channels
Detects rogue APs and interference
Use case:
Security monitoring
RF analysis

7. WLC in WAN – best AP mode
Best mode: FlexConnect (Local Switching)
Why:
Client traffic stays local (doesn’t go to WLC over WAN)
Only control traffic goes to WLC
Benefit:
Saves bandwidth
Works even if WAN is slow

8. Challenges with Autonomous APs (50+ APs)
 No centralized management
 Need to configure each AP manually
 No seamless roaming
 No RF optimization
 Hard to troubleshoot
Real issue:
Changing SSID → need to update 50 APs manually 

9. What happens if WLC goes down (Local mode)
 In Local mode (central switching):

AP loses CAPWAP tunnel
Clients disconnect 
No authentication or traffic flow

 Because:
All control + data depends on WLC

 If it was FlexConnect:
Clients may still work (local switching)