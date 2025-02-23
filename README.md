# Network-Security-Daycare-Project

## Scenerio:
In this project, I reinforced my knowledge of network security by designing a secure network topology and configuring various security measures for a daycare center. This was to ensure the daycare's network is secure, protecting sensitive data like children's personal information, while maintaining a stable, efficient network infrastructure.

## Objectives
- Design and implement a secure network topology for the daycare center.
- Configure and customize firewalls for enhanced security.
- Perform penetration testing to identify vulnerabilities in the system.
- Monitor and log network traffic to detect potential security issues.

### Tools Used
-GNS3 and Virtualbox for Network real world Simulation
- Windows Defender Firewall: Configured to protect individual devices within the daycare center network.
- pfSense: Used for configuring and managing firewalls,and custom firewall rules to ensure network security.
- Wireshark: For capturing and analyzing network traffic to ensure data integrity and security.
- Metasploit/Kali Linux: Used for penetration testing to assess the security of the network and firewall setup.

## Project Breakdown

## 1. Connecting VirtualBox VMs to GNS3
- I installed VirtualBox and imported my Windows and Kali Linux VMs.
- I linked the VMs to GNS3 using Edit > Preferences > VirtualBox VMs.
- I connected each VM’s network adapter to the switch.
- Here's the sketch I drew that guided me through out the project
![thumbnail_IMG_0775](https://github.com/user-attachments/assets/d6244640-9769-4071-9863-5afea0fe3293)

## 2. Setting Up the Network Topology
- I created a new GNS3 project.
- I added a pfSense VM and Ethernet switch.
- I connected pfSense’s WAN to the internet and its LAN to the switch.
<img width="639" alt="2025-02-21 (4)" src="https://github.com/user-attachments/assets/b3b147b0-c62c-404a-bd99-926b3ce0c5be" />

## 3. Configuring VLANs and pfSense
- I created VLANs on pfSense.
- **VLAN 10** (Admin Network): 192.168.20.1 - 192.168.20.100
- **VLAN 20** (Staff Network): 192.168.30.1 - 192.168.30.100
- **VLAN 30** (Guest/Kids Network): 192.40.1 - 192.168.40.100
- I assigned VLAN interfaces, set up DHCP, and applied basic firewall rules.
<img width="690" alt="2025-02-21 (7)" src="https://github.com/user-attachments/assets/8049a568-0ca5-4424-b239-c21dfb791b19" />

- Here's how I configured the staff network
  
<img width="346" alt="2025-02-21 (9)" src="https://github.com/user-attachments/assets/86145ef2-de80-47fa-b2b8-0e9fed8da9dc" />

<img width="558" alt="2025-02-21 (10)" src="https://github.com/user-attachments/assets/efa940cf-145e-4684-8959-afc1d2c74afb" />

- Here's how it looks after configurating each VLAN's 

<img width="638" alt="2025-02-21 (8)" src="https://github.com/user-attachments/assets/25c35122-437a-4813-9721-f5a6c3245e0d" />

- ![Firewall Rules](screenshots/firewall_rules.png)

## 4. Testing and Verification
- I powered on pfSense and the VirtualBox VMs.
- I verified IP assignments with ping tests and checked the firewall logs.
- ![Testing](screenshots/testing.png)





  
