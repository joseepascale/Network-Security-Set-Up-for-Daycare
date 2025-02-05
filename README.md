# Network-Security-Daycare-Project

## Scenerio:
In this project, I reinforced my knowledge of network security by designing a secure network topology and configuring various security measures for a daycare center. This was to ensure the daycare's network is secure, protecting sensitive data like children's personal information, while maintaining a stable, efficient network infrastructure.

## Objectives
- Design and implement a secure network topology for the daycare center.
- Configure and customize firewalls for enhanced security.
- Set up secure VPN connections for remote access and file transfers.
- Perform penetration testing to identify vulnerabilities in the system.
 Monitor and log network traffic to detect potential security issues.

### Tools Used
-GNS3 and Virtualbox for Network real world Simulation
- Windows Defender Firewall: Configured to protect individual devices within the daycare center network.
- pfSense: Used for configuring and managing firewalls, VPNs, and custom firewall rules to ensure network security.
- Wireshark: For capturing and analyzing network traffic to ensure data integrity and security.
- Metasploit/Kali Linux: Used for penetration testing to assess the security of the network and firewall setup.

## Project Breakdown

## **1. Designing the Network Topology**
-sketch
![thumbnail_IMG_0775](https://github.com/user-attachments/assets/bab3748e-cb2c-4ff3-aa61-5127d6fe521c)
- Connected only pfsense to **WAN (em0) to NAT** for Internet access.
- Connected **LAN (em1) to Host-Only Adapter** for VLANs and VirtualBox VMs.
 ![2025-02-05 (1)](https://github.com/user-attachments/assets/31137831-57be-4d1f-b795-39375995d952) 

## **2. Implementing Network Segmentation**
- Added **pfSense (router), switch, and PC VMs (Windows & Kali Linux)** to GNS3.
![2025-02-05](https://github.com/user-attachments/assets/581f77b9-a492-4680-8c76-e138149ec623)
- Configured and used an **Ethernet switch to automatically handle VLAN traffic** without requiring manual trunk/access port configurations.
![2025-02-01 (8)](https://github.com/user-attachments/assets/db01030c-d25b-4bff-9b56-7b8bae930c1e)
- Connected **pfSense LAN (em1) to the switch** to handle VLANs.
- Connected **Windows and Kali Linux VMs** to the switch for network segmentation.
![2025-02-04](https://github.com/user-attachments/assets/f64aead3-041f-4168-985f-224dc64b0fb2)




  
