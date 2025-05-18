# IP Addressing Scheme

## 📘 Overview
This document provides the IP addressing plan for the network. It includes device interface assignments, subnetting structure, VLAN configuration, and gateway information.

---

## 📋 IP Addressing Table

| Device        | Interface              | IPv4 Address   | Subnet Mask     | Vlan ID | Default Gateway   |
|---------------|------------------------|----------------|------------------|---------|-------------------|
| R1            | GigabitEthernet0/0     | 10.0.0.1       | 255.0.0.0        |         |                   |
| R1            | GigabitEthernet0/1     | 192.168.200.1  | 255.255.255.252  |         |                   |
| R1            | GigabitEthernet0/2     | 192.168.250.1  | 255.255.255.252  |         |                   |
| R2            | GigabitEthernet0/0.10  | 192.168.10.2   | 255.255.255.0    |         |                   |
| R2            | GigabitEthernet0/0.20  | 192.168.20.2   | 255.255.255.0    |         |                   |
| R2            | GigabitEthernet0/0.30  | 192.168.30.2   | 255.255.255.0    |         |                   |
| R2            | GigabitEthernet0/0.40  | 192.168.40.3   | 255.255.255.0    |         |                   |
| R2            | GigabitEthernet0/0.50  | 192.168.50.3   | 255.255.255.0    |         |                   |
| R2            | GigabitEthernet0/0.60  | 192.168.60.3   | 255.255.255.0    |         |                   |
| R2            | GigabitEthernet0/1     | 192.168.100.1  | 255.255.255.252  |         |                   |
| R2            | GigabitEthernet0/2     | 192.168.200.2  | 255.255.255.252  |         |                   |
| R3            | GigabitEthernet0/0.10  | 192.168.10.3   | 255.255.255.0    |         |                   |
| R3            | GigabitEthernet0/0.20  | 192.168.20.3   | 255.255.255.0    |         |                   |
| R3            | GigabitEthernet0/0.30  | 192.168.30.3   | 255.255.255.0    |         |                   |
| R3            | GigabitEthernet0/0.40  | 192.168.40.2   | 255.255.255.0    |         |                   |
| R3            | GigabitEthernet0/0.50  | 192.168.50.2   | 255.255.255.0    |         |                   |
| R3            | GigabitEthernet0/0.60  | 192.168.60.2   | 255.255.255.0    |         |                   |
| R3            | GigabitEthernet0/1     | 192.168.100.2  | 255.255.255.252  |         |                   |
| R3            | GigabitEthernet0/2     | 192.168.250.2  | 255.255.255.252  |         |                   |
| S1            | Vlan                   | 192.168.50.2   | 255.255.255.0    | 50      | 192.168.50.1      |
| S2            | Vlan                   | 192.168.50.4   | 255.255.255.0    | 50      | 192.168.50.1      |
| S3            | Vlan                   | 10.0.0.5       | 255.0.0.0        | 100     | 10.0.0.1          |
| DHCP Server   | NIC                    | 192.168.50.5   | 255.255.255.0    | 50      | 192.168.50.1      |
| Web Server    | NIC                    | 10.0.0.10      | 255.0.0.0        |         | 10.0.0.1          |
| Email Server  | NIC                    | 10.0.0.20      | 255.0.0.0        |         | 10.0.0.1          |
| Syslog Server | NIC                    | 10.0.0.30      | 255.0.0.0        |         | 10.0.0.1          |
| DNS Server    | NIC                    | 10.0.0.40      | 255.0.0.0        |         | 10.0.0.1          |
| Department 1  | NIC                    | DHCP           | DHCP             | 10      | 192.168.10.1      |
| Department 2  | NIC                    | DHCP           | DHCP             | 20      | 192.168.20.1      |
| Department 3  | NIC                    | DHCP           | DHCP             | 30      | 192.168.30.1      |
| Department 4  | NIC                    | DHCP           | DHCP             | 40      | 192.168.40.1      |
| Department 5  | NIC                    | DHCP           | DHCP             | 50      | 192.168.50.1      |
| Guest Network | NIC                    | DHCP           | DHCP             | 60      | 192.168.60.1      |
