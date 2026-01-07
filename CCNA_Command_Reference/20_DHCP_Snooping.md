# DHCP Snooping Commands

## Enable DHCP Snooping

| Command | Description |
|---------|-------------|
| `ip dhcp snooping` | Enable DHCP snooping globally |
| `ip dhcp snooping vlan <vlan-list>` | Enable for specific VLANs |

## Configure Trusted Ports

| Command | Description |
|---------|-------------|
| `ip dhcp snooping trust` | Mark interface as trusted (interface config) |

**Note**: By default, all ports are untrusted.

## Rate Limiting

| Command | Description |
|---------|-------------|
| `ip dhcp snooping limit rate <pps>` | Set DHCP packet rate limit (interface config) |

## DHCP Snooping Configuration Example

```
! Enable globally
ip dhcp snooping
ip dhcp snooping vlan 10,20,30

! Configure uplink as trusted
interface g0/1
 ip dhcp snooping trust

! Configure access ports with rate limiting
interface range g0/2-24
 ip dhcp snooping limit rate 15
```

## Optional Settings

| Command | Description |
|---------|-------------|
| `ip dhcp snooping verify mac-address` | Verify source MAC matches DHCP |
| `no ip dhcp snooping information option` | Disable Option 82 insertion |

**Note**: Option 82 can cause issues if DHCP server doesn't support it. Disable if needed.

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip dhcp snooping` | Display DHCP snooping status |
| `show ip dhcp snooping binding` | Display DHCP snooping binding table |
| `show ip dhcp snooping database` | Display database agent status |
| `show ip dhcp snooping statistics` | Display DHCP snooping statistics |

## DHCP Snooping Binding Table

The binding table contains:
- MAC address
- IP address
- Lease time
- VLAN
- Interface

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip dhcp snooping binding` | Clear all bindings |
| `clear ip dhcp snooping binding <mac>` | Clear specific binding |
| `clear ip dhcp snooping statistics` | Clear statistics |

## Save Binding Database

| Command | Description |
|---------|-------------|
| `ip dhcp snooping database <url>` | Save bindings to external location |

```
ip dhcp snooping database flash:/dhcp_snooping.db
ip dhcp snooping database tftp://10.0.0.1/dhcp_snooping.db
```

---

# Dynamic ARP Inspection (DAI)

## Enable DAI

| Command | Description |
|---------|-------------|
| `ip arp inspection vlan <vlan-list>` | Enable DAI for VLANs |

## Configure Trusted Ports

| Command | Description |
|---------|-------------|
| `ip arp inspection trust` | Mark interface as trusted |

## Rate Limiting

| Command | Description |
|---------|-------------|
| `ip arp inspection limit rate <pps>` | Set ARP packet rate limit |
| `ip arp inspection limit rate <pps> burst interval <sec>` | Set burst interval |

## DAI Validation

| Command | Description |
|---------|-------------|
| `ip arp inspection validate src-mac` | Validate source MAC |
| `ip arp inspection validate dst-mac` | Validate destination MAC |
| `ip arp inspection validate ip` | Validate IP addresses |

```
ip arp inspection validate src-mac dst-mac ip
```

## ARP ACL (for non-DHCP hosts)

| Command | Description |
|---------|-------------|
| `arp access-list <name>` | Create ARP ACL |
| `permit ip host <ip> mac host <mac>` | Permit specific IP-MAC pair |
| `ip arp inspection filter <acl> vlan <vlan>` | Apply ARP ACL |

```
arp access-list STATIC_HOSTS
 permit ip host 10.0.0.100 mac host 0011.2233.4455

ip arp inspection filter STATIC_HOSTS vlan 10
```

## DAI Configuration Example

```
! Enable DAI (requires DHCP snooping first)
ip dhcp snooping
ip dhcp snooping vlan 10

ip arp inspection vlan 10

! Trust uplink
interface g0/1
 ip dhcp snooping trust
 ip arp inspection trust

! Rate limit on access ports
interface range g0/2-24
 ip arp inspection limit rate 15
```

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip arp inspection` | Display DAI status |
| `show ip arp inspection vlan <vlan>` | Display DAI for VLAN |
| `show ip arp inspection interfaces` | Display interface status |
| `show ip arp inspection statistics` | Display statistics |

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip arp inspection statistics` | Clear DAI statistics |
| `clear ip arp inspection log` | Clear DAI log |

## Errdisable Recovery

| Command | Description |
|---------|-------------|
| `errdisable recovery cause arp-inspection` | Enable auto-recovery |
| `errdisable recovery interval <seconds>` | Set recovery interval |
