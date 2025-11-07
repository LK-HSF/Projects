# Active Directory & DHCP Lab (Cisco + Windows Server)

 

## Overview

This lab demonstrates a basic Active Directory Domain Services (AD DS) deployment with a DHCP Server role and VLAN segmentation using Cisco router and switch configuration. 

The setup includes one Windows Server (acting as Domain Controller + DHCP), one Windows Client (dynamic IP), a Layer 2 switch, and a router providing inter-VLAN routing.

 

---

 

## Network Topology

 

| Device | Interface / VLAN | IP Address | Notes |

|--------|------------------|-------------|-------|

| **Router (R1)** | f0/0.10 | 192.168.10.1 /24 | VLAN 10 Gateway (Clients) |

| | f0/0.20 | 192.168.20.1 /24 | VLAN 20 Gateway (Servers) |

| | ip helper-address | 192.168.20.10 | DHCP relay for VLAN 10 |

| **Switch (SW1)** | f0/1 | Trunk | Connected to router |

| | f0/2 | VLAN 10 | Client access port |

| | f0/3 | VLAN 20 | Server access port |

| **Server (WS22-DC01)** | Ethernet | 192.168.20.10 /24 | AD DS + DHCP Server |

| **Client (W11P-CLIENT)** | Ethernet | DHCP | Receives dynamic IP from server |

 

---

 

## Server Configuration

 

| Setting | Value |

|----------|--------|

| IP Address | 192.168.20.10 |

| Subnet Mask | 255.255.255.0 |

| Default Gateway | 192.168.20.1 |

| DNS Server | 192.168.20.10 |

| Roles Installed | Active Directory Domain Services, DHCP Server |

| Domain Name | lab.local |

 

---

 

## VLAN Summary

 

| VLAN | Purpose | Subnet |

|------|----------|--------|

| 10 | Clients | 192.168.10.0/24 |

| 20 | Servers | 192.168.20.0/24 |

 

---

 

## Screenshots

 

| Screenshot | Description |

|-------------|-------------|

| router-cfg.png | Router configuration showing subinterfaces and DHCP relay |

| switch-cfg.png | Switch configuration showing VLANs and trunk/access ports |

| server-cfg.png | Server configuration showing static IP and DHCP scope setup |

| client-dynamic-ip.png | Client computer showing dynamic IP assignment from DHCP |

 

*(All images should be placed in the `/images` folder.)*

 

---

 

## Key Learning Points

- Promoting a Windows Server to a Domain Controller 

- Configuring DHCP with proper scopes and VLAN relay 

- Using VLANs for logical network segmentation 

- Setting up inter-VLAN routing on a Cisco router 

- Verifying client IP assignment and domain connectivity 

 

---

 

## Tools Used

- Cisco Packet Tracer (or GNS3) 

- Windows Server 2022 

- Windows 11 Pro 

 

---
## Notes

This project demonstrates a simple but realistic small business network environment where AD DS, DHCP, and VLANs work together. It serves as a foundation for future labs involving Group Policy, DNS, and additional domain controllers.
