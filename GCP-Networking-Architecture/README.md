# Lab GSP211: Multiple VPC Networks

## 1. Project Description
In this project, I configured a complex network topology in Google Cloud Platform. The goal was to demonstrate how to segment traffic using multiple Virtual Private Clouds (VPC) and how to manage connectivity between them.

## 2. Key Architecture Features
* **Network Segmentation:** Created three distinct networks: `managementnet`, `privatenet`, and `publicnet`.
* **Multi-NIC Instance:** Deployed a VM instance (`vm-appliance`) with three network interfaces to act as a bridge between different VPCs.
* **VPC Peering:** Established a private connection between `managementnet` and `privatenet` to allow internal traffic without using the public internet.
* **Custom Firewalls:** Configured rules to permit ICMP (ping) and SSH traffic only where necessary.

---

## 3. Visual Evidence

### VPC Network Topology
This screenshot confirms the creation of the custom VPCs and their specific CIDR blocks.
![VPC Topology](01-vpc-topology.png)

### Multi-NIC Configuration
Detail of the `vm-appliance` instance showing three active network interfaces (nic0, nic1, nic2). This is a critical configuration for network appliances.
![Multi-NIC Config](02-multi-nic-config.png)

### VPC Peering Status
Evidence of the "Active" peering state, ensuring private communication between separate VPCs.
![VPC Peering](03-vpc-peering-status.png)

### Firewall Security Rules
Verification of the firewall rules applied to allow controlled access to the instances.
![Firewall Rules](04-firewall-rules.png)

### Connectivity Verification
Final PING test between instances in different networks, confirming that the peering and ruteo work correctly.
![Connectivity Test](05-connectivity-test.png)

---

## 4. Technical Reflection (Self-Analysis)
The most challenging part was ensuring the **Multi-NIC VM** was assigned to the correct subnets during creation. This lab is fundamental for my preparation for the **Google Associate Cloud Engineer (ACE)** certification, as it covers core networking and security principles.
