# Enterprise Network Infrastructure Project (Site-to-Site VPN & Multi-VLAN)

## 📝 Project Overview
This project demonstrates a comprehensive network infrastructure solution for a business comprising a **Main Office (Site 1)** and a **Branch Office (Site 2)**. The system is designed to provide secure connectivity, automated IP management, and robust access control policies using Cisco technologies.

* **Status:** Completed (Full configuration applied in the `.pkt` file).
* **Core Technologies:** GRE VPN, OSPF, EIGRP, NAT Overload, Inter-VLAN Routing, and ACL Security.

---

## 🏗️ Network Architecture

### 1. Main Office (SITE 1)
* **Network Address:** `172.25.0.0/16`.
* **VLAN Segmentation:** * **VLAN 10 (Director):** `172.25.10.0/24`.
    * **VLAN 20 (Sales):** `172.25.20.0/24`.
    * **VLAN 30 (Accounting):** `172.25.30.0/24`.
    * **VLAN 40 (Server):** `172.25.40.0/24`.
* **Key Implementations:**
    * **Layer 3 Switching:** Inter-VLAN routing configured on **SWL3**.
    * **Dynamic Routing:** Internal routing via **EIGRP AS 100**.
    * **IP Management:** **DHCP Relay Agent** configured to distribute dynamic IPs to VLANs 10, 20, and 30.
    * **External Connectivity:** Default Route propagation into EIGRP for Internet access.

### 2. Branch Office (SITE 2)
* **Network Address:** `172.26.0.0/16`.
* **Kỹ thuật triển khai:**
    * **Router-on-a-Stick:** Configured with sub-interfaces for VLAN routing.
    * **Local DHCP:** Router acts as a DHCP server for Branch VLANs, pointing to the Main Office DNS.

### 3. WAN & Edge Services
* **Internet Simulation:** A cluster of 3 ISP Routers running **OSPF Area 0**.
* **VPN Site-to-Site:** Established a secure **GRE VPN** tunnel between the Main Office and Branch
