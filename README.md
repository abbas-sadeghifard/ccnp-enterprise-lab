# CCNP Enterprise Practical Lab

## 🎯 Objective
The primary objective of this project is to implement, verify, and troubleshoot a complex Enterprise network environment. This lab covers advanced routing, switching, security, and automation tasks required for CCNP Enterprise certification (ENCOR + ENARSI).

## 🗺️ Topology
The lab is designed using EVE-NG. The topology features a hierarchical campus (Core/Distribution/Access), **multi-site branch connectivity**, and a simulated Internet edge with **redundant ISP connections**.
![Network Topology](topology/Topology.png)


## 🏗️ Pre-configured Environment
The lab environment is provided with the following pre-existing configurations and baseline connectivity:
* **Topology:** Physical cabling and node placement (Core, Distribution, Access, and ISP routers) are pre-defined in the `.unl` project file.
* **WAN/ISP Links:** WAN connectivity and ISP-side interface parameters are pre-provisioned, serving as the demarcation point for internal enterprise routing.
* **Base Connectivity:** Initial interface assignments are set to facilitate immediate lab entry and testing.

## 🚀 Lab Objectives & Implementation Scope
This lab is a comprehensive enterprise infrastructure project designed to cover advanced CCNP-level implementation, verification, and troubleshooting. The scope is divided into the following technical domains:

### 1. ⚡ Switching & Layer 2 Core Infrastructure
*   **VLAN & Trunking:** Strategic VLAN design, VTPv2/v3 management, 802.1Q trunking, and DTP hardening .
*   **High Availability & Loop Prevention:** EtherChannel (L2/L3 via LACP), RSTP/MSTP (Root Bridge selection, PortFast, BPDU Guard), and UDLD.
*   **VTPv3 Integration:** Advanced MSTP configuration and VLAN structure management.

### 2. 🛣️ Routing & Traffic Engineering
*   **Inter-VLAN & Redundancy:** L3 SVI and Router-on-a-stick, HSRP (active role management, timer tuning, MD5 authentication).
*   **Advanced Routing:** OSPFv2 and EIGRP optimization (Area design, Passive interfaces, Metric/Cost/Delay manipulation, Stub Areas, and Redistribution with route filtering/tagging).
*   **Traffic Control:** Policy-Based Routing (PBR) and Control Plane activation, Static/Floating routes with IP SLA and Track Object logic.

### 3. 🌐 WAN, VPN & Tunneling
*   **Tunneling:** GRE Tunneling (MTU/MSS optimization).
*   **DMVPN:** Phase 2 deployment utilizing FVRF (Front-Door VRF).
*   **IPsec VPN:** Comprehensive implementations (IKEv1/v2, Crypto Maps, IPsec Profiles, GRE over IPsec) including DoS protection for IKEv2.
*   **Connectivity:** Layer 2/Layer 3 WAN Cloud integration and IP addressing design.

### 4. 🛡️ Enterprise Security & Hardening
*   **Data Plane Security:** Port Security (Static/Sticky/Dynamic), DHCP Snooping, Dynamic ARP Inspection (DAI), and VLAN ACLs.
*   **Control Plane & Edge Security:** ZBFW (Zone-Based Firewall), CoPP (Control Plane Policing), uRPF, and RBAC (Role-Based Access Control).
*   **NAT/PAT:** Redundant Source NAT/PAT implementation with BGP and non-BGP internet scenarios using public pools.

### 5. 🗺️ BGP & Internet Edge
*   **eBGP:** Multi-homed internet redundancy, Route Filtering, BGP Authentication, and Attribute manipulation for asymmetric traffic control.

### 6. ⚙️ Operations, Automation & Management
*   **Automation:** Ansible infrastructure (Playbooks with Jinja2 templates, YAML variables, and native IOS modules).
*   **Monitoring & Observability:** SNMPv2c/v3 (Traps, PRTG integration), Syslog, and IP SLA probes.
*   **Maintenance:** EEM (Embedded Event Manager) for automated CLI actions, Archive service for FTP-based backups, and Auto-Recovery for Err-Disable states.


## 📁 Repository Contents
```text
.
├── docs/            # Lab Guide PDFs and documentation
├── eve-ng/          # EVE-NG topology files (.unl)
├── configs/         # Device configurations (running-config)
├── topology/        # Network diagrams and screenshots
└── ansible/         # Automation scripts and Jinja2 templates
```
## 🚀 Planned Improvements

This roadmap outlines the short‑term improvements planned for the lab topology, focusing on enterprise network stability, security hardening, and operational management using Ansible.

### Phase 1: Core Protocol Tuning & Security Baseline
- **Infrastructure Hardening**
  - Implement Management Plane Protection (MPP)
  - Enforce SSHv2 access and AAA authentication models
  - Configure local logging for operational visibility

- **Routing Optimization**
  - Tune OSPF/EIGRP/BGP timers to improve convergence
  - Implement route filtering using prefix-lists and route-maps
  - Simulate ISP-scale routing control scenarios

- **Layer 2 Security**
  - Deploy Port-Security on access interfaces
  - Implement DHCP Snooping
  - Enable Dynamic ARP Inspection (DAI)

---

### Phase 2: Advanced Network Services & Hardening
- **Perimeter Security**
  - Configure Zone-Based Firewall (ZBF) on IOS-XE routers
  - Implement NAT/PAT for simulated edge connectivity

- **Redundancy Protocols**
  - Deploy First Hop Redundancy Protocols (HSRP / VRRP)
  - Implement object tracking for failover scenarios

- **Network Access Control**
  - Configure 802.1X authentication on access switches
  - Implement MAC Authentication Bypass (MAB)

---

### Phase 3: Operational Automation (Ansible)
- **Control Node Integration**
  - Deploy a Linux control node for Ansible management
  - Manage IOS/IOS-XE devices via SSH

- **State Auditing**
  - Develop playbooks to verify operational state:
    - Interface status
    - OSPF neighbor consistency
    - Routing table validation

- **Configuration Lifecycle Management**
  - Automate daily configuration backups
  - Perform bulk configuration changes on switch ports
  - Use Ansible modules such as `ios_config` and `ios_command`

## 🛠️ Tools Used

- **Network Simulator:** EVE-NG
- **Network Operating System:** Cisco IOS-XE
- **Automation:** Ansible, Jinja2
- **Version Control:** Git and GitHub

## EVE-NG Lab Package
Part 1:
https://my.uupload.ir/dl/n2J2dY6e
Part 2:
https://my.uupload.ir/dl/ODwr7rWx
Part 3:
https://my.uupload.ir/dl/eyJZ5kXD

## EVE-Workshop-v6 Setup Guide
link:
https://my.uupload.ir/p/v9VG5eYr

## ℹ️ About This Project

This lab is a professional-grade study environment designed to simulate real-world enterprise network scenarios and operational constraints. It provides hands-on experience in deploying, troubleshooting, optimizing, and maintaining enterprise infrastructure while preparing for the CCNP Enterprise certification.