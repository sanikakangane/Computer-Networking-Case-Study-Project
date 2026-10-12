# Gatewick Costume & Prop Rental House — Computer Network Design

A Cisco Packet Tracer case study focused on designing and implementing a structured IPv4 network for Gatewick Costume & Prop Rental House, including departmental segmentation, inter-VLAN routing, and WAN connectivity to a remote Prop Workshop.

🔗 **[Download Packet Tracer Project (.pkt)](https://github.com/sanikakangane/Computer-Networking-Case-Study-Project/raw/refs/heads/main/GateWick-Project/GateWick-CN-Project.pkt)**

## Project Overview

The project designs a computer network for four departments:

- Warehouse
- Fitting Studio
- Administration
- IT

The network uses an Extended Star topology with a central switch, department switches, a main router, and a point-to-point WAN connection to the offsite Prop Workshop.

## Objectives

- Design an Extended Star network topology.
- Apply VLSM to the `10.200.0.0/22` network with 20% spare capacity.
- Separate departments using VLANs.
- Configure access ports and trunk links.
- Implement IEEE 802.1Q trunking and Router-on-a-Stick inter-VLAN routing.
- Establish a `/30` point-to-point WAN connection.
- Verify VLAN configuration, interfaces, trunks, and end-to-end connectivity.

## Technologies Used

- Cisco Packet Tracer
- IPv4 Addressing and VLSM
- VLANs
- IEEE 802.1Q Trunking
- Router-on-a-Stick
- Inter-VLAN Routing
- Point-to-Point WAN
- ICMP and Ping Testing
- Cisco IOS CLI

## Network Design

The network follows an Extended Star topology in which departmental switches connect to a central core switch.

### VLAN and IP Addressing Plan

| VLAN ID | Department | Network | Default Gateway |
|---|---|---|---|
| 10 | Warehouse | `10.200.0.0/26` | `10.200.0.1` |
| 20 | Fitting Studio | `10.200.0.64/27` | `10.200.0.65` |
| 30 | Administration | `10.200.0.96/28` | `10.200.0.97` |
| 40 | IT | `10.200.0.112/28` | `10.200.0.113` |

### WAN Addressing

| Device | Interface | IP Address |
|---|---|---|
| R0-Main | G0/0/1 | `10.200.0.129/30` |
| R1-Workshop | G0/0/0 | `10.200.0.130/30` |

The `/30` subnet provides two usable IPv4 addresses for the point-to-point connection.

## Network Devices

**Routers**
- R0-Main
- R1-Workshop

**Switches**
- S0-Core
- S1-Admin
- S2-Fitting
- S3-IT
- S4-Warehouse

**End Devices**

Nine PCs are distributed across the four departments.

## Key Implementations

### 1. VLAN Segmentation

Each department is assigned a separate VLAN to create distinct logical broadcast domains.

### 2. Trunk Links

IEEE 802.1Q trunk links connect the core switch to department switches and the main router, carrying traffic for multiple VLANs.

### 3. Router-on-a-Stick

Subinterfaces on R0-Main provide default gateways and enable communication between the four departmental VLANs.

### 4. VLSM

The `10.200.0.0/22` address block is divided into subnet sizes suited to the departments' host requirements, with additional address space retained for future expansion.

### 5. WAN Connectivity

A point-to-point connection links R0-Main to R1-Workshop using the `10.200.0.128/30` subnet.

## Verification and Testing

The following checks are documented in the project report:

- VLAN verification using `show vlan brief`
- Trunk verification using `show interfaces trunk`
- Router interface verification using `show ip interface brief`
- Same-VLAN connectivity testing
- Inter-VLAN connectivity testing
- WAN connectivity testing between the routers

### Results

| Test | Result |
|---|---|
| VLAN configuration | Successful |
| Trunk configuration | Successful |
| Router subinterfaces | Successful |
| PC0 → PC1 | 4/4 replies, 0% packet loss |
| PC0 → PC4 | 4/4 replies, 0% packet loss |
| PC0 → R1-Workshop | 4/4 replies, 0% packet loss |

## Important Note

IP addresses were configured manually. DHCP and DNS are discussed in the report as networking concepts but were not implemented as services in this project.

## Learning Outcomes

- Understanding IPv4 subnetting and VLSM.
- Configuring VLANs and access ports.
- Understanding trunk links and IEEE 802.1Q.
- Implementing inter-VLAN routing with Router-on-a-Stick.
- Establishing point-to-point WAN connectivity.
- Verifying network configurations using Cisco IOS commands.
- Troubleshooting basic connectivity issues.

## Author

**Sanika Kangane 👩🏻‍💻**  
B.Tech Computer Science and Engineering — Class of 2029

---

*Academic project completed using Cisco Packet Tracer.*
