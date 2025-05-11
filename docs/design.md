# 🧠 Network Design Explanation

## 🏢 Project Overview

This simulated enterprise network is designed using **Cisco Packet Tracer** to reflect a realistic mid-sized company's IT infrastructure. The network implements key principles of **segmentation, high availability, security**, while maintaining support for core services such as DNS, Email, Web Server and centralized logging.

---

## 🎯 Design Objectives

- Departmental isolation through **VLAN segmentation**
- **Redundant routing and switching** to ensure availability
- Isolated **DMZ** for internet-facing services
- Secure **guest Wi-Fi** network with encryption
- Centralized logging and basic **access control policies**
- Remote access restricted to authorized users via **SSH**

---

## 🧱 Core Components

### 🔹 VLAN Structure
- VLANs are used to segment departments
- A separate VLAN is allocated for Guest Wi-Fi access
- A dedicated DMZ VLAN isolates publicly accessible servers (e.g.Web, Email, DNS)

### 🔹 Routing & Redundancy
- **Router-on-a-Stick** is used for inter-VLAN routing
- Two routers are configured with **HSRP** for default gateway redundancy
- Core switches utilize **STP** to prevent switching loops
- **EtherChannel** links between switches improve bandwidth and provide redundancy

### 🔹 Security Measures
- **ACLs** are applied to control access between VLANs and to/from the DMZ
- **Port Security** is enabled on access switch ports to prevent unauthorized devices
- **SSH** is used instead of Telnet for secure remote administration
- Guest Wi-Fi uses **WPA2-PSK with AES** encryption for client access

### 🔹 Network Services
- **Syslog Server** is used to collect logs from routers and switches
- A **DHCP Server** provides IP addresses for multiple VLANs
- An internal **DNS Server** is used to resolve local domains
- An **Email Server** resides in the DMZ for external/internal communications
- A **Web Server** to provide web services
---

## 🌐 DMZ Design

- The DMZ contains:
  - Email Server
  - DNS Server
  - Web Server
  - Syslog Server
- Access to DMZ services is tightly controlled using ACLs
---

## 📶 Guest Wi-Fi Zone

- Separate VLAN and SSID
- Connected via a wireless router with WPA2 security with AES encryption
- ACLs prevent access from Guest VLAN to internal VLANs

---

## 🛡 High Availability Summary

| Component      | Redundancy Mechanism |
|----------------|-----------------------|
| Routers        | HSRP                  |
| Switches       | STP + EtherChannel    |
| Gateways       | HSRP Virtual IP       |

---

## 📈 Scalability Considerations

- VLAN design allows future department growth
- HSRP and STP configurations support additional routing/switching devices
- ACL structure can be extended as more services are added

---

## 🔚 Summary

This network design simulates an enterprise-level environment and practices **security, segmentation, and resilience**. It can be used for both training and showcasing foundational network design skills in a realistic enterprise context.
