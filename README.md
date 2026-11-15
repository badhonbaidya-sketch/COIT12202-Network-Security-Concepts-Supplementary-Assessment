## SS1 — GNS3 Network Topology

The starter GNS3 project contains four nodes: LAN-Host, VPNServer, Internet and Client. This topology is used to configure a secure HTTPS web server and establish a WireGuard VPN connection between the remote Client and the private LAN.
<img width="959" height="565" alt="image" src="https://github.com/user-attachments/assets/ce5bc680-ff34-472d-b949-22695ada961d" />

## SS2 — Initial Network Connectivity

I tested the initial network connectivity using ping commands. The purpose was to confirm that Client could communicate with the public VPNServer address while the private LAN remained inaccessible before the WireGuard tunnel was established.
<img width="959" height="562" alt="image" src="https://github.com/user-attachments/assets/6d4a0aab-3a11-4cce-a0bb-8a170854b84d" />
