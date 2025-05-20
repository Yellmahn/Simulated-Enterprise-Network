# 🔒 ACL Implementation Documentation

This document outlines the ACL (Access Control List) configuration used to manage inter-VLAN traffic and secure access to the DMZ and Guest network.

---

## 📘 Overview

The network contains:

- 🏢 **5 Departmental VLANs** (internal-only communication)
- 🌐 **DMZ Network** (public-facing servers: Web, Email, DNS, Sys)
- 📱 **Guest VLAN** (internet access only)

ACLs are implemented on Layer 3 interfaces to **restrict access**, **control traffic flow**, and **enhance network security**.
Each network is on a **separate VLAN** with inter-VLAN routing enabled. ACLs are configured to filter traffic between VLANs as per defined policies.

---
## 🎯 ACL Policy Objectives

- ❌ Restrict communication between departments
- 🚫 Block Guest access to internal VLANs
- ✅ Allow only specific services to/from DMZ:
  - HTTP to Web Server
  - DNS to/from DNS Server
  - SMTP to Email Server
- 🛡️ Deny all other traffic by default

---

## 📄 ACL Rules Summary

| ACL Name             | Direction | Device & Interface  | Description                                       |
|----------------------|-----------|---------------------|---------------------------------------------------|
| `DMZ_ACCESS_CONTROL` | Outbound  | R1 – G0/0           | Allow selected external traffic to DMZ services   |
| `BLOCK_VLAN10`       | Inbound   | R3 and R2 – G0/0.10 | Deny access from Dept. 1 to other departments     |
| `BLOCK_VLAN20`       | Inbound   | R3 and R2 – G0/0.20 | Deny access from Dept. 2 to other departments     |
| `BLOCK_VLAN30`       | Inbound   | R3 and R2 – G0/0.30 | Deny access from Dept. 3 to other departments     |
| `BLOCK_VLAN40`       | Inbound   | R3 and R2 – G0/0.40 | Deny access from Dept. 4 to other departments     |
| `BLOCK_VLAN50`       | Inbound   | R3 and R2 – G0/0.50 | Deny access from Dept. 5 to other departments     |
| `BLOCK_VLAN60`       | Inbound   | R3 and R2 – G0/0.60 | Deny access from Guest to internal departments    |

## 🛡️Detailed Access Control lists
*Extended IP access list DMZ_ACCESS_CONTROL*
    - 10 permit tcp any host 10.0.0.10 eq www
    - 20 permit tcp any host 10.0.0.10 eq 443
    - 30 permit tcp any host 10.0.0.20 eq smtp
    - 40 permit tcp any host 10.0.0.20 eq pop3
    - 50 permit tcp any host 10.0.0.20 eq 143
    - 60 permit udp any host 10.0.0.30 eq 514
    - 70 permit udp any host 10.0.0.40 eq domain
    - 80 permit tcp any host 10.0.0.40 eq domain
    - 90 deny ip any 10.0.0.0 0.0.0.25
*Extended IP access list BLOCK_VLAN10*
    - 10 permit udp any eq bootpc any eq bootps
    - 20 permit udp any eq bootps any eq bootpc
    - 30 deny ip 192.168.10.0 0.0.0.255 192.168.20.0 0.0.0.255
    - 40 deny ip 192.168.10.0 0.0.0.255 192.168.30.0 0.0.0.255
    - 50 deny ip 192.168.10.0 0.0.0.255 192.168.40.0 0.0.0.255
    - 60 deny ip 192.168.10.0 0.0.0.255 192.168.50.0 0.0.0.255
    - 70 deny ip 192.168.10.0 0.0.0.255 192.168.60.0 0.0.0.255
    - 80 permit ip 192.168.10.0 0.0.0.255 any
Extended IP access list BLOCK_VLAN20
    - 10 permit udp any eq bootpc any eq bootps
    - 20 permit udp any eq bootps any eq bootpc
    - 30 deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
    - 40 deny ip 192.168.20.0 0.0.0.255 192.168.30.0 0.0.0.255
    - 50 deny ip 192.168.20.0 0.0.0.255 192.168.40.0 0.0.0.255
    - 60 deny ip 192.168.20.0 0.0.0.255 192.168.50.0 0.0.0.255
    - 70 deny ip 192.168.20.0 0.0.0.255 192.168.60.0 0.0.0.255
    - 80 permit ip 192.168.20.0 0.0.0.255 any
Extended IP access list BLOCK_VLAN30
    - 10 permit udp any eq bootpc any eq bootps
    - 20 permit udp any eq bootps any eq bootpc
    - 30 deny ip 192.168.30.0 0.0.0.255 192.168.10.0 0.0.0.255
    - 40 deny ip 192.168.30.0 0.0.0.255 192.168.20.0 0.0.0.255
    - 50 deny ip 192.168.30.0 0.0.0.255 192.168.40.0 0.0.0.255
    - 60 deny ip 192.168.30.0 0.0.0.255 192.168.50.0 0.0.0.255
    - 70 deny ip 192.168.30.0 0.0.0.255 192.168.60.0 0.0.0.255
    - 80 permit ip 192.168.30.0 0.0.0.255 any
Extended IP access list BLOCK_VLAN40
    - 10 permit udp any eq bootpc any eq bootps
    - 20 permit udp any eq bootps any eq bootpc
    - 30 deny ip 192.168.40.0 0.0.0.255 192.168.10.0 0.0.0.255
    - 40 deny ip 192.168.40.0 0.0.0.255 192.168.20.0 0.0.0.255
    - 50 deny ip 192.168.40.0 0.0.0.255 192.168.30.0 0.0.0.255
    - 60 deny ip 192.168.40.0 0.0.0.255 192.168.50.0 0.0.0.255
    - 70 deny ip 192.168.40.0 0.0.0.255 192.168.60.0 0.0.0.255
    - 80 permit ip 192.168.40.0 0.0.0.255 any
Extended IP access list BLOCK_VLAN50
    - 10 permit udp any eq bootpc any eq bootps
    - 20 permit udp any eq bootps any eq bootpc
    - 30 deny ip 192.168.50.0 0.0.0.255 192.168.10.0 0.0.0.255
    - 40 deny ip 192.168.50.0 0.0.0.255 192.168.20.0 0.0.0.255
    - 50 deny ip 192.168.50.0 0.0.0.255 192.168.30.0 0.0.0.255
    - 60 deny ip 192.168.50.0 0.0.0.255 192.168.40.0 0.0.0.255
    - 70 deny ip 192.168.50.0 0.0.0.255 192.168.60.0 0.0.0.255
    - 80 permit ip 192.168.50.0 0.0.0.255 any
Extended IP access list BLOCK_VLAN60
    - 10 permit udp any eq bootpc any eq bootps
    - 20 permit udp any eq bootps any eq bootpc
    - 30 deny ip 192.168.60.0 0.0.0.255 192.168.10.0 0.0.0.255
    - 40 deny ip 192.168.60.0 0.0.0.255 192.168.20.0 0.0.0.255
    - 50 deny ip 192.168.60.0 0.0.0.255 192.168.30.0 0.0.0.255
    - 60 deny ip 192.168.60.0 0.0.0.255 192.168.40.0 0.0.0.255
    - 70 deny ip 192.168.60.0 0.0.0.255 192.168.50.0 0.0.0.255
    - 80 permit ip 192.168.60.0 0.0.0.255 any
