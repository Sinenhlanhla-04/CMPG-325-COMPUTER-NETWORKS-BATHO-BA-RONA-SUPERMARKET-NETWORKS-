# Batho Ba Rona Supermarket — Network Design

## 📌 Project Overview

This repository contains the **First Milestone** of the Batho Ba Rona Supermarket network design project for **CMPG 325 — Computer Networks**.

The project focuses on designing a network infrastructure for Batho Ba Rona Supermarket, a small retail supermarket located in Mahikeng. The network is intended to support the supermarket's Point-of-Sale (POS) systems, administrative users, staff Wi-Fi, and server/inventory systems.

This milestone documents the network requirements, proposed physical and logical topology, IP addressing plan, VLAN segmentation, growth planning, and the initial default routing design.

> **⚠️ Project Status: First Milestone — Work in Progress**

The network project is **not yet completed**. Additional configurations, testing, verification, documentation, and requirements may be completed in subsequent milestones.

---

## 🏪 Client Background

Batho Ba Rona Supermarket is a small retail supermarket located in **Mahikeng**, serving the local community with grocery and household products.

The supermarket depends on:

* Point-of-Sale (POS) systems
* Administrative systems
* Staff wireless connectivity
* Inventory and stock management systems

The network must therefore be reliable and easy to maintain because the business has only **one part-time IT support person** managing its technology needs.

---

## 🎯 First Milestone Objectives

The main objectives covered in this milestone are:

* Analyse the client's network requirements.
* Use the assigned `192.168.17.0/24` address block.
* Develop a physical network topology.
* Develop a logical network topology.
* Divide the network into appropriate VLANs.
* Create a VLSM-based IP addressing plan.
* Plan for a 25% increase in users without requiring renumbering.
* Develop an initial default routing design.

---

## 🌐 Network Segmentation

The proposed network is divided into four main VLANs:

|   VLAN | Department     | Purpose                          |
| -----: | -------------- | -------------------------------- |
| **10** | POS            | Point-of-Sale systems            |
| **20** | Administration | Administrative users and systems |
| **30** | Wi-Fi/Staff    | Staff wireless devices           |
| **40** | Server         | Inventory and stock systems      |

Logical segmentation was selected to separate the different areas of the supermarket and make the network easier to manage.

---

## 🖥️ Physical Topology

The proposed physical topology includes:

* ISP router
* Edge router
* Core switch
* Three access switches
* POS devices
* Administration devices
* Wi-Fi/Staff devices
* Server systems

The physical topology represents how the network devices are connected and how the different departments will access the network.


The logical topology represents the VLAN assignments, subnet allocations, gateway addresses, and WAN connection.

The `192.168.17.0/24` address block is divided between the different network segments using VLSM.

#IP ADDRESS PLANNING
1

VLSM is used to divide the address block according to the estimated requirements of each department. The subnets are also sized to accommodate the required **25% user growth** without requiring network renumbering.

|                 VLAN | Network            | Subnet Mask       | Usable Hosts | Gateway         |
| -------------------: | ------------------ | ----------------- | -----------: | --------------- |
|       **20 – Admin** | `192.168.17.0/27`  | `255.255.255.224` |           30 | `192.168.17.1`  |
| **30 – Wi-Fi/Staff** | `192.168.17.32/27` | `255.255.255.224` |           30 | `192.168.17.33` |
|         **10 – POS** | `192.168.17.64/28` | `255.255.255.240` |           14 | `192.168.17.65` |
|      **40 – Server** | `192.168.17.80/29` | `255.255.255.248` |            6 | `192.168.17.81` |
|              **WAN** | `192.168.17.88/30` | `255.255.255.252` |            2 | —               |

---

## 📈 Growth Planning

The design considers **CR5**, which requires the network to accommodate a **25% increase in users** without requiring renumbering.

| Department     | Current Devices | 25% Growth | Planned Capacity |
| -------------- | --------------: | ---------: | ---------------: |
| POS            |              10 |       12.5 |          13 → 16 |
| Administration |              15 |      18.75 |          19 → 30 |
| Wi-Fi/Staff    |              20 |         25 |               30 |
| Server         |               3 |       3.75 |            4 → 6 |

The intention is to allocate sufficient address space during the initial design so that additional devices can be added later without changing the existing addressing structure.

---

## 🔀 Initial Default Routing Design

The proposed design uses a **static default route** on the edge router.


The edge router will use this route to forward traffic that is not destined for a local network toward the ISP router.

A static default route was selected because the network needs to remain relatively simple and manageable for the available IT support resources.

> **Note:** Routing configuration and verification form part of the ongoing project work and are not presented as fully completed in this milestone.

---

## 🛠️ Tools and Technologies

The project currently uses:

* **Cisco Packet Tracer**
* IPv4 addressing
* VLSM
* VLANs
* Ethernet switching
* Router configuration
* Static/default routing

---

## 📂 Repository Structure

The repository may contain the following files as the project develops:

Batho-Ba-Rona-Supermarket/
│
├── README.md
│
├── packet-tracer/
│   └── Batho-Ba-Rona-Supermarket.pkt
│
├── documentation/
│   └── Batho Ba Rona Supermarket.docx
│
├── images/
│   ├── physical-topology.png
│   └── logical-topology.png
│
└── screenshots/
    └── ...
```

Additional files and screenshots will be added as the project progresses through future milestones.

---

## 📊 Current Milestone Status

| Component              | Status                      |
| ---------------------- | --------------------------- |
| Client requirements    | ✅ Completed for Milestone 1 |
| Client analysis        | ✅ Completed for Milestone 1 |
| Physical topology      | ✅ Designed                  |
| Logical topology       | ✅ Designed                  |
| VLAN planning          | ✅ Planned                   |
| IP addressing plan     | ✅ Designed                  |
| VLSM                   | ✅ Planned                   |
| 25% growth planning    | ✅ Planned                   |
| Default routing design | 🔄 Initial design           |
| Full configuration     | 🔄 In progress              |
| Network verification   | 🔄 To be completed          |
| Final documentation    | 🔄 To be completed          |

---

## 🚧 Future Work

The project will continue beyond this first milestone. Future work may include:

* Completing device configurations.
* Configuring VLANs and switch ports.
* Configuring routing.
* Verifying connectivity between network segments.
* Testing the default route.
* Performing `ping` and `traceroute` tests.
* Adding configuration and verification screenshots.
* Updating the documentation as new milestones are completed.

---

## 👤 Project Information

**Client:** Batho Ba Rona Supermarket
**Module:** CMPG 325 — Computer Networks
**Project ID:** CMPG325-2026-015
**Client ID:** CLI-015
**Location:** Mahikeng

---

## 📌 Project Status

**Current Stage: First Milestone**

This repository represents the **current stage of the project and is not the final completed network implementation**. The design and documentation will be updated as additional milestones and requirements are completed.

