# Batho Ba Rona Supermarket — Network Design

## 📌 Project Overview
Individual semester project for **CMPG 325 — Computer Networks** (Project ID: CMPG325-2026-015, Client ID: CLI-015).

The project designs and simulates, in Cisco Packet Tracer, the network for Batho Ba Rona Supermarket, a small retail supermarket in Mahikeng. The network supports the Point-of-Sale (POS) systems, administration users, staff Wi-Fi and the server. The client has only one part-time IT support person, so the design is kept simple and easy to maintain.

**Status:** Implementation complete. The video demonstration is the final item.

## 🌐 Network Design
The assigned block 192.168.17.0/24 is divided with VLSM:

| VLAN | Department | Network | Usable Hosts | Gateway |
|---|---|---|---|---|
| 20 | Administration | 192.168.17.0/27 | 30 | 192.168.17.1 |
| 30 | Wi-Fi/Staff | 192.168.17.32/27 | 30 | 192.168.17.33 |
| 10 | POS | 192.168.17.64/28 | 14 | 192.168.17.65 |
| 40 | Server | 192.168.17.80/29 | 6 | 192.168.17.81 |
| — | WAN to ISP | 192.168.17.88/30 | 2 | .89 (ISP), .90 (edge) |

Devices: ISP router, edge router (router-on-a-stick), core switch, three access switches, an access point, and PCs, a printer, a server and a laptop.

## 🔀 Assigned Challenge — Default Routing (edge/ISP path)
A static default route on BBR-EDGE-RTR sends all traffic that is not for an internal VLAN to the ISP router:

`ip route 0.0.0.0 0.0.0.0 192.168.17.89`

**Why it is appropriate:** the supermarket has a single connection to the ISP, so one next hop is enough. A static route is simple and suits the one part-time IT person.

**How it was verified:**
- `show ip route` shows `S* 0.0.0.0/0 via 192.168.17.89`.
- BBR-EDGE-RTR pings the ISP router with 100% success, and the traceroute shows a single hop.
- POS-PC1 (VLAN 10), ADMIN-PC1 (VLAN 20) and STAFF-LAPTOP (VLAN 30) all reach 192.168.17.89 through their gateways.
- ISP-RTR has a return route to 192.168.17.0/24 via 192.168.17.90.

## 📈 Change Request CR5 — 25% User Growth
The subnets were sized so a 25% increase fits without renumbering:

| Department | Current | After +25% | Subnet capacity |
|---|---|---|---|
| POS | 10 | 13 | 14 (/28) |
| Administration | 15 | 19 | 30 (/27) |
| Wi-Fi/Staff | 20 | 25 | 30 (/27) |
| Server | 3 | 4 | 6 (/29) |

## 🛠️ Troubleshooting Performed
- The SW-POS uplink to BBR-CORE-SW was disconnected and was reconnected (SW-POS Fa0/1 to BBR-CORE-SW Fa0/2).
- The ISP router needed its interface address and a return route.
- BBR-CORE-SW Fa0/4 was an access port in VLAN 1. It was changed to a trunk carrying VLAN 30 so the Wi-Fi VLAN could reach its gateway.

## 📂 Repository Contents
- `Batho Ba Rona Supermarket.docx` — Milestone 1 design documentation
- Milestone 2 documentation (Word document)
- `BathoBarona_CLI-015_Milestone2.pkt` — final Packet Tracer file
- `configs/` — running configurations of BBR-EDGE-RTR and ISP-RTR
- `screenshots/milestone2/` — testing evidence
- `reflection.md` — project reflection
- Earlier Packet Tracer files from Milestone 1

## 🛠️ Tools and Technologies
Cisco Packet Tracer, IPv4, VLSM, VLANs, 802.1Q trunking, router-on-a-stick, static routing.

## 👤 Project Information
**Client:** Batho Ba Rona Supermarket
**Module:** CMPG 325 — Computer Networks
**Project ID:** CMPG325-2026-015
**Client ID:** CLI-015
**Location:** Mahikeng

## 🎓 Academic Integrity

This project was developed as part of the **CMPG 325 — Computer Networks** academic coursework.

Artificial Intelligence (AI) tools were used during the development of this project as a **learning and support resource**, including assistance with understanding networking concepts, clarifying instructions, and improving the organisation and documentation of the project.

The final work reflects my **own understanding, analysis, decision-making, and implementation** of the network design. I did not copy another student's work or submit someone else's project as my own.

All project decisions, configurations, designs, and documentation were reviewed and understood by me. Any external sources or assistance used during the development of the project should be acknowledged in accordance with the academic integrity requirements of **North-West University**.

This repository is intended for **academic and educational purposes** and should not be copied, reproduced, or submitted as another student's work.
