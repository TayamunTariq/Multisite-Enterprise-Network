\# Secure Multi-Site Enterprise Network Design



\## 🌐 Project Overview

This project involves the design and implementation of a scalable, \*\*3-tier hierarchical network\*\* for a 200-user enterprise. It features a redundant failover architecture and secure remote access between two distinct geographical sites (Headquarters and Branch Office).



\## 🛠️ Technical Specifications

\* \*\*Architecture:\*\* 3-Tier Hierarchical Model (Core, Distribution, Access).

\* \*\*Redundancy:\*\* Hot Standby Router Protocol (HSRP) for gateway availability.

\* \*\*Security:\*\* Site-to-Site IPsec VPN using AES encryption and SHA hashing.

\* \*\*Simulation Tool:\*\* Cisco Packet Tracer.

\* \*\*Hardware:\*\* Cisco 2911 Routers, 3650 Multilayer Switches, 2960 Access Switches.



\## 📍 Network Topology

\### Site A (Headquarters)

\* \*\*Internal Subnet:\*\* `192.168.10.0/24`.

\* \*\*Default Gateway (Virtual IP):\*\* `192.168.10.254`.

\* \*\*Redundancy:\*\* Configured HSRP between `HQ-R1` (Primary) and `HQ-R2` (Standby) to ensure 99.9% availability.



\### Site B (Branch Office)

\* \*\*Internal Subnet:\*\* `192.168.20.0/24`.

\* \*\*Default Gateway:\*\* `192.168.20.1`.



\### Interconnectivity

\* \*\*Primary Link:\*\* `12.0.0.0/24`.

\* \*\*Backup Link:\*\* `11.0.0.0/24`.



\## 🔐 Security Implementation (IPsec VPN)

The Site-to-Site VPN ensures that all traffic between Site A and Site B is encrypted before traveling over the public internet link.

\* \*\*Phase 1 (ISAKMP):\*\* AES Encryption, SHA Hash, Diffie-Hellman Group 2.

\* \*\*Phase 2 (IPsec):\*\* ESP-AES and ESP-SHA-HMAC transform sets.

\* \*\*Interesting Traffic:\*\* Defined via ACL to only encrypt traffic between the `192.168.10.0` and `192.168.20.0` networks.



\## 🚀 How to Verify

1\. \*\*HSRP Failover:\*\* Shutdown the `G0/0` interface on `HQ-R1` and observe the transition of `HQ-R2` from Standby to Active.

2\. \*\*VPN Status:\*\* Run `show crypto ipsec sa` on the routers to verify encapsulated and decapsulated packet counts.

3\. \*\*Connectivity:\*\* Perform a `tracert` from a PC in Site A to a PC in Site B to confirm the path through the VPN tunnel.



---

