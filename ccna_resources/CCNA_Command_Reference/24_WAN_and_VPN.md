# WAN and VPN Commands

## WAN Connection Types

| Type | Description |
|------|-------------|
| Leased Line | Dedicated point-to-point |
| MPLS | Label-switched provider network |
| Metro Ethernet | Ethernet-based WAN |
| Internet VPN | Encrypted tunnel over Internet |
| DSL | Digital Subscriber Line |
| Cable | DOCSIS over coax |
| Cellular | 4G/5G wireless |

---

## Serial Interface Configuration

| Command | Description |
|---------|-------------|
| `interface serial <number>` | Enter serial interface config |
| `ip address <ip> <mask>` | Assign IP address |
| `clock rate <bps>` | Set clock rate (DCE side only) |
| `bandwidth <kbps>` | Set bandwidth for routing metrics |
| `encapsulation hdlc` | Set HDLC encapsulation (default) |
| `encapsulation ppp` | Set PPP encapsulation |
| `no shutdown` | Enable interface |

### Serial Interface Example

```
interface serial 0/0/0
 ip address 10.0.0.1 255.255.255.252
 clock rate 128000
 no shutdown
```

---

## PPP Configuration

| Command | Description |
|---------|-------------|
| `encapsulation ppp` | Enable PPP on interface |
| `ppp authentication chap` | Enable CHAP authentication |
| `ppp authentication pap` | Enable PAP authentication |
| `ppp chap hostname <name>` | Set CHAP hostname |
| `ppp chap password <password>` | Set CHAP password |

### PPP CHAP Example

```
! Router 1
username R2 password SecretPass
interface serial 0/0/0
 encapsulation ppp
 ppp authentication chap

! Router 2
username R1 password SecretPass
interface serial 0/0/0
 encapsulation ppp
 ppp authentication chap
```

---

## GRE Tunnel Configuration

| Command | Description |
|---------|-------------|
| `interface tunnel <number>` | Create tunnel interface |
| `tunnel source <interface/ip>` | Set tunnel source |
| `tunnel destination <ip>` | Set tunnel destination |
| `tunnel mode gre ip` | Set GRE mode (default) |
| `ip address <ip> <mask>` | Assign tunnel IP |

### GRE Tunnel Example

```
! Router 1
interface tunnel 0
 ip address 10.0.0.1 255.255.255.0
 tunnel source g0/0
 tunnel destination 203.0.113.2

! Router 2
interface tunnel 0
 ip address 10.0.0.2 255.255.255.0
 tunnel source g0/0
 tunnel destination 198.51.100.1
```

---

## IPSec VPN Configuration

### ISAKMP Policy (Phase 1)

| Command | Description |
|---------|-------------|
| `crypto isakmp policy <priority>` | Create ISAKMP policy |
| `encryption aes 256` | Set encryption algorithm |
| `hash sha256` | Set hash algorithm |
| `authentication pre-share` | Set authentication method |
| `group 14` | Set DH group |
| `lifetime <seconds>` | Set SA lifetime |

### Pre-Shared Key

| Command | Description |
|---------|-------------|
| `crypto isakmp key <key> address <peer-ip>` | Set pre-shared key |

### IPSec Transform Set (Phase 2)

| Command | Description |
|---------|-------------|
| `crypto ipsec transform-set <name> <transforms>` | Create transform set |
| `mode tunnel` | Set tunnel mode (default) |
| `mode transport` | Set transport mode |

### Crypto ACL

| Command | Description |
|---------|-------------|
| `access-list <num> permit ip <src> <wild> <dst> <wild>` | Define interesting traffic |

### Crypto Map

| Command | Description |
|---------|-------------|
| `crypto map <name> <seq> ipsec-isakmp` | Create crypto map entry |
| `set peer <ip>` | Set VPN peer |
| `set transform-set <name>` | Apply transform set |
| `match address <acl>` | Match traffic ACL |

### Apply Crypto Map

| Command | Description |
|---------|-------------|
| `crypto map <name>` | Apply to interface |

### Site-to-Site VPN Example

```
! Phase 1
crypto isakmp policy 10
 encryption aes 256
 hash sha256
 authentication pre-share
 group 14
 lifetime 86400

crypto isakmp key MySecretKey address 203.0.113.2

! Phase 2
crypto ipsec transform-set MYSET esp-aes 256 esp-sha256-hmac
 mode tunnel

! Crypto ACL
access-list 100 permit ip 192.168.1.0 0.0.0.255 192.168.2.0 0.0.0.255

! Crypto Map
crypto map MYMAP 10 ipsec-isakmp
 set peer 203.0.113.2
 set transform-set MYSET
 match address 100

! Apply to interface
interface g0/1
 crypto map MYMAP
```

---

## Show Commands

| Command | Description |
|---------|-------------|
| `show interfaces serial <num>` | Display serial interface |
| `show controllers serial <num>` | Display DCE/DTE status |
| `show ppp all` | Display PPP status |
| `show interface tunnel <num>` | Display tunnel interface |
| `show crypto isakmp sa` | Display ISAKMP SAs |
| `show crypto ipsec sa` | Display IPSec SAs |
| `show crypto isakmp policy` | Display ISAKMP policies |
| `show crypto map` | Display crypto maps |

---

## VPN Types

| Type | Description |
|------|-------------|
| **Site-to-Site** | Connect two networks |
| **Remote Access** | Connect individual users |
| **GRE over IPSec** | Multicast/routing over VPN |
| **DMVPN** | Dynamic hub-and-spoke VPN |

## IPSec Protocols

| Protocol | Port/Number | Description |
|----------|-------------|-------------|
| IKE | UDP 500 | Key exchange |
| ESP | Protocol 50 | Encryption + Authentication |
| AH | Protocol 51 | Authentication only |
| NAT-T | UDP 4500 | NAT traversal |

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear crypto sa` | Clear all crypto SAs |
| `clear crypto isakmp` | Clear ISAKMP SAs |
