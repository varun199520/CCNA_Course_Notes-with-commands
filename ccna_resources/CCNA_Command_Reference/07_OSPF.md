# OSPF Configuration Commands

## Enable OSPF

| Command | Description |
|---------|-------------|
| `router ospf <process-id>` | Enter OSPF router configuration mode |
| `router-id <id>` | Set OSPF router ID (recommended: x.x.x.x format) |

## Network Statements

| Command | Description |
|---------|-------------|
| `network <ip> <wildcard> area <area-id>` | Enable OSPF on matching interfaces |
| `network 0.0.0.0 255.255.255.255 area 0` | Enable OSPF on all interfaces |

## Interface-Level OSPF Configuration

| Command | Description |
|---------|-------------|
| `ip ospf <process-id> area <area-id>` | Enable OSPF directly on interface |
| `ip ospf cost <value>` | Set OSPF cost on interface |
| `ip ospf priority <0-255>` | Set DR/BDR election priority (0 = never DR) |
| `ip ospf hello-interval <seconds>` | Set hello interval (default 10) |
| `ip ospf dead-interval <seconds>` | Set dead interval (default 40) |
| `ip ospf network point-to-point` | Set network type to point-to-point |

## Passive Interface

| Command | Description |
|---------|-------------|
| `passive-interface <interface>` | Stop sending OSPF hellos on interface |
| `passive-interface default` | Make all interfaces passive by default |
| `no passive-interface <interface>` | Enable OSPF on specific interface |

## OSPF Cost and Reference Bandwidth

| Command | Description |
|---------|-------------|
| `auto-cost reference-bandwidth <mbps>` | Set reference bandwidth (default 100 Mbps) |
| `ip ospf cost <value>` | Manually set interface cost |

## Default Route Advertisement

| Command | Description |
|---------|-------------|
| `default-information originate` | Advertise default route (if one exists) |
| `default-information originate always` | Always advertise default route |

## OSPF Authentication

| Command | Description |
|---------|-------------|
| `ip ospf authentication` | Enable plaintext authentication |
| `ip ospf authentication message-digest` | Enable MD5 authentication |
| `ip ospf authentication-key <password>` | Set plaintext password |
| `ip ospf message-digest-key <id> md5 <password>` | Set MD5 key |
| `area <area-id> authentication` | Enable area-wide authentication |
| `area <area-id> authentication message-digest` | Enable area-wide MD5 auth |

## OSPF Timers

| Command | Description |
|---------|-------------|
| `timers throttle spf <start> <hold> <max>` | Set SPF calculation timers |
| `ip ospf hello-interval <seconds>` | Set hello interval |
| `ip ospf dead-interval <seconds>` | Set dead interval |

## OSPF Area Types

| Command | Description |
|---------|-------------|
| `area <area-id> stub` | Configure stub area |
| `area <area-id> stub no-summary` | Configure totally stubby area |
| `area <area-id> nssa` | Configure NSSA |
| `area <area-id> nssa no-summary` | Configure totally NSSA |

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip ospf` | Display OSPF process info |
| `show ip ospf neighbor` | Display OSPF neighbors |
| `show ip ospf neighbor detail` | Display detailed neighbor info |
| `show ip ospf interface` | Display OSPF interface info |
| `show ip ospf interface brief` | Display OSPF interface summary |
| `show ip ospf database` | Display LSDB |
| `show ip route ospf` | Display OSPF routes |
| `show ip protocols` | Display routing protocol info |

## OSPFv3 (IPv6)

| Command | Description |
|---------|-------------|
| `ipv6 router ospf <process-id>` | Enter OSPFv3 config mode |
| `router-id <id>` | Set router ID (required) |
| `ipv6 ospf <process-id> area <area-id>` | Enable OSPFv3 on interface |

## OSPF Network Types

| Type | Hello | Dead | DR/BDR |
|------|-------|------|--------|
| Broadcast | 10s | 40s | Yes |
| Point-to-Point | 10s | 40s | No |
| Non-Broadcast | 30s | 120s | Yes |
| Point-to-Multipoint | 30s | 120s | No |

## OSPF Neighbor States

1. **Down** - No hellos received
2. **Init** - Hello received, but no 2-way
3. **2-Way** - Bidirectional communication
4. **ExStart** - Master/slave negotiation
5. **Exchange** - DBD exchange
6. **Loading** - LSR/LSU exchange
7. **Full** - Fully adjacent

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip ospf process` | Reset OSPF process |
| `clear ip ospf counters` | Clear OSPF counters |
