# Network-Security-Daycare-Project

## Scenerio:
My role as a part-time assistant teacher in a daycare inspired me to design a secure network set-up simulation. In this project, I reinforced my knowledge of network security by designing a secure network topology and configuring various security measures for a daycare center. This was to ensure the daycare's network is secure, protecting sensitive data like children's personal information, while maintaining a stable, efficient network infrastructure.

## Objectives
- Design and implement a secure network topology for the daycare center.
- Configure and customize firewalls for enhanced security.
-  Monitor and log network traffic to detect potential security issues.
- Perform penetration testing to identify vulnerabilities in the system.


### Tools Used
-GNS3 and Virtualbox for Network real world Simulation
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

## 4. Firewall Rules for Each VLAN
**Here's a look at the pfsense console and how I assigned different Ip's
<img width="503" alt="2025-02-21 (5)" src="https://github.com/user-attachments/assets/f594c729-6ddf-4f42-9d80-354b6368e507" />

- navigated to **Firewall > Rules** in web GUI pfSense.
-  I selected the VLAN interface 
-  Added new rules to allow or restrict traffic:
  
1- Allow Admin VLAN to Access Staff VLAN
- Source: VLAN20_Admin net
- Destination: VLAN30_Staff net
- Action: Pass
- Protocol: Any
<img width="629" alt="2025-02-22 (5)" src="https://github.com/user-attachments/assets/715a7c17-2705-44bf-b17e-253094547d52" />

2- Block Guest/Kids VLAN from Accessing Admin VLAN
- Source: VLAN40_Guest net
- Destination: VLAN20_Office net
- Action: Block
- Protocol: Any

3- Allow Internet Access for Guest/Kids VLAN
- Source: VLAN40_Guest net
- Destination: Any
- Action: Pass
- Protocol: TCP/UDP
- Destination Port Range: 80 (HTTP) and 443 (HTTPS)

<img width="623" alt="2025-02-22 (4)" src="https://github.com/user-attachments/assets/ad29f2b0-bec5-4841-b580-652fa4dc0f5e" />


## 5. Testing and Verification
- I powered on pfSense and the VirtualBox VMs.
- I verified IP assignments with ping tests and checked the firewall logs.

- Here's after I allowed Admin VLAN  to access Staff VLAN 
<img width="553" alt="2025-02-21 (16)" src="https://github.com/user-attachments/assets/bf1d4445-40c0-4353-b4c7-2abfd4eda3c8" />


- Here's after I blocked the Guest/Kids VLAN from accessing the Admin
<img width="663" alt="2025-02-21 (15)" src="https://github.com/user-attachments/assets/8b8a8247-be92-4891-a8f9-0208d04bfdb7" />




  
