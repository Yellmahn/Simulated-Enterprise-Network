# VLAN Implementation Overview

This document describes the VLAN design and implementation for a Cisco-based network topology created in Cisco Packet Tracer.

---

## 📚 VLAN Structure

The network is segmented into six active VLANs to provide logical separation for different departments and user groups. An additional VLAN is reserved as the native VLAN on trunk links.

| VLAN ID | VLAN Name        | Purpose          | Devices          |
|---------|------------------|------------------|------------------|
| 10      | Department 1     | Department 1     | Department's PC  |
| 20      | Department 2     | Department 2     | Department's PC  |
| 30      | Department 3     | Department 3     | Department's PC  |
| 40      | Department 4     | Department 4     | Department's PC  |
| 50      | Department 5     | Department 5     | Department's PC  |
| 60      | Public_WiFi      | Guest Network    | Wireless Clients |
| 100     | DMZ              | DMZ Network      | DMZ Endpoints	   |
| 999     | Native_Vlan      | Native VLAN      | Unused Ports	   |

---

## 🧭 VLAN Availability

All VLANs are created and available on **both Switch 1 and Switch 2**. End devices are connected to access ports assigned to their respective VLANs across the switches.

This allows seamless VLAN communication across the network, with trunk links ensuring inter-switch connectivity.

---

## 🔁 Trunk Links & EtherChannel

There are **three trunk links** established in the topology:

1. **Router 2 ↔ Switch 1**  
2. **Router 3 ↔ Switch 2**  
3. **Switch 1 ↔ Switch 2** (via **EtherChannel** for redundancy and load balancing)

- All trunk links carry VLANs: 10, 20, 30, 40, 50, 60  
- **VLAN 999** is configured as the **Native VLAN** on all trunk ports, following best practices

---

## 🌐 Spanning Tree Protocol (PVST)

**Per VLAN Spanning Tree (PVST)** is implemented to maintain a loop-free and efficient Layer 2 topology.

- **Switch 1** is designated as the **Root Bridge** for:
  - VLAN 10 (DEPT1)
  - VLAN 20 (DEPT2)
  - VLAN 50 (DEPT5)

- **Switch 2** is designated as the **Root Bridge** for:
  - VLAN 30 (DEPT3)
  - VLAN 40 (DEPT4)
  - VLAN 60 (GUEST)

This STP design enables Redundancy by distributing root bridge roles across both core switches.
