# IPv6 ACL Configuration - Packet Tracer Lab



## 📌 Overview


This project demonstrates how to configure IPv6 Access Control Lists (ACLs) in Cisco Packet Tracer to protect a server from DoS and DDoS attacks. The lab focuses on filtering HTTP/HTTPS traffic and ICMP ping requests using properly placed ACLs on routers.


---



## 🎯 Objectives



### Part 1: HTTP/HTTPS Filtering (DoS Protection)

- Block HTTP (port 80) and HTTPS (port 443) traffic from a specific IPv6 network:
  - `2001:db8:1:11::/64`
- Allow all other traffic.
- Ensure legitimate users (PC1) can still access the server.


### Part 2: ICMP Filtering (DDoS Protection)

- Block all ICMP traffic to the server.
- Allow other IPv6 traffic (such as web access).
- Apply ACL closest to destination for effectiveness.


---

## 🖥️ Network Addressing



| Device   | Interface | IPv6 Address            | Gateway   |
|----------|----------|-------------------------|-----------|
| PC1      | NIC      | 2001:db8:1:10::10/64    | fe80::1   |
| PC2      | NIC      | 2001:db8:1:11::11/64    | fe80::1   |
| Server3  | NIC      | 2001:db8:1:30::30/64    | fe80::30  |


---


## ⚙️ Configuration Summary

📍 ACL 2: BLOCK_ICMP (R3)

Blocks all ICMP traffic to Server3.

deny icmp any any  
permit ipv6 any any

📍 Applied closest to destination (Server3 network).

🧪 Verification Steps
✔ HTTP/HTTPS Test
PC1 → Server3: Access allowed ✅
PC2 → Server3: HTTP/HTTPS blocked ❌
✔ ICMP Test
PC1 → Server3: Ping fails ❌
PC2 → Server3: Ping fails ❌
✔ Web Access
PC1 can still access server via browser ✅
🔐 Key Learning Outcomes
IPv6 ACL creation and deployment
Difference between source vs destination placement
DoS vs DDoS mitigation techniques
Real-world network security filtering
🚀 Tools Used
Cisco Packet Tracer
IPv6 Routing
Access Control Lists (ACLs)
📌 Author

Cybersecurity & Cloud Networking Learner
