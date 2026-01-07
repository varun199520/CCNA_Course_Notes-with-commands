# Port Security Commands

## Enable Port Security

| Command | Description |
|---------|-------------|
| `switchport mode access` | Set port as access (required first) |
| `switchport port-security` | Enable port security |

## Port Security Configuration

| Command | Description |
|---------|-------------|
| `switchport port-security maximum <num>` | Set max MAC addresses (default 1) |
| `switchport port-security mac-address <mac>` | Statically configure allowed MAC |
| `switchport port-security mac-address sticky` | Enable sticky learning |
| `switchport port-security violation <action>` | Set violation action |
| `switchport port-security aging time <min>` | Set aging time |
| `switchport port-security aging type <type>` | Set aging type |

## Violation Modes

| Mode | Description | Traffic | Log | Err-Disable |
|------|-------------|---------|-----|-------------|
| `shutdown` | Disable port (default) | Dropped | Yes | Yes |
| `restrict` | Drop traffic, log | Dropped | Yes | No |
| `protect` | Drop traffic silently | Dropped | No | No |

## Port Security Configuration Example

```
interface g0/1
 switchport mode access
 switchport access vlan 10
 switchport port-security
 switchport port-security maximum 2
 switchport port-security mac-address sticky
 switchport port-security violation restrict
```

## Static MAC Address Configuration

```
interface g0/1
 switchport mode access
 switchport port-security
 switchport port-security mac-address 0011.2233.4455
```

## Aging Configuration

| Command | Description |
|---------|-------------|
| `switchport port-security aging time <minutes>` | Set aging time |
| `switchport port-security aging type absolute` | Age from learning time |
| `switchport port-security aging type inactivity` | Age from last use |
| `switchport port-security aging static` | Enable aging for static MACs |

## Show Commands

| Command | Description |
|---------|-------------|
| `show port-security` | Display summary of all ports |
| `show port-security interface <int>` | Display port security for interface |
| `show port-security address` | Display secure MAC addresses |
| `show interfaces status` | Display interface status |

## Show Port-Security Interface Output

```
Port Security              : Enabled
Port Status                : Secure-up
Violation Mode             : Restrict
Aging Time                 : 0 mins
Aging Type                 : Absolute
SecureStatic Address Aging : Disabled
Maximum MAC Addresses      : 2
Total MAC Addresses        : 1
Configured MAC Addresses   : 0
Sticky MAC Addresses       : 1
Last Source Address:Vlan   : 0011.2233.4455:10
Security Violation Count   : 0
```

## Recovery from Err-Disabled State

### Manual Recovery

```
interface g0/1
 shutdown
 no shutdown
```

### Automatic Recovery (Errdisable Recovery)

| Command | Description |
|---------|-------------|
| `errdisable recovery cause psecure-violation` | Enable auto-recovery |
| `errdisable recovery interval <seconds>` | Set recovery interval |

```
errdisable recovery cause psecure-violation
errdisable recovery interval 300
```

## Show Errdisable Status

| Command | Description |
|---------|-------------|
| `show errdisable recovery` | Display errdisable recovery settings |
| `show interfaces status err-disabled` | Display err-disabled interfaces |

## Clear Port Security

| Command | Description |
|---------|-------------|
| `clear port-security all` | Clear all secure addresses |
| `clear port-security configured` | Clear configured addresses |
| `clear port-security dynamic` | Clear dynamically learned |
| `clear port-security sticky` | Clear sticky addresses |
| `clear port-security sticky interface <int>` | Clear sticky on interface |

## Best Practices

1. Use on access ports only (not trunks)
2. Set appropriate maximum based on expected devices
3. Use sticky learning in dynamic environments
4. Use restrict mode to avoid accidental lockouts
5. Configure errdisable recovery for shutdown mode
6. Document static MAC address assignments
