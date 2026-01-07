# Access Control List (ACL) Commands

## ACL Types Overview

| Type | Number Range | Matches On |
|------|--------------|------------|
| Standard Numbered | 1-99, 1300-1999 | Source IP only |
| Extended Numbered | 100-199, 2000-2699 | Source/Dest IP, Protocol, Ports |
| Standard Named | Name | Source IP only |
| Extended Named | Name | Source/Dest IP, Protocol, Ports |

---

## Standard ACL Configuration

### Numbered Standard ACL

| Command | Description |
|---------|-------------|
| `access-list <1-99> permit <source> <wildcard>` | Permit source |
| `access-list <1-99> deny <source> <wildcard>` | Deny source |
| `access-list <1-99> permit any` | Permit all traffic |
| `access-list <1-99> deny any` | Deny all traffic (implicit) |
| `access-list <1-99> permit host <ip>` | Permit single host |
| `access-list <1-99> remark <text>` | Add comment |

### Named Standard ACL

| Command | Description |
|---------|-------------|
| `ip access-list standard <name>` | Create/enter named standard ACL |
| `permit <source> <wildcard>` | Permit source |
| `deny <source> <wildcard>` | Deny source |
| `<seq> permit <source> <wildcard>` | Add entry with sequence number |

### Standard ACL Examples

```
! Numbered standard ACL
access-list 1 permit 192.168.1.0 0.0.0.255
access-list 1 deny any

! Named standard ACL
ip access-list standard BLOCK_GUEST
 deny 10.0.0.0 0.0.0.255
 permit any
```

---

## Extended ACL Configuration

### Numbered Extended ACL

| Command | Description |
|---------|-------------|
| `access-list <100-199> permit <protocol> <src> <src-wild> <dst> <dst-wild>` | Basic permit |
| `access-list <100-199> permit tcp <src> <src-wild> <dst> <dst-wild> eq <port>` | Permit TCP port |
| `access-list <100-199> permit icmp <src> <src-wild> <dst> <dst-wild>` | Permit ICMP |

### Named Extended ACL

| Command | Description |
|---------|-------------|
| `ip access-list extended <name>` | Create/enter named extended ACL |
| `permit <protocol> <src> <wild> <dst> <wild> [options]` | Add permit entry |
| `deny <protocol> <src> <wild> <dst> <wild> [options]` | Add deny entry |

### Extended ACL Examples

```
! Permit HTTP and HTTPS from any to web server
access-list 100 permit tcp any host 10.0.0.100 eq 80
access-list 100 permit tcp any host 10.0.0.100 eq 443
access-list 100 deny ip any any

! Named extended ACL
ip access-list extended WEB_ACCESS
 permit tcp 192.168.1.0 0.0.0.255 any eq 80
 permit tcp 192.168.1.0 0.0.0.255 any eq 443
 permit icmp any any
 deny ip any any
```

---

## ACL Port Operators

| Operator | Description |
|----------|-------------|
| `eq <port>` | Equal to |
| `neq <port>` | Not equal to |
| `lt <port>` | Less than |
| `gt <port>` | Greater than |
| `range <start> <end>` | Range of ports |

## Common Port Numbers

| Port | Protocol | Service |
|------|----------|---------|
| 20-21 | TCP | FTP |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 67-68 | UDP | DHCP |
| 69 | UDP | TFTP |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 443 | TCP | HTTPS |

---

## Apply ACL to Interface

| Command | Description |
|---------|-------------|
| `ip access-group <acl> in` | Apply ACL inbound |
| `ip access-group <acl> out` | Apply ACL outbound |

```
interface g0/0
 ip access-group 100 in
```

## Apply ACL to VTY Lines

```
line vty 0 15
 access-class 10 in
```

---

## Modify Named ACL

| Command | Description |
|---------|-------------|
| `no <seq-number>` | Delete specific entry |
| `<seq> permit/deny ...` | Insert entry at sequence |

```
ip access-list extended WEB_ACCESS
 no 20
 15 permit tcp any any eq 8080
```

---

## Show Commands

| Command | Description |
|---------|-------------|
| `show access-lists` | Display all ACLs |
| `show access-lists <number/name>` | Display specific ACL |
| `show ip access-lists` | Display IP ACLs |
| `show ip interface <int>` | Display ACLs applied to interface |
| `show running-config | include access` | Display ACL config |

## Clear ACL Counters

| Command | Description |
|---------|-------------|
| `clear access-list counters` | Clear all ACL counters |
| `clear access-list counters <acl>` | Clear specific ACL counters |

---

## ACL Best Practices

1. **Standard ACLs**: Place close to **destination**
2. **Extended ACLs**: Place close to **source**
3. Order entries from most specific to least specific
4. Always end with explicit deny or permit
5. Document with remarks
6. Test before applying to production

## Implicit Deny

All ACLs have an invisible `deny any` at the end. If no entries match, traffic is denied.
