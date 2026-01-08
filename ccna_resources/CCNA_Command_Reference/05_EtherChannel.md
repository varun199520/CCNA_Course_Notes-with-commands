# EtherChannel Commands

## EtherChannel Configuration Methods

### LACP (Link Aggregation Control Protocol) - IEEE 802.3ad

| Command | Description |
|---------|-------------|
| `channel-group <number> mode active` | Enable LACP, actively negotiate |
| `channel-group <number> mode passive` | Enable LACP, passively wait for negotiation |

### PAgP (Port Aggregation Protocol) - Cisco Proprietary

| Command | Description |
|---------|-------------|
| `channel-group <number> mode desirable` | Enable PAgP, actively negotiate |
| `channel-group <number> mode auto` | Enable PAgP, passively wait for negotiation |

### Static EtherChannel (No Protocol)

| Command | Description |
|---------|-------------|
| `channel-group <number> mode on` | Force EtherChannel without negotiation |

## EtherChannel Interface Configuration

| Command | Description |
|---------|-------------|
| `interface port-channel <number>` | Enter port-channel interface config |
| `switchport mode trunk` | Configure as trunk (applied to port-channel) |
| `switchport mode access` | Configure as access port |
| `switchport trunk allowed vlan <list>` | Set allowed VLANs on trunk |

## Load Balancing

| Command | Description |
|---------|-------------|
| `port-channel load-balance <method>` | Set load-balancing method (global config) |

### Load Balance Methods

| Method | Description |
|--------|-------------|
| `src-mac` | Source MAC address |
| `dst-mac` | Destination MAC address |
| `src-dst-mac` | Source and destination MAC |
| `src-ip` | Source IP address |
| `dst-ip` | Destination IP address |
| `src-dst-ip` | Source and destination IP |
| `src-port` | Source TCP/UDP port |
| `dst-port` | Destination TCP/UDP port |
| `src-dst-port` | Source and destination port |

## Layer 3 EtherChannel

| Command | Description |
|---------|-------------|
| `no switchport` | Convert to routed port (on member interfaces) |
| `channel-group <number> mode active` | Add to channel group |
| `interface port-channel <number>` | Enter port-channel interface |
| `ip address <ip> <mask>` | Assign IP to port-channel |

## Show Commands

| Command | Description |
|---------|-------------|
| `show etherchannel summary` | Display EtherChannel summary |
| `show etherchannel port-channel` | Display port-channel info |
| `show etherchannel load-balance` | Display load-balancing method |
| `show etherchannel detail` | Display detailed EtherChannel info |
| `show interfaces port-channel <number>` | Display port-channel interface info |
| `show lacp neighbor` | Display LACP neighbor info |
| `show lacp internal` | Display LACP internal info |
| `show pagp neighbor` | Display PAgP neighbor info |
| `show pagp internal` | Display PAgP internal info |

## EtherChannel Configuration Example

```
! Configure member interfaces
interface range g0/1-2
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
 channel-group 1 mode active

! Configure port-channel interface
interface port-channel 1
 switchport mode trunk
 switchport trunk allowed vlan 10,20,30
```

## EtherChannel Requirements

All member interfaces must have matching:
- Speed and duplex
- Switchport mode (access/trunk)
- Access VLAN (if access mode)
- Allowed VLANs and native VLAN (if trunk mode)
- STP settings

## Troubleshooting Commands

| Command | Description |
|---------|-------------|
| `show etherchannel summary` | Check channel status (flags: P=bundled, I=stand-alone) |
| `show interfaces status` | Verify interface status |
| `show running-config interface <int>` | Verify interface configuration |
