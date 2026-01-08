# SSH and Console Security Commands

## Console Line Security

| Command | Description |
|---------|-------------|
| `line console 0` | Enter console line config |
| `password <password>` | Set console password |
| `login` | Enable password prompt |
| `login local` | Use local user database |
| `exec-timeout <min> <sec>` | Set idle timeout |
| `logging synchronous` | Prevent log messages from interrupting input |

```
line console 0
 password cisco123
 login
 exec-timeout 5 0
 logging synchronous
```

## VTY Line Security

| Command | Description |
|---------|-------------|
| `line vty 0 15` | Enter VTY line config (16 lines) |
| `password <password>` | Set VTY password |
| `login` | Enable password prompt |
| `login local` | Use local user database |
| `transport input <protocol>` | Set allowed protocols |
| `exec-timeout <min> <sec>` | Set idle timeout |
| `access-class <acl> in` | Apply ACL to restrict access |

```
line vty 0 15
 login local
 transport input ssh
 exec-timeout 10 0
 access-class 10 in
```

## Local User Configuration

| Command | Description |
|---------|-------------|
| `username <name> password <pass>` | Create user with plaintext password |
| `username <name> secret <pass>` | Create user with encrypted password |
| `username <name> privilege <0-15>` | Set privilege level |

```
username admin privilege 15 secret AdminPass123
username readonly privilege 1 secret ReadOnly123
```

## Enable Password/Secret

| Command | Description |
|---------|-------------|
| `enable password <password>` | Set unencrypted enable password |
| `enable secret <password>` | Set encrypted enable password (preferred) |
| `service password-encryption` | Encrypt all plaintext passwords |

---

## SSH Configuration

### Prerequisites for SSH

1. Configure hostname (not "Router" or "Switch")
2. Configure domain name
3. Generate RSA keys
4. Configure VTY lines for SSH

### SSH Setup Commands

| Command | Description |
|---------|-------------|
| `hostname <name>` | Set hostname |
| `ip domain-name <domain>` | Set domain name |
| `crypto key generate rsa` | Generate RSA keys |
| `crypto key generate rsa modulus <bits>` | Generate keys with specific size |
| `ip ssh version 2` | Enable SSH version 2 only |

### SSH Configuration Example

```
hostname R1
ip domain-name example.com
crypto key generate rsa modulus 2048
ip ssh version 2
ip ssh time-out 60
ip ssh authentication-retries 3

username admin secret SecurePass123

line vty 0 15
 login local
 transport input ssh
 exec-timeout 10 0
```

### SSH Optional Settings

| Command | Description |
|---------|-------------|
| `ip ssh time-out <seconds>` | SSH negotiation timeout |
| `ip ssh authentication-retries <num>` | Max auth attempts |
| `ip ssh source-interface <int>` | Source interface for SSH |

### Delete RSA Keys

| Command | Description |
|---------|-------------|
| `crypto key zeroize rsa` | Delete RSA keys (disables SSH) |

---

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip ssh` | Display SSH configuration |
| `show ssh` | Display active SSH sessions |
| `show users` | Display logged-in users |
| `show line` | Display line status |
| `show running-config | section line` | Display line configuration |

---

## AAA Configuration (Basic)

| Command | Description |
|---------|-------------|
| `aaa new-model` | Enable AAA |
| `aaa authentication login default local` | Use local database |
| `aaa authentication login <list> local` | Create named auth list |

---

## Transport Input Options

| Option | Description |
|--------|-------------|
| `transport input none` | Disable all remote access |
| `transport input telnet` | Allow Telnet only |
| `transport input ssh` | Allow SSH only (recommended) |
| `transport input telnet ssh` | Allow both |
| `transport input all` | Allow all protocols |

---

## Privilege Levels

| Level | Description |
|-------|-------------|
| 0 | Limited commands (logout, enable, disable, help, exit) |
| 1 | User EXEC mode (default) |
| 15 | Privileged EXEC mode (full access) |
| 2-14 | Custom privilege levels |

```
! Custom privilege level
privilege exec level 5 show running-config
username operator privilege 5 secret OperPass
```

---

## Security Best Practices

1. Use `enable secret` instead of `enable password`
2. Use SSH instead of Telnet
3. Use RSA keys of 2048 bits or higher
4. Set appropriate exec-timeout
5. Use ACLs to restrict management access
6. Use local usernames with `secret` (encrypted)
7. Enable `service password-encryption`
