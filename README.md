# ConnectX Multi-Branch Enterprise Network

A complete enterprise networking project designed and implemented in
**Cisco Packet Tracer** for a fictional multi-branch organization,
**ConnectX**.

The project demonstrates practical network planning, IP addressing and
subnetting, WAN/LAN topology design, dynamic routing with OSPF, network
services, basic security, testing, maintenance, and future scalability.

## 📌 Project Overview

The network connects **Headquarters in Amman** with branch offices in:

-   Amman HQ
-   Irbid
-   Zarqa
-   Aqaba
-   Beirut
-   Cairo

The network is designed with:

-   **Star topology** for the LANs
-   **Ring topology** for the WAN
-   **OSPF** for dynamic routing
-   Static IP addressing for infrastructure devices
-   DHCP for end-user devices
-   Multiple network services including DHCP, DNS, FTP, HTTPS, and Email

The project was developed as a university networking project at **Al
Hussein Technical University (HTU)**.

## 🛠️ Technologies & Concepts

### Network Simulation

-   Cisco Packet Tracer

### Networking

-   IPv4 addressing
-   Subnetting
-   `/27` LAN subnets
-   `/30` point-to-point WAN subnets
-   LAN and WAN design
-   Star topology
-   Ring topology
-   Static and dynamic IP addressing
-   DHCP
-   DHCP relay using `ip helper-address`

### Routing

-   OSPF (Open Shortest Path First)
-   OSPF route selection
-   Routing tables
-   Dynamic route propagation

### Network Services

-   DHCP
-   DNS
-   FTP
-   HTTPS
-   Email (SMTP / POP3)

### Security

-   Router passwords
-   Encrypted privileged access
-   HTTPS instead of HTTP
-   User authentication for FTP and Email services

## 🗺️ Network Topology

The WAN uses a ring structure:

``` text
                 Amman HQ
                /        \
             Irbid        Cairo
               |            |
             Zarqa        Beirut
                \          /
                   Aqaba
```

Each location has a local LAN using a star topology, with end devices
connected through switches to the local router.

### Why these topologies?

**Star topology (LAN):** - Easy installation - Easy expansion - Fault
isolation - Straightforward troubleshooting

**Ring topology (WAN):** - Provides an alternative path between
locations - Supports network redundancy when appropriately implemented

## 🔢 IP Addressing

### LAN

The LAN address space is:

``` text
192.168.1.0/24
```

It is divided into `/27` subnets.

Subnet mask:

``` text
255.255.255.224
```

The project uses separate LAN subnets for each location, with an
additional subnet reserved for future use.

  Location       Network
  -------------- --------------------
  Amman HQ       `192.168.1.0/27`
  Amman Branch   `192.168.1.32/27`
  Cairo          `192.168.1.64/27`
  Beirut         `192.168.1.96/27`
  Aqaba          `192.168.1.128/27`
  Zarqa          `192.168.1.160/27`
  Irbid          `192.168.1.192/27`
  Future Use     `192.168.1.224/27`

### WAN

The WAN address space is:

``` text
100.0.0.0/8
```

Point-to-point router connections use `/30` subnets.

Subnet mask:

``` text
255.255.255.252
```

WAN links include:

-   Amman ↔ Irbid
-   Irbid ↔ Zarqa
-   Zarqa ↔ Aqaba
-   Aqaba ↔ Beirut
-   Beirut ↔ Cairo
-   Cairo ↔ Amman

## 📡 IP Addressing Strategy

Infrastructure devices use **static IP addresses**, including:

-   Routers
-   Servers
-   Printers

End-user PCs use **DHCP** so their addresses can be assigned
automatically.

This approach makes infrastructure devices predictable while reducing
the manual configuration required for end-user devices.

## 🚦 OSPF Routing

The project uses **OSPF** as its dynamic routing protocol.

OSPF was selected instead of RIP because the network contains multiple
interconnected locations and requires a routing protocol that can scale
with the network.

The implementation demonstrates:

-   Dynamic route advertisement
-   OSPF routing tables
-   Route selection based on OSPF metrics
-   Fast convergence when network topology changes

You can inspect the routing information on a router with:

``` text
show ip route
```

## 🖥️ Network Services

### DHCP

DHCP automatically provides clients with:

-   IP address
-   Subnet mask
-   Default gateway
-   DNS server

DHCP pools are configured for the different LAN subnets.

DHCP relay is implemented using:

``` text
ip helper-address
```

This allows clients on different LANs to reach the DHCP server.

### DNS

DNS maps the organization's domain name to the web server's IP address.

This allows users to access the website using a domain name instead of
manually entering an IP address.

### FTP

FTP provides file-transfer functionality between users across the
network.

User accounts are configured with usernames, passwords, and permissions.

### HTTPS

The organization's website is provided through HTTPS.

HTTP is disabled in the implementation and HTTPS is enabled to provide
encrypted web communication.

### Email

The network includes an internal email service using:

-   SMTP for sending email
-   POP3 for receiving email

Users are configured with individual accounts.

## 🔐 Security

Basic security measures implemented in the project include:

-   Router passwords
-   Encrypted privileged-access passwords
-   HTTPS instead of HTTP
-   Authentication for FTP
-   Authentication for Email services

The project also identifies several possible future security
improvements, including:

-   Firewall deployment
-   VLAN segmentation
-   Centralized AAA authentication
-   Stronger access-control policies

## 🧪 Testing

The network was designed with several tests to verify functionality.

  Test   Purpose                   Method
  ------ ------------------------- --------------------
  T1     End-to-end connectivity   `ping`
  T2     Internal email delivery   Send/receive email
  T3     DNS resolution            Web browser
  T4     FTP functionality         FTP connection
  T5     OSPF routing              `show ip route`

### Example

To test connectivity from a PC:

``` text
ping <destination-ip>
```

To inspect routing information:

``` text
show ip route
```

OSPF routes should appear in the routing table.

## ▶️ How to Use the Project

### Requirements

You need:

-   **Cisco Packet Tracer**
-   The `.pkt` project file included in this repository

### Steps

1.  Download or clone this repository.
2.  Open the `.pkt` file using Cisco Packet Tracer.
3.  Wait for the topology to load.
4.  Select a PC, router, or server to inspect its configuration.
5.  Use the PC Command Prompt to test connectivity.
6.  Use router CLI commands to inspect routing and configuration.
7.  Test the configured network services.

### Useful Commands

Check interfaces:

``` text
show ip interface brief
```

Check the routing table:

``` text
show ip route
```

Check OSPF information:

``` text
show ip ospf
```

Test connectivity:

``` text
ping <destination-ip>
```

Trace a route:

``` text
traceroute <destination-ip>
```

## 📁 Repository Structure

``` text
ConnectX-Networking/
│
├── README.md
└── final assignment.pkt
```

The repository contains the Cisco Packet Tracer implementation. The
detailed university report is not included in the repository.

## 🚀 Future Improvements

The project identifies several possible improvements for a larger
production network.

### Security

-   Add a firewall
-   Introduce VLAN segmentation
-   Implement centralized AAA/RADIUS authentication

### Performance

-   Load balancing
-   Quality of Service (QoS)
-   Improved OSPF area design

### Scalability

-   Larger or more flexible subnet allocation
-   Additional switches
-   Redundant routers and WAN links

## 📚 Learning Outcomes

This project provided practical experience with:

-   Enterprise network planning
-   IPv4 subnetting
-   Network topology design
-   Cisco router and switch configuration
-   OSPF dynamic routing
-   DHCP and DHCP relay
-   DNS, FTP, HTTPS, and Email services
-   Basic network security
-   Connectivity troubleshooting
-   Network testing and documentation
-   Scalability and maintenance planning

## 👨‍💻 Author

**Yousof Flaifel**

Data Science & AI Student\
Al Hussein Technical University (HTU)

------------------------------------------------------------------------

*University Networking Project --- 2025*
