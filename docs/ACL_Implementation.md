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
