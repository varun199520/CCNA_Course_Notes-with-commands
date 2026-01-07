# Static Routing Commands

## Enable IP Routing

| Command | Description |
|---------|-------------|
| `ip routing` | Enable IP routing (required on Layer 3 switches) |

## Static Route Configuration

| Command | Description |
|---------|-------------|
| `ip route <network> <mask> <next-hop-ip>` | Static route via next-hop IP |
| `ip route <network> <mask> <exit-interface>` | Static route via exit interface |
| `ip route <network> <mask> <exit-interface> <next-hop-ip>` | Fully specified static route |
| `ip route 0.0.0.0 0.0.0.0 <next-hop>` | Default route (gateway of last resort) |

## Static Route Examples

```
! Route to 192.168.10.0/24 via next-hop
ip route 192.168.10.0 255.255.255.0 10.0.0.2

! Route via exit interface
ip route 192.168.10.0 255.255.255.0 GigabitEthernet0/1

! Fully specified route
ip route 192.168.10.0 255.255.255.0 GigabitEthernet0/1 10.0.0.2

! Default route
ip route 0.0.0.0 0.0.0.0 203.0.113.1
```

## Floating Static Routes

| Command | Description |
|---------|-------------|
| `ip route <network> <mask> <next-hop> <AD>` | Static route with administrative distance |

```
! Primary route (AD=1 default)
ip route 192.168.10.0 255.255.255.0 10.0.0.2

! Backup route with higher AD (floating static)
ip route 192.168.10.0 255.255.255.0 10.0.1.2 100
```

## IPv6 Static Routes

| Command | Description |
|---------|-------------|
| `ipv6 unicast-routing` | Enable IPv6 routing |
| `ipv6 route <prefix>/<length> <next-hop>` | IPv6 static route via next-hop |
| `ipv6 route <prefix>/<length> <exit-interface>` | IPv6 static route via interface |
| `ipv6 route ::/0 <next-hop>` | IPv6 default route |

```
! IPv6 static route examples
ipv6 route 2001:db8:1::/64 2001:db8:0::2
ipv6 route 2001:db8:1::/64 GigabitEthernet0/1
ipv6 route ::/0 2001:db8:0::1
```

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip route` | Display IPv4 routing table |
| `show ip route static` | Display only static routes |
| `show ip route <network>` | Display route to specific network |
| `show ipv6 route` | Display IPv6 routing table |
| `show ipv6 route static` | Display IPv6 static routes |
| `show running-config | include ip route` | Display configured static routes |

## Administrative Distance Reference

| Route Source | Default AD |
|--------------|-----------|
| Directly Connected | 0 |
| Static Route | 1 |
| EIGRP Summary | 5 |
| eBGP | 20 |
| EIGRP (internal) | 90 |
| IGRP | 100 |
| OSPF | 110 |
| IS-IS | 115 |
| RIP | 120 |
| EIGRP (external) | 170 |
| iBGP | 200 |
| Unknown | 255 (not installed) |

## Delete Static Route

| Command | Description |
|---------|-------------|
| `no ip route <network> <mask> <next-hop>` | Remove static route |
| `no ipv6 route <prefix>/<length> <next-hop>` | Remove IPv6 static route |
