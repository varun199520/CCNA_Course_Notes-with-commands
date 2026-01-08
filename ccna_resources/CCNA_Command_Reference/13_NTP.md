# NTP Configuration Commands

## NTP Client Configuration

| Command | Description |
|---------|-------------|
| `ntp server <ip-address>` | Configure NTP server |
| `ntp server <ip-address> prefer` | Configure preferred NTP server |
| `ntp server <ip-address> key <key-id>` | Configure NTP server with authentication |

## NTP Server Configuration

| Command | Description |
|---------|-------------|
| `ntp master <stratum>` | Configure device as NTP master |
| `ntp source <interface>` | Set source interface for NTP |

## NTP Peer Configuration

| Command | Description |
|---------|-------------|
| `ntp peer <ip-address>` | Configure NTP peer (symmetric active) |

## NTP Authentication

| Command | Description |
|---------|-------------|
| `ntp authenticate` | Enable NTP authentication |
| `ntp authentication-key <key-id> md5 <password>` | Create authentication key |
| `ntp trusted-key <key-id>` | Specify trusted key |
| `ntp server <ip> key <key-id>` | Use key with server |

## NTP Authentication Example

```
ntp authenticate
ntp authentication-key 1 md5 MySecretKey
ntp trusted-key 1
ntp server 10.0.0.1 key 1
```

## NTP Access Control

| Command | Description |
|---------|-------------|
| `ntp access-group peer <acl>` | Allow full access (sync and provide) |
| `ntp access-group serve <acl>` | Allow sync requests only |
| `ntp access-group serve-only <acl>` | Allow sync but not control queries |
| `ntp access-group query-only <acl>` | Allow control queries only |

## Show Commands

| Command | Description |
|---------|-------------|
| `show clock` | Display current time |
| `show clock detail` | Display time with source info |
| `show ntp status` | Display NTP synchronization status |
| `show ntp associations` | Display NTP server associations |
| `show ntp associations detail` | Display detailed associations |

## Clock Configuration

| Command | Description |
|---------|-------------|
| `clock timezone <name> <offset>` | Set timezone |
| `clock summer-time <name> recurring` | Enable daylight saving |
| `clock set <hh:mm:ss> <day> <month> <year>` | Manually set clock |
| `clock calendar-valid` | Mark hardware clock as valid |
| `ntp update-calendar` | Update hardware clock with NTP |

## Clock Examples

```
! Set timezone
clock timezone EST -5
clock summer-time EDT recurring

! Set clock manually
clock set 14:30:00 5 January 2026
```

## NTP Stratum Levels

| Stratum | Description |
|---------|-------------|
| 0 | Atomic clock, GPS (reference clock) |
| 1 | Directly connected to stratum 0 |
| 2 | Syncs from stratum 1 |
| 3-15 | Each level syncs from previous |
| 16 | Unsynchronized |

## Loopback for NTP

```
! Best practice: use loopback as NTP source
interface loopback 0
 ip address 1.1.1.1 255.255.255.255

ntp source loopback 0
ntp master 3
```

## Debug Commands

| Command | Description |
|---------|-------------|
| `debug ntp events` | Debug NTP events |
| `debug ntp packets` | Debug NTP packets |
