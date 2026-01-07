# Interface Configuration Commands

## Entering Interface Configuration

| Command | Description |
|---------|-------------|
| `interface <type> <number>` | Enter interface config mode (e.g., `interface g0/0`) |
| `interface range <type> <range>` | Configure multiple interfaces (e.g., `interface range g0/0-3`) |

## Basic Interface Commands

| Command | Description |
|---------|-------------|
| `shutdown` | Administratively disable the interface |
| `no shutdown` | Enable the interface |
| `description <text>` | Add description to the interface |

## Layer 3 Interface Configuration (Routers)

| Command | Description |
|---------|-------------|
| `ip address <ip-address> <subnet-mask>` | Assign IPv4 address to interface |
| `ip address <ip-address> <subnet-mask> secondary` | Assign secondary IPv4 address |
| `ip address dhcp` | Obtain IP address via DHCP |
| `ipv6 address <ipv6-address>/<prefix>` | Assign IPv6 address |
| `ipv6 address autoconfig` | Enable SLAAC for IPv6 |
| `ipv6 enable` | Enable IPv6 on interface |

## Speed and Duplex Configuration

| Command | Description |
|---------|-------------|
| `speed <10|100|1000|auto>` | Set interface speed |
| `duplex <half|full|auto>` | Set duplex mode |
| `mdix auto` | Enable automatic MDI/MDIX crossover |

## Switch Virtual Interface (SVI)

| Command | Description |
|---------|-------------|
| `interface vlan <vlan-id>` | Create/enter SVI for VLAN |
| `ip default-gateway <ip-address>` | Set default gateway for switch |

## Loopback Interface

| Command | Description |
|---------|-------------|
| `interface loopback <number>` | Create/enter loopback interface |

## Show Commands

| Command | Description |
|---------|-------------|
| `show interfaces` | Display all interface details |
| `show interfaces <type> <number>` | Display specific interface details |
| `show ip interface brief` | Display summary of all interfaces (IPv4) |
| `show ipv6 interface brief` | Display summary of all interfaces (IPv6) |
| `show interfaces status` | Display interface status (switches) |
| `show interfaces trunk` | Display trunk interface information |
| `show interfaces description` | Display interface descriptions |
| `show interfaces counters` | Display interface packet counters |

## Interface Error Commands

| Command | Description |
|---------|-------------|
| `show interfaces <int>` | Shows CRC errors, collisions, runts, giants |
| `clear counters` | Reset interface counters |

## Router Sub-interface (Router-on-a-Stick)

| Command | Description |
|---------|-------------|
| `interface <type>.<subinterface>` | Create sub-interface (e.g., `interface g0/0.10`) |
| `encapsulation dot1q <vlan-id>` | Associate sub-interface with VLAN |
| `encapsulation dot1q <vlan-id> native` | Configure native VLAN on sub-interface |
