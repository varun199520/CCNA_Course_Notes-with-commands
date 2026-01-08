# Spanning Tree Protocol (STP) Commands

## STP Mode Configuration

| Command | Description |
|---------|-------------|
| `spanning-tree mode pvst` | Enable Per-VLAN Spanning Tree (Cisco default) |
| `spanning-tree mode rapid-pvst` | Enable Rapid PVST+ |
| `spanning-tree mode mst` | Enable Multiple Spanning Tree |
| `no spanning-tree vlan <vlan-id>` | Disable STP on specific VLAN |

## Root Bridge Configuration

| Command | Description |
|---------|-------------|
| `spanning-tree vlan <vlan-id> root primary` | Make switch root bridge (priority 24576 or 4096 less than current root) |
| `spanning-tree vlan <vlan-id> root secondary` | Make switch secondary root (priority 28672) |
| `spanning-tree vlan <vlan-id> priority <value>` | Set priority manually (increments of 4096: 0-61440) |

## Port Cost Configuration

| Command | Description |
|---------|-------------|
| `spanning-tree vlan <vlan-id> cost <value>` | Set port cost for specific VLAN |
| `spanning-tree cost <value>` | Set port cost for all VLANs |

## Port Priority Configuration

| Command | Description |
|---------|-------------|
| `spanning-tree vlan <vlan-id> port-priority <value>` | Set port priority (0-240, increments of 16) |
| `spanning-tree port-priority <value>` | Set port priority for all VLANs |

## PortFast Configuration

| Command | Description |
|---------|-------------|
| `spanning-tree portfast` | Enable PortFast on access port |
| `spanning-tree portfast trunk` | Enable PortFast on trunk port |
| `spanning-tree portfast default` | Enable PortFast globally on all access ports |
| `spanning-tree portfast disable` | Disable PortFast on interface |

## BPDU Guard

| Command | Description |
|---------|-------------|
| `spanning-tree bpduguard enable` | Enable BPDU Guard on interface |
| `spanning-tree bpduguard disable` | Disable BPDU Guard on interface |
| `spanning-tree portfast bpduguard default` | Enable BPDU Guard globally on PortFast ports |

## BPDU Filter

| Command | Description |
|---------|-------------|
| `spanning-tree bpdufilter enable` | Enable BPDU Filter on interface |
| `spanning-tree portfast bpdufilter default` | Enable BPDU Filter globally |

## Root Guard

| Command | Description |
|---------|-------------|
| `spanning-tree guard root` | Enable Root Guard on interface |

## Loop Guard

| Command | Description |
|---------|-------------|
| `spanning-tree guard loop` | Enable Loop Guard on interface |
| `spanning-tree loopguard default` | Enable Loop Guard globally |

## STP Timers

| Command | Description |
|---------|-------------|
| `spanning-tree vlan <vlan-id> hello-time <seconds>` | Set hello time (1-10 sec, default 2) |
| `spanning-tree vlan <vlan-id> forward-time <seconds>` | Set forward delay (4-30 sec, default 15) |
| `spanning-tree vlan <vlan-id> max-age <seconds>` | Set max age (6-40 sec, default 20) |

## Show Commands

| Command | Description |
|---------|-------------|
| `show spanning-tree` | Display STP info for all VLANs |
| `show spanning-tree vlan <vlan-id>` | Display STP info for specific VLAN |
| `show spanning-tree summary` | Display STP summary |
| `show spanning-tree root` | Display root bridge info |
| `show spanning-tree bridge` | Display local bridge info |
| `show spanning-tree interface <int>` | Display STP info for interface |
| `show spanning-tree interface <int> detail` | Display detailed STP info |
| `show spanning-tree blockedports` | Display blocked ports |
| `show spanning-tree inconsistentports` | Display inconsistent ports |

## STP Port States

| State | Description |
|-------|-------------|
| **Disabled** | Port is administratively down |
| **Blocking** | Receives BPDUs only, does not forward frames |
| **Listening** | Sends/receives BPDUs, does not forward frames |
| **Learning** | Learns MAC addresses, does not forward frames |
| **Forwarding** | Normal operation, forwards frames |

## STP Cost Reference

| Speed | IEEE Cost | Cisco Legacy Cost |
|-------|-----------|-------------------|
| 10 Mbps | 100 | 100 |
| 100 Mbps | 19 | 19 |
| 1 Gbps | 4 | 4 |
| 10 Gbps | 2 | 2 |
