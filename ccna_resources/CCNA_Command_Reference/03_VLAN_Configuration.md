# VLAN Configuration Commands

## Creating and Managing VLANs

| Command | Description |
|---------|-------------|
| `vlan <vlan-id>` | Create VLAN and enter VLAN config mode |
| `name <vlan-name>` | Assign name to VLAN |
| `no vlan <vlan-id>` | Delete a VLAN |
| `vlan <range>` | Create multiple VLANs (e.g., `vlan 10,20,30` or `vlan 10-30`) |

## Access Port Configuration

| Command | Description |
|---------|-------------|
| `switchport mode access` | Set port as access port |
| `switchport access vlan <vlan-id>` | Assign port to VLAN |
| `switchport voice vlan <vlan-id>` | Assign voice VLAN to port |

## Trunk Port Configuration

| Command | Description |
|---------|-------------|
| `switchport mode trunk` | Set port as trunk port |
| `switchport trunk encapsulation dot1q` | Set trunk encapsulation to 802.1Q |
| `switchport trunk native vlan <vlan-id>` | Set native VLAN for trunk |
| `switchport trunk allowed vlan <vlan-list>` | Specify allowed VLANs on trunk |
| `switchport trunk allowed vlan add <vlan-id>` | Add VLAN to allowed list |
| `switchport trunk allowed vlan remove <vlan-id>` | Remove VLAN from allowed list |
| `switchport trunk allowed vlan all` | Allow all VLANs on trunk |
| `switchport trunk allowed vlan except <vlan-id>` | Allow all VLANs except specified |
| `switchport trunk allowed vlan none` | Block all VLANs on trunk |

## Dynamic Trunking Protocol (DTP)

| Command | Description |
|---------|-------------|
| `switchport mode dynamic auto` | Port becomes trunk if neighbor is trunk/desirable |
| `switchport mode dynamic desirable` | Actively negotiates to become trunk |
| `switchport nonegotiate` | Disable DTP negotiation |

## Show Commands

| Command | Description |
|---------|-------------|
| `show vlan` | Display all VLANs and port assignments |
| `show vlan brief` | Display VLAN summary |
| `show vlan id <vlan-id>` | Display specific VLAN details |
| `show interfaces trunk` | Display trunk port information |
| `show interfaces switchport` | Display switchport configuration |
| `show interfaces <int> switchport` | Display specific port switchport info |
| `show dtp interface <int>` | Display DTP status on interface |

## VTP (VLAN Trunking Protocol) Commands

| Command | Description |
|---------|-------------|
| `vtp mode <server|client|transparent|off>` | Set VTP mode |
| `vtp domain <name>` | Set VTP domain name |
| `vtp password <password>` | Set VTP password |
| `vtp version <1|2|3>` | Set VTP version |
| `vtp pruning` | Enable VTP pruning |
| `show vtp status` | Display VTP configuration |
| `show vtp password` | Display VTP password |

## Inter-VLAN Routing (Router-on-a-Stick)

```
! On Router
interface g0/0
 no shutdown

interface g0/0.10
 encapsulation dot1q 10
 ip address 192.168.10.1 255.255.255.0

interface g0/0.20
 encapsulation dot1q 20
 ip address 192.168.20.1 255.255.255.0
```

## Layer 3 Switch Inter-VLAN Routing

| Command | Description |
|---------|-------------|
| `ip routing` | Enable Layer 3 routing on switch |
| `interface vlan <vlan-id>` | Create SVI for VLAN |
| `ip address <ip> <mask>` | Assign IP to SVI |
| `no switchport` | Convert switch port to routed port |
