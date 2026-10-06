# Small Business Network Design

## Overview
This project demonstrates the design and configuration of a small business network using Cisco Packet Tracer. The network separates Sales and IT into two IPv4 networks connected through a Cisco router, with DHCP used to automatically assign client IP addresses.

The project was built to practice foundational networking concepts including IPv4 addressing, subnetting, routing, DHCP, Cisco IOS configuration, connectivity testing, and network troubleshooting.

## Network Topology

![Network Topology](network-topology.png)

### Devices
- 1 Cisco 2911 Router
- 2 Cisco 2960 Switches
- 6 Client PCs
- 1 Company Server

## Network Design

| Network | Network Address | Subnet Mask | Default Gateway |
|---|---|---|---|
| Sales | 192.168.10.0/24 | 255.255.255.0 | 192.168.10.1 |
| IT | 192.168.20.0/24 | 255.255.255.0 | 192.168.20.1 |

The company server uses the static IP address `192.168.20.100`.

## Router Configuration

The Cisco 2911 router provides communication between the Sales and IT networks.

- `GigabitEthernet0/0` → `192.168.10.1/24`
- `GigabitEthernet0/1` → `192.168.20.1/24`

Both interfaces were configured and enabled through the Cisco IOS command-line interface.

## DHCP Configuration

DHCP pools were configured on the router for both departments.

**Sales DHCP Pool**
- Network: `192.168.10.0/24`
- Default Gateway: `192.168.10.1`

**IT DHCP Pool**
- Network: `192.168.20.0/24`
- Default Gateway: `192.168.20.1`

Addresses `192.168.10.1–192.168.10.9` and `192.168.20.1–192.168.20.9` were excluded from DHCP allocation. The server address `192.168.20.100` was also excluded to preserve its static configuration.

![Router Configuration](router-configuration.png)

## Testing and Verification

Connectivity was tested from a Sales workstation to the company server located on the IT network.

The Sales workstation successfully received the following configuration through DHCP:

- IPv4 Address: `192.168.10.10`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.10.1`

A ping from `192.168.10.10` to the company server at `192.168.20.100` returned all four packets successfully with **0% packet loss**, confirming successful communication between the two networks.

![Connectivity Test](connectivity-test.png)

## Skills Demonstrated

- Cisco Packet Tracer
- TCP/IP and IPv4 Addressing
- Subnetting
- Cisco Routing and Switching Fundamentals
- DHCP Configuration
- Cisco IOS CLI
- Static Server Addressing
- Inter-Network Communication
- Connectivity Testing
- Network Troubleshooting

## Project Files

The `Small_Business_Network.pkt` file contains the complete Cisco Packet Tracer topology and configuration.
