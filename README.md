<h1 align="center">Cisco Network Configuration and Routing Project</h1>

<p align="center">
  <b></b> Static Routing Between Two LANs Cisco Packet Tracer Project
</p>

<p align="center">
  📄 <b>Download PDF Documentation:</b><br>
  [ EN ] <a href="https://github.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/blob/main/Cisco_Network_Configuration_and_Routing_Project.pdf"><b>[ English Version PDF ]</b></a><br>
  [ ES ] <a href="https://github.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/blob/main/Proyecto_Configuracion_y_Enrutamiento_de_Redes_Cisco.pdf"><b>[ Versión en Español PDF ]</b></a>
</p>

<hr>

## 📋 Index

- [1. Introduction](#1-introduction)
- [2. Objective](#2-objective)
- [3. Network Topology](#3-network-topology)
- [4. Work Performed](#4-work-performed)
  - [4.1 Physical and Logical Cabling](#41-physical-and-logical-cabling)
  - [4.2 Host Configuration](#42-host-configuration)
  - [4.3 Switch Configuration](#43-switch-configuration)
  - [4.4 Router Configuration](#44-router-configuration)
  - [4.5 Static Routing Implementation](#45-static-routing-implementation)
  - [4.6 Verification & Testing](#46-verification--testing)
- [5. Skills Demonstrated](#5-skills-demonstrated)
- [6. Tools Used](#6-tools-used)

---

## 1. Introduction

This is a network configuration exercise that I carried out in Cisco Packet Tracer. It covers the design, cabling and configuration of a small three-segment network - the RED LAN, the BLUE LAN and the GREEN link between them including IP addressing, switch and router setup, and static routing so the two LANs can communicate. It applies concepts from the SMR course together with my own self-study. The screenshots below show the main steps rather than every one, since the same procedure was applied the same way to both the RED and BLUE networks.

---

## 2. Objective

Design, cable and configure a two-site network (RED and BLUE) in Cisco Packet Tracer, with IP addressing, switch and router configuration, and static routing to give end-to-end connectivity between the two LANs.

---

## 3. Network Topology

The network is made up of two separate LANs, RED and BLUE, each with its own subnet, joined by a point-to-point link (GREEN) between two Cisco routers:

- **RED:** `172.16.0.0/24` (Gateway: `172.16.0.1`) — 2 PCs, 1 switch, 1 router (`RED1`)
- **BLUE:** `192.168.0.0/24` (Gateway: `192.168.0.1`) — 2 PCs, 1 switch, 1 router (`BLUE1`)
- **GREEN (link):** `89.12.0.0/24` — `RED1` ↔ `BLUE1` point-to-point link

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%201.PNG" alt="Figure 1" width="100%">
</p>

---

## 4. Work Performed

### 4.1 Physical and Logical Cabling
I connected all the PCs, switches and routers according to the topology, checking that each cable went to the correct interface between the hosts, the switches and the gateway routers.

### 4.2 Host Configuration
I assigned a static IP address to every host on both networks — giving Layer 3 IP address, subnet mask, default gateway and DNS reachability inside each LAN. The screenshots show the RED hosts; the BLUE hosts (`BLUE_PC1`, `BLUE_PC2`) were configured the same way.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%202.PNG" alt="Figure 2" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%203.PNG" alt="Figure 3" width="100%">
</p>

### 4.3 Switch Configuration
I configured a hostname and an enable secret (privileged-mode) password on both switches, `RED_SW1` and `BLUE_SW1`, to protect administrative access and identify each device. The screenshot shows `RED_SW1`; `BLUE_SW1` was configured identically.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%204.PNG" alt="Figure 4" width="100%">
</p>

### 4.4 Router Configuration
I configured the hostname, the enable secret password and the interface IP addresses on both routers, `RED1` and `BLUE1`, then brought the interfaces up with `no shutdown` and verified Layer 3 connectivity with ping tests from the hosts to their gateways. The enable secret used here is a common lab default, suitable only for a practice network like this; a real network would need a strong, unique password and extra controls such as AAA or SSH-only management.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%205.PNG" alt="Figure 5" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%206.PNG" alt="Figure 6" width="100%">
</p>

### 4.5 Static Routing Implementation
At first each router only knew about its own directly connected network, so RED and BLUE could not communicate. I configured a static route (`ip route`) on each router, pointing to the remote subnet through the next-hop address on the link between them. This gave both routers a path to the other side.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%207.PNG" alt="Figure 7" width="100%">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%208.PNG" alt="Figure 8" width="100%">
</p>

### 4.6 Verification & Testing
I tested end-to-end connectivity with ping between a RED host and a BLUE host. The first ping, run before the static routes were in place, failed with "Destination host unreachable" (100% packet loss) — the expected result, which confirmed why the routing in Section 4.5 was needed. After both static routes were added, a second ping succeeded with 0% packet loss and normal ICMP replies, confirming that the two networks could now communicate.

<p align="center">
  <img src="https://raw.githubusercontent.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/main/Figure%209.PNG" alt="Figure 9" width="100%">
</p>

---

## 5. Skills Demonstrated

- IP addressing and subnetting (IPv4)
- Switch and router configuration (hostname, enable secret)
- Cisco IOS command-line interface (CLI)
- Static routing configuration and troubleshooting
- Connectivity testing and diagnostics with ping (ICMP)
- Basic credential-hygiene awareness on network devices
- Clear technical documentation of a multi-step exercise

---

## 6. Tools Used

- Cisco Packet Tracer
  
---

## 7. Cisco Packet Tracer Lab File

<p align="center">
  🌐 <b>Open or Download Lab File:</b><br>
  <a href="https://github.com/radu-hatos/Cisco_Network_Configuration_and_Routing_Project/blob/main/Cisco_Network_Configuration_and_Routing_Project.pkt"><b>[ Cisco Packet Tracer .pkt Lab File ]</b></a>
</p
