# CCNP Enterprise Practical Lab

## Objective
The primary objective of this project is to implement, verify, and troubleshoot a complex Enterprise network environment. This lab covers advanced routing, switching, security, and automation tasks required for CCNP Enterprise certification (ENCOR + ENARSI).

## Topology
The lab is designed using EVE-NG. The topology features a hierarchical campus (Core/Distribution/Access), multi-site branch connectivity, and a simulated Internet edge with redundant ISP connections.
![Network Topology](topology/topology-main.png)
*Figure 1: Main Network Topology*


## What Was Configured
Key technologies implemented in this lab include:
*   **Layer 2:** VLANs, Trunking, EtherChannel (L2/L3), STP/RSTP/MSTP.
*   **Layer 3:** OSPFv2, EIGRP, Route Redistribution, HSRP.
*   **WAN:** DMVPN Phase 2, GRE, Site-to-Site IPsec (IKEv1/v2).
*   **Security:** ACLs, Port Security, DHCP Snooping, ZBFW, CoPP.
*   **Services:** DHCP Server/Relay, NAT/PAT, IP SLA.

## Repository Contents
```text
.
├── docs/            # Lab Guide PDFs and documentation
├── eve-ng/          # EVE-NG topology files (.unl)
├── configs/         # Device configurations (running-config)
├── topology/        # Network diagrams and screenshots
└── ansible/         # Automation scripts and Jinja2 templates
```
## Planned Improvements

- [ ] Implement Python/Netmiko scripts for automated configuration backups.
- [ ] Add network monitoring integration (SNMP and Syslog).
- [ ] Complete IPv6 dual-stack migration.

## Tools Used

- **Network Simulator:** EVE-NG
- **Network Operating System:** Cisco IOS-XE
- **Automation:** Ansible, Jinja2
- **Version Control:** Git and GitHub

## About This Project

This lab is a professional-grade study environment designed to simulate real-world enterprise network scenarios and operational constraints. It provides hands-on experience in deploying, troubleshooting, optimizing, and maintaining enterprise infrastructure while preparing for the CCNP Enterprise certification.