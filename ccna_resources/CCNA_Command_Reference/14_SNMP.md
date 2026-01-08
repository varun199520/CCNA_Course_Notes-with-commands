# SNMP Configuration Commands

## SNMP Versions

| Version | Authentication | Encryption |
|---------|---------------|------------|
| SNMPv1 | Community string (plaintext) | No |
| SNMPv2c | Community string (plaintext) | No |
| SNMPv3 | Username/password | Yes (optional) |

## SNMPv2c Configuration

| Command | Description |
|---------|-------------|
| `snmp-server community <string> ro` | Create read-only community |
| `snmp-server community <string> rw` | Create read-write community |
| `snmp-server community <string> ro <acl>` | Restrict access with ACL |

## SNMP Trap/Inform Configuration

| Command | Description |
|---------|-------------|
| `snmp-server host <ip> version 2c <community>` | Configure trap destination |
| `snmp-server host <ip> informs version 2c <community>` | Configure inform destination |
| `snmp-server enable traps` | Enable all traps |
| `snmp-server enable traps <type>` | Enable specific trap type |

## Common Trap Types

| Command | Description |
|---------|-------------|
| `snmp-server enable traps snmp` | SNMP authentication traps |
| `snmp-server enable traps config` | Configuration change traps |
| `snmp-server enable traps syslog` | Syslog traps |
| `snmp-server enable traps ospf` | OSPF traps |
| `snmp-server enable traps bgp` | BGP traps |

## SNMPv3 Configuration

| Command | Description |
|---------|-------------|
| `snmp-server group <name> v3 <auth\|priv\|noauth>` | Create SNMPv3 group |
| `snmp-server user <name> <group> v3 auth <md5\|sha> <password>` | Create auth user |
| `snmp-server user <name> <group> v3 auth <md5\|sha> <password> priv <des\|aes> <password>` | Create auth+priv user |

## SNMPv3 Security Levels

| Level | Description |
|-------|-------------|
| `noauth` | No authentication, no encryption |
| `auth` | Authentication, no encryption |
| `priv` | Authentication and encryption |

## SNMPv3 Example

```
! Create group with auth and privacy
snmp-server group ADMIN v3 priv

! Create user with SHA auth and AES encryption
snmp-server user admin1 ADMIN v3 auth sha AuthPass123 priv aes 128 PrivPass123

! Configure trap destination for SNMPv3
snmp-server host 10.0.0.100 version 3 priv admin1
```

## SNMP System Information

| Command | Description |
|---------|-------------|
| `snmp-server contact <text>` | Set contact information |
| `snmp-server location <text>` | Set device location |
| `snmp-server chassis-id <text>` | Set chassis ID |

## Show Commands

| Command | Description |
|---------|-------------|
| `show snmp` | Display SNMP statistics |
| `show snmp community` | Display community strings |
| `show snmp host` | Display trap destinations |
| `show snmp user` | Display SNMPv3 users |
| `show snmp group` | Display SNMPv3 groups |
| `show snmp engineID` | Display SNMP engine ID |

## SNMP Components

| Component | Description |
|-----------|-------------|
| **NMS** | Network Management System (manager) |
| **Agent** | SNMP software on managed device |
| **MIB** | Management Information Base (database) |
| **OID** | Object Identifier (variable identifier) |

## SNMP Messages

| Message | Direction | Description |
|---------|-----------|-------------|
| **Get** | NMS → Agent | Request single variable |
| **GetNext** | NMS → Agent | Request next variable in MIB |
| **GetBulk** | NMS → Agent | Request multiple variables (v2+) |
| **Set** | NMS → Agent | Modify variable value |
| **Trap** | Agent → NMS | Unsolicited notification |
| **Inform** | Agent → NMS | Acknowledged notification (v2+) |
| **Response** | Agent → NMS | Reply to Get/Set |

## SNMP Ports

| Port | Protocol | Description |
|------|----------|-------------|
| UDP 161 | SNMP | Agent listens for requests |
| UDP 162 | SNMP Trap | NMS listens for traps |
