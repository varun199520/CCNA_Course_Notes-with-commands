# CDP and LLDP Commands

## CDP (Cisco Discovery Protocol)

### CDP Global Configuration

| Command | Description |
|---------|-------------|
| `cdp run` | Enable CDP globally (default) |
| `no cdp run` | Disable CDP globally |
| `cdp timer <seconds>` | Set CDP advertisement interval (default 60) |
| `cdp holdtime <seconds>` | Set CDP holdtime (default 180) |
| `cdp advertise-v2` | Enable CDPv2 (default) |

### CDP Interface Configuration

| Command | Description |
|---------|-------------|
| `cdp enable` | Enable CDP on interface (default) |
| `no cdp enable` | Disable CDP on interface |

### CDP Show Commands

| Command | Description |
|---------|-------------|
| `show cdp` | Display CDP global settings |
| `show cdp neighbors` | Display CDP neighbor summary |
| `show cdp neighbors detail` | Display detailed neighbor info |
| `show cdp entry <name>` | Display specific neighbor |
| `show cdp interface` | Display CDP-enabled interfaces |
| `show cdp traffic` | Display CDP packet statistics |

### CDP Neighbor Output Fields

| Field | Description |
|-------|-------------|
| Device ID | Neighbor hostname |
| Local Intrfce | Local interface connected to neighbor |
| Holdtme | Time until entry expires |
| Capability | Device capabilities (R=Router, S=Switch, etc.) |
| Platform | Device model |
| Port ID | Neighbor's interface |

---

## LLDP (Link Layer Discovery Protocol)

### LLDP Global Configuration

| Command | Description |
|---------|-------------|
| `lldp run` | Enable LLDP globally |
| `no lldp run` | Disable LLDP globally |
| `lldp timer <seconds>` | Set LLDP advertisement interval (default 30) |
| `lldp holdtime <seconds>` | Set LLDP holdtime (default 120) |
| `lldp reinit <seconds>` | Set reinitialization delay (default 2) |

### LLDP Interface Configuration

| Command | Description |
|---------|-------------|
| `lldp transmit` | Enable LLDP transmit on interface |
| `lldp receive` | Enable LLDP receive on interface |
| `no lldp transmit` | Disable LLDP transmit |
| `no lldp receive` | Disable LLDP receive |

### LLDP Show Commands

| Command | Description |
|---------|-------------|
| `show lldp` | Display LLDP global settings |
| `show lldp neighbors` | Display LLDP neighbor summary |
| `show lldp neighbors detail` | Display detailed neighbor info |
| `show lldp entry <name>` | Display specific neighbor |
| `show lldp interface` | Display LLDP-enabled interfaces |
| `show lldp traffic` | Display LLDP packet statistics |

---

## CDP vs LLDP Comparison

| Feature | CDP | LLDP |
|---------|-----|------|
| **Standard** | Cisco Proprietary | IEEE 802.1AB |
| **Default State** | Enabled | Disabled |
| **Timer** | 60 seconds | 30 seconds |
| **Holdtime** | 180 seconds | 120 seconds |
| **Multicast Address** | 01:00:0C:CC:CC:CC | 01:80:C2:00:00:0E |
| **Layer** | Layer 2 | Layer 2 |

## Capability Codes

| Code | Description |
|------|-------------|
| R | Router |
| T | Trans Bridge |
| B | Source Route Bridge |
| S | Switch |
| H | Host |
| I | IGMP |
| r | Repeater |
| P | Phone |

## Security Considerations

- Disable CDP/LLDP on external-facing interfaces
- Disable on interfaces connected to untrusted networks
- Information disclosed can be used for reconnaissance

```
! Disable CDP on specific interface
interface g0/0
 no cdp enable

! Disable LLDP on specific interface  
interface g0/0
 no lldp transmit
 no lldp receive
```

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear cdp counters` | Clear CDP statistics |
| `clear cdp table` | Clear CDP neighbor table |
| `clear lldp counters` | Clear LLDP statistics |
| `clear lldp table` | Clear LLDP neighbor table |
