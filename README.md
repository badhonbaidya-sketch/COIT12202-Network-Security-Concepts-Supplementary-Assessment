## SS1 - GNS3 Network Topology

The starter GNS3 project contains four nodes: LAN-Host, VPNServer, Internet and Client. This topology is used to configure a secure HTTPS web server and establish a WireGuard VPN connection between the remote Client and the private LAN.

<img width="959" height="565" alt="image" src="https://github.com/user-attachments/assets/ce5bc680-ff34-472d-b949-22695ada961d" />

## SS2 - Initial Network Connectivity

I tested the initial network connectivity using ping commands. The purpose was to confirm that Client could communicate with the public VPNServer address while the private LAN remained inaccessible before the WireGuard tunnel was established.

<img width="959" height="562" alt="image" src="https://github.com/user-attachments/assets/6d4a0aab-3a11-4cce-a0bb-8a170854b84d" />

## SS3 — Root Certificate Authority Creation

I created a Root Certificate Authority using OpenSSL on VPNServer. I generated a 4096-bit RSA private key and a self-signed certificate valid for approximately 10 years. The verification output confirms that the certificate subject and issuer match, showing that the Root CA is self-signed.

<img width="959" height="563" alt="image" src="https://github.com/user-attachments/assets/207d1a04-f6cc-4d1a-8b3f-9d432ffc7ad6" />

## SS4: CSR Transfer and Verification*

The Certificate Signing Request (CSR) was successfully transferred from LAN-Host to VPNServer using HTTP on port 8080. OpenSSL was used to verify the CSR subject and confirm the server identity before certificate signing.

<img width="959" height="564" alt="image" src="https://github.com/user-attachments/assets/5c910353-e336-48f3-8fe8-476416264bde" />

## SS5 – Server Certificate Signing and Verification

The server certificate was successfully signed by Badhon Root CA. OpenSSL verification returned OK, confirming that the certificate was issued by the trusted Root CA. The certificate is valid for one year and identifies www.12305332.lab.

<img width="959" height="563" alt="image" src="https://github.com/user-attachments/assets/75a1d357-44bb-420e-b8a0-b7ca7593d593" />

## SS6 – Signed Certificate Transfer and Verification

The CA-signed server certificate was successfully downloaded from VPNServer to LAN-Host using HTTP on port 8080. OpenSSL was used to verify the certificate details, confirming that it was issued by Badhon Root CA for www.12305332.lab.

<img width="959" height="563" alt="image" src="https://github.com/user-attachments/assets/7c54c8b7-0712-496a-9db5-e218d53c1991" />

## SS7 – Nginx HTTPS Configuration and Successful Testing

Nginx was successfully configured to use the CA-signed SSL certificate on port 443. The configuration test passed, and the HTTPS connection returned HTTP/1.1 200 OK, confirming that the secure web server is responding correctly.

<img width="959" height="565" alt="image" src="https://github.com/user-attachments/assets/5849833a-222d-4ca2-9696-36c4d25c5c77" />

## SS8 – Root CA Certificate Verification*

The Root CA certificate was successfully downloaded from the VPNServer to the LAN-Host. OpenSSL confirmed the certificate's subject and issuer as Badhon Root CA, establishing the CA identity needed for HTTPS certificate verification.

<img width="959" height="563" alt="image" src="https://github.com/user-attachments/assets/a8e363dd-6bbc-4797-97d3-114582794630" />

## SS9 – HTTPS and Certificate Chain Verification

Successfully verified the HTTPS connection using the trusted Root CA certificate. The webpage loaded without SSL errors, and OpenSSL confirmed that the server certificate was valid and signed by the trusted Certificate Authority.

<img width="959" height="563" alt="image" src="https://github.com/user-attachments/assets/97272362-f6dd-47e7-9866-c53b30419ef2" />

## SS10 - WireGuard Key Generation and VPNServer Configuration*

I generated the WireGuard private and public keys on VPNServer and checked the existing configuration. The VPNServer uses IP address 10.0.0.1/24 and port 51820, with 10.0.0.2/32 configured for the client peer. This prepares the server for establishing a secure VPN tunnel.

<img width="959" height="566" alt="image" src="https://github.com/user-attachments/assets/43a232e8-bb9c-4de7-bd37-8977af545700" />

## SS11 WireGuard VPNServer Configuration and Interface Verification

I configured and activated the WireGuard VPNServer using the `wg-quick up wg0` command. The server interface was successfully created with IP address 10.0.0.1/24 and listening port 51820. I used `wg show` to verify that the interface was running and the client peer public key was correctly configured with AllowedIPs 10.0.0.2/32. The output confirms that the VPNServer is ready for client connection testing. 

<img width="959" height="565" alt="image" src="https://github.com/user-attachments/assets/289630fd-a451-403a-afd2-61b22854a538" />

## 
