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
- Kali Linux: Used for penetration testing to assess the security of the network and firewall setup.

## Project Breakdown

## 1. Connecting VirtualBox VMs to GNS3
- I installed VirtualBox and imported my Windows VM as Admin PC.
- I linked the VM to GNS3 using Edit > Preferences > VirtualBox VMs.
- I connected windows VM network adapter to the switch.
- Here's the sketch I drew that guided me through out the project
![IMG_0856](https://github.com/user-attachments/assets/a98a1929-f8eb-4634-9607-be648b4c2484)

## 2. Network Topology
- I created a new GNS3 project.
- **Router**: pfSense (Router1) manages the network and connects to the internet (NAT1).
- **LAN 1**: Admin and Staff computers are connected through **Switch1**.
- **LAN 2**: Guests and Kids computers are connected through **Switch2**.
- **Firewall Rules**: pfSense controls traffic between these LANs.
<img width="526" alt="2025-03-05" src="https://github.com/user-attachments/assets/9161c5d9-73e4-4b5d-a1a8-db883aceebee" />

## 3. **Assign IP Addresses**
| Interface | Network | IP Address |
|-----------|--------|------------|
| **WAN** | Internet (NAT1) | Assigned by DHCP |
| **LAN1** | Admin & Staff | 172.30.0.254/24 |
| **LAN2** | Guests & Kids | 172.30.1.254/24 |

<img width="765" alt="2025-03-05 (9)" src="https://github.com/user-attachments/assets/cac63718-2a6d-42f9-8cee-bcef7e59d842" />


**Device IP Assignments:**
| Device  | Network | IP Address |
|---------|--------|------------|
| **Admin**  | LAN1 | 172.30.0.2 |
| **Staff**  | LAN1 | 172.30.0.4 |
| **Guest**  | LAN2 | 172.30.1.2|
| **Kids**   | LAN2 | 172.30.1.4 |


## 4. Firewall Rules for Each VLAN
**Here's a look at the pfsense console and how I assigned different Ip's
<img width="601" alt="2025-03-05 (7)" src="https://github.com/user-attachments/assets/f896655d-53af-4407-8511-3e713661b2f8" />

- navigated to **Firewall > Rules** in web GUI pfSense.
-  I selected the LAN interface 
-  Added new rules to allow or restrict traffic:

 **1- Allow LAN1 (Admin & Staff) to Access LAN2 (Guests & Kids)**  
- **Source**: LAN1 net  
- **Destination**: LAN2 net  
- **Action**: Pass  
- **Protocol**: Any  

**2- Allow Admin to Access Staff**  
- **Source**: Admin (172.30.0.2)  
- **Destination**: Staff (172.30.0.4)  
- **Action**: Pass  
- **Protocol**: Any  

 **3- Block Staff from Accessing Admin**  
- **Source**: Staff (172.30.0.4)
- **Destination**: Admin (172.30.0.2) 
- **Action**: Block  
- **Protocol**: Any  

 **4- Block All Access to Admin PC**  
- **Source**: Any  
- **Destination**: Admin (172.30.0.2)  
- **Action**: Block  
- **Protocol**: Any  

 **5- Allow Internet Access for LAN1 (Admin & Staff)**  
- **Source**: LAN1 net  
- **Destination**: Any  
- **Action**: Pass  
- **Protocol**: TCP/UDP  
- **Destination Port Range**: 80 (HTTP) and 443 (HTTPS)

**6- Allow Internet Access for LAN2 (Guests & Kids)**  
- **Source**: LAN2 net 
- **Destination**: Any 
- **Action**: Pass  
- **Protocol**: TCP/UDP  
- **Destination Port Range**: 80 (HTTP) and 443 (HTTPS)

**7- Allow Access from LAN1 to LAN2**  
- **Source**: LAN1 net 
- **Destination**: LAN2 net  
- **Action**: Pass  
- **Protocol**: Any

<img width="707" alt="2025-03-05 (15)" src="https://github.com/user-attachments/assets/66122fe9-ca0d-4653-b299-b7ab2234c5c8" />



## 5. Testing and Verification
- I powered on pfSense and the VirtualBox VMs.
- I verified IP assignments with ping tests


**1- Admin PC should be able to access staff PC **
- ping 172.30.0.4
  
<img width="363" alt="2025-03-05 (16)" src="https://github.com/user-attachments/assets/440c0f80-b092-490f-9c53-39481471c89d" />

**2- LAN2 devices should be able to access internet but not allowed to access LAN1 
- ping 8.8.8.8
- ping 172.30.0.2

<img width="381" alt="2025-03-05 (17)" src="https://github.com/user-attachments/assets/969b9e3c-b684-45b1-a5d3-b9e319c1e069" />

**2- LAN1 devices should be able to access LAN2 devices **
-ping 172.30.1.2

<img width="379" alt="2025-03-05 (4)" src="https://github.com/user-attachments/assets/b79a7aab-f444-4e30-b7b3-985c50526f8e" />


### **6- Analyzing Traffic in Wireshark**  

**1- Wirecapture for LAN1 to LAN2 ping request 

<img width="641" alt="2025-03-18 (2)" src="https://github.com/user-attachments/assets/cef511ff-8c23-4573-8191-a7a488e2abe5" />



  
