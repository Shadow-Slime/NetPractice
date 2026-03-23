*This project has been created as part of the 42 curriculum by ddamiba.*

# NetPractice

## Description

NetPractice is a networking configuration exercise project from the 42 curriculum. The goal is to develop a practical understanding of TCP/IP addressing and network routing by solving a series of progressively complex network topology puzzles.

Each level presents a broken or incomplete network diagram — containing routers, switches, and hosts — and requires correctly configuring IP addresses, subnet masks, and routing tables so that all devices can communicate as intended. The project covers real-world scenarios including multi-router topologies, inter-subnet routing, public vs. private addressing, and the distinction between host-facing and point-to-point links.

By completing the 10 levels, the student builds hands-on familiarity with how packets are forwarded across networks, how subnet masks carve address space into distinct blocks, and how routing tables determine the path a packet takes from source to destination.

## Instructions

### Running the training interface

The shell script provided may not be executable from the start:

```bash
chmod +x run.sh
```

To launch the training interface locally in your browser:

```bash
./run.sh
```

### Working through the levels

- The interface presents 10 levels, each with a network diagram containing misconfigured or missing values
- Fill in IP addresses, subnet masks, and routing table entries until the network validates successfully
- Use the **Check** button to verify your configuration for the current level
- Corrections can be made at any time before exporting

### Exporting configurations

Once a level is solved, export its configuration using the **Get my config** button inside the interface. This downloads a JSON configuration file for that level.

### Submission requirements

- Solve all 10 levels and export a configuration file for each one
- Place all 10 exported configuration files at the **root of your Git repository**
- Files should be named as provided by the export function (e.g. `level1.json` through `level10.json`)
- Include this `README.md` at the root of the repository as well

## Resources

### Networking concepts studied

The following concepts are covered across the 10 levels of this project:

- **TCP/IP addressing** — how IPv4 addresses are structured, what each octet represents, and how addresses are assigned to network interfaces
- **Subnet masks and CIDR notation** — how masks like /28 or 255.255.255.240 divide an address space into fixed-size blocks, and how prefix length determines block size and count
- **Subnetting** — identifying network boundaries, calculating valid host ranges, and avoiding overlapping subnets
- **Routing tables** — how routers use longest prefix match to forward packets, the role of default routes (0.0.0.0/0), and how missing or incorrect routes cause one-way communication failures
- **Default gateways** — how hosts hand off traffic destined for outside their local subnet
- **Routers and switches** — the distinction between layer 2 switching (same subnet) and layer 3 routing (between subnets), and how multi-router topologies require explicit inter-router routes
- **Point-to-point links** — the use of /30 (255.255.255.252) masks for router-to-router links with only two usable addresses per block
- **Public vs. private IP addresses** — RFC 1918 reserved ranges (10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16) and why they are not routable on the public internet
- **OSI model layers** — understanding which layer handles addressing (layer 3) vs. frame delivery (layer 2)
- **NAT (Network Address Translation)** — conceptual understanding of how private networks reach the internet by rewriting source addresses at the border router

### Reference materials

- **TCP/IP Model — GeeksforGeeks**
  https://www.geeksforgeeks.org/computer-networks/tcp-ip-model/
  Overview of the TCP/IP stack, its layers, and how addressing operates at the network layer.

- **TCP/IP Addressing — IBM AIX Documentation**
  https://www.ibm.com/docs/en/aix/7.2.0?topic=protocol-tcpip-addressing
  Technical reference on IPv4 address classes, subnet masks, and how addressing is applied in practice.

- **Networking Fundamentals — YouTube Playlist (Practical Networking)**
  https://www.youtube.com/playlist?list=PLIhvC56v63IJVXv0GJcl9vO5Z6znCVb1P
  Video series covering subnetting, routing, switching, and TCP/IP fundamentals with visual explanations.

### AI usage

**Claude (claude.ai)** was used throughout this project as a learning aid and sanity checker in two main ways:

- **Concept explanations** — used to clarify how subnet masks divide address space into blocks, why certain prefix lengths (e.g. /30 vs /28) are appropriate for different link types, and how longest prefix match governs routing decisions
- **Exercise-specific debugging** — used on a case-by-case basis to diagnose why a particular configuration was failing, such as identifying overlapping subnets, wrong next-hop addresses in routing tables, missing return routes on the internet side, or mismatched masks between directly connected interfaces