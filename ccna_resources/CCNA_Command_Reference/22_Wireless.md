# Wireless Configuration Commands

## Wireless LAN Controller (WLC) Concepts

### Wireless Standards

| Standard | Name | Frequency | Max Speed |
|----------|------|-----------|-----------|
| 802.11a | Wi-Fi 2 | 5 GHz | 54 Mbps |
| 802.11b | Wi-Fi 1 | 2.4 GHz | 11 Mbps |
| 802.11g | Wi-Fi 3 | 2.4 GHz | 54 Mbps |
| 802.11n | Wi-Fi 4 | 2.4/5 GHz | 600 Mbps |
| 802.11ac | Wi-Fi 5 | 5 GHz | 6.9 Gbps |
| 802.11ax | Wi-Fi 6 | 2.4/5/6 GHz | 9.6 Gbps |

### 2.4 GHz Non-Overlapping Channels

| Region | Channels |
|--------|----------|
| Most Countries | 1, 6, 11 |
| Europe | 1, 5, 9, 13 |

---

## Autonomous AP Configuration

### Basic AP Configuration

| Command | Description |
|---------|-------------|
| `dot11 ssid <name>` | Create SSID |
| `authentication open` | Set open authentication |
| `authentication key-management wpa version 2` | Enable WPA2 |
| `wpa-psk ascii <passphrase>` | Set WPA2 pre-shared key |
| `guest-mode` | Broadcast SSID |

### Interface Configuration

| Command | Description |
|---------|-------------|
| `interface dot11radio 0` | Enter 2.4 GHz radio config |
| `interface dot11radio 1` | Enter 5 GHz radio config |
| `ssid <name>` | Associate SSID with radio |
| `channel <number>` | Set radio channel |
| `power local <mW>` | Set transmit power |
| `no shutdown` | Enable radio |

### Autonomous AP Example

```
dot11 ssid CORPORATE
 authentication open
 authentication key-management wpa version 2
 wpa-psk ascii MySecurePassword123
 guest-mode

interface dot11radio 0
 ssid CORPORATE
 channel 6
 no shutdown

interface dot11radio 1
 ssid CORPORATE
 channel 36
 no shutdown
```

---

## Lightweight AP (CAPWAP)

### CAPWAP Ports

| Port | Protocol | Description |
|------|----------|-------------|
| UDP 5246 | CAPWAP Control | Control messages (encrypted) |
| UDP 5247 | CAPWAP Data | Data traffic |

### WLC Discovery Methods

1. **DHCP Option 43** - WLC IP in DHCP response
2. **DNS** - cisco-capwap-controller.domain
3. **Broadcast** - Local subnet discovery
4. **Previously known** - Stored WLC addresses

---

## WLC Configuration (GUI-based)

### Common WLC Settings

| Setting | Description |
|---------|-------------|
| **WLAN** | Create/manage wireless networks |
| **Interface** | Layer 3 interfaces for VLANs |
| **Security** | Authentication and encryption |
| **RF Profiles** | Radio frequency settings |

### WLC WLAN Security Options

| Security | Description |
|----------|-------------|
| Open | No authentication |
| WPA2 Personal | Pre-shared key (PSK) |
| WPA2 Enterprise | 802.1X/RADIUS |
| WPA3 | Latest security standard |

---

## 802.1X Authentication

### Switch Configuration for 802.1X

| Command | Description |
|---------|-------------|
| `aaa new-model` | Enable AAA |
| `aaa authentication dot1x default group radius` | Use RADIUS for 802.1X |
| `dot1x system-auth-control` | Enable 802.1X globally |
| `dot1x pae authenticator` | Set port as authenticator |
| `authentication port-control auto` | Enable 802.1X on port |

### 802.1X Configuration Example

```
aaa new-model
aaa authentication dot1x default group radius
aaa authorization network default group radius
dot1x system-auth-control

radius server RADIUS1
 address ipv4 10.0.0.100 auth-port 1812 acct-port 1813
 key RadiusSecret123

interface g0/1
 switchport mode access
 switchport access vlan 10
 authentication port-control auto
 dot1x pae authenticator
```

---

## Wireless Show Commands

| Command | Description |
|---------|-------------|
| `show dot11 associations` | Display wireless clients |
| `show dot11 bssid` | Display BSSID info |
| `show interfaces dot11radio 0` | Display radio interface |
| `show controllers dot11radio 0` | Display radio details |

---

## Wireless Terminology

| Term | Description |
|------|-------------|
| **SSID** | Service Set Identifier (network name) |
| **BSSID** | Basic Service Set ID (AP MAC address) |
| **BSS** | Basic Service Set (single AP) |
| **ESS** | Extended Service Set (multiple APs) |
| **CAPWAP** | Control and Provisioning of Wireless APs |
| **WLC** | Wireless LAN Controller |
| **LAP** | Lightweight Access Point |

## Wireless Security Protocols

| Protocol | Encryption | Authentication |
|----------|------------|----------------|
| WEP | RC4 (weak) | Open/Shared Key |
| WPA | TKIP | PSK or 802.1X |
| WPA2 | AES-CCMP | PSK or 802.1X |
| WPA3 | AES-GCMP | SAE or 802.1X |
