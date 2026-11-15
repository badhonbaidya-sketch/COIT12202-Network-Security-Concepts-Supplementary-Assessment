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
