# NAT Configuration Commands

## NAT Terminology

| Term | Description |
|------|-------------|
| **Inside Local** | Private IP of internal host |
| **Inside Global** | Public IP representing internal host |
| **Outside Local** | IP of external host as seen internally |
| **Outside Global** | Public IP of external host |

## Define Inside/Outside Interfaces

| Command | Description |
|---------|-------------|
| `ip nat inside` | Mark interface as inside (interface config) |
| `ip nat outside` | Mark interface as outside (interface config) |

## Static NAT

| Command | Description |
|---------|-------------|
| `ip nat inside source static <local-ip> <global-ip>` | One-to-one static mapping |

```
! Static NAT example
ip nat inside source static 192.168.1.10 203.0.113.10

interface g0/0
 ip address 192.168.1.1 255.255.255.0
 ip nat inside

interface g0/1
 ip address 203.0.113.1 255.255.255.0
 ip nat outside
```

## Dynamic NAT

| Command | Description |
|---------|-------------|
| `ip nat pool <name> <start-ip> <end-ip> netmask <mask>` | Create NAT pool |
| `ip nat pool <name> <start-ip> <end-ip> prefix-length <prefix>` | Create pool with prefix |
| `access-list <num> permit <network> <wildcard>` | Define inside hosts |
| `ip nat inside source list <acl> pool <name>` | Map ACL to pool |

```
! Dynamic NAT example
ip nat pool PUBLIC_POOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 pool PUBLIC_POOL
```

## PAT (Port Address Translation / NAT Overload)

| Command | Description |
|---------|-------------|
| `ip nat inside source list <acl> pool <name> overload` | PAT with pool |
| `ip nat inside source list <acl> interface <int> overload` | PAT with interface |

```
! PAT using interface IP
access-list 1 permit 192.168.1.0 0.0.0.255
ip nat inside source list 1 interface g0/1 overload

! PAT using pool
ip nat pool PAT_POOL 203.0.113.10 203.0.113.10 netmask 255.255.255.0
ip nat inside source list 1 pool PAT_POOL overload
```

## Static PAT (Port Forwarding)

| Command | Description |
|---------|-------------|
| `ip nat inside source static tcp <local-ip> <port> <global-ip> <port>` | Static TCP port mapping |
| `ip nat inside source static udp <local-ip> <port> <global-ip> <port>` | Static UDP port mapping |

```
! Port forwarding examples
ip nat inside source static tcp 192.168.1.100 80 203.0.113.1 80
ip nat inside source static tcp 192.168.1.100 443 203.0.113.1 443
ip nat inside source static tcp 192.168.1.200 22 203.0.113.1 2222
```

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip nat translations` | Display NAT translation table |
| `show ip nat translations verbose` | Display detailed translations |
| `show ip nat statistics` | Display NAT statistics |
| `show running-config | include ip nat` | Display NAT configuration |

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip nat translation *` | Clear all dynamic translations |
| `clear ip nat translation inside <ip> outside <ip>` | Clear specific translation |
| `clear ip nat statistics` | Clear NAT statistics |

## Debug Commands

| Command | Description |
|---------|-------------|
| `debug ip nat` | Debug NAT translations |
| `debug ip nat detailed` | Detailed NAT debugging |

## NAT Types Summary

| Type | Description | Use Case |
|------|-------------|----------|
| **Static NAT** | One-to-one mapping | Servers needing fixed public IP |
| **Dynamic NAT** | Pool of public IPs | When you have multiple public IPs |
| **PAT/Overload** | Many-to-one using ports | Most common, conserves IPs |

## Private IP Address Ranges (RFC 1918)

| Class | Range | CIDR |
|-------|-------|------|
| A | 10.0.0.0 - 10.255.255.255 | 10.0.0.0/8 |
| B | 172.16.0.0 - 172.31.255.255 | 172.16.0.0/12 |
| C | 192.168.0.0 - 192.168.255.255 | 192.168.0.0/16 |
