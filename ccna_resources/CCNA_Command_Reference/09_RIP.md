# RIP Configuration Commands

## Enable RIP

| Command | Description |
|---------|-------------|
| `router rip` | Enter RIP router configuration mode |
| `version 2` | Enable RIP version 2 |
| `network <classful-network>` | Enable RIP on network |
| `no auto-summary` | Disable automatic summarization |

## Basic Configuration Example

```
router rip
 version 2
 network 10.0.0.0
 network 192.168.1.0
 no auto-summary
```

## RIP Settings

| Command | Description |
|---------|-------------|
| `passive-interface <interface>` | Stop sending RIP updates on interface |
| `passive-interface default` | Make all interfaces passive |
| `no passive-interface <interface>` | Enable RIP on specific interface |
| `default-information originate` | Advertise default route |

## RIP Timers

| Command | Description |
|---------|-------------|
| `timers basic <update> <invalid> <holddown> <flush>` | Set RIP timers |

Default Timers:
- **Update**: 30 seconds
- **Invalid**: 180 seconds
- **Holddown**: 180 seconds
- **Flush**: 240 seconds

## RIP Authentication (v2)

| Command | Description |
|---------|-------------|
| `key chain <name>` | Create key chain |
| `key <number>` | Create key in key chain |
| `key-string <password>` | Set key password |
| `ip rip authentication mode md5` | Enable MD5 auth on interface |
| `ip rip authentication key-chain <keychain>` | Apply key chain to interface |

## RIPng (IPv6)

| Command | Description |
|---------|-------------|
| `ipv6 router rip <name>` | Enter RIPng config mode |
| `ipv6 rip <name> enable` | Enable RIPng on interface |

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip rip database` | Display RIP database |
| `show ip route rip` | Display RIP routes |
| `show ip protocols` | Display routing protocol info |

## RIP Characteristics

| Feature | Value |
|---------|-------|
| **Type** | Distance Vector |
| **Metric** | Hop Count |
| **Max Hops** | 15 (16 = unreachable) |
| **AD** | 120 |
| **Update Method** | Broadcast (v1) / Multicast 224.0.0.9 (v2) |

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip route *` | Clear routing table |
