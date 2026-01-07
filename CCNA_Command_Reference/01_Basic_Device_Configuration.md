# Basic Device Configuration Commands

## Accessing CLI Modes

| Command | Description |
|---------|-------------|
| `enable` | Enter privileged EXEC mode from user EXEC mode |
| `configure terminal` | Enter global configuration mode from privileged EXEC mode |
| `exit` | Exit current mode and go back one level |
| `end` | Return to privileged EXEC mode from any config mode |
| `disable` | Return to user EXEC mode from privileged EXEC mode |

## Hostname Configuration

| Command | Description |
|---------|-------------|
| `hostname <name>` | Set the device hostname |

## Password Configuration

| Command | Description |
|---------|-------------|
| `enable password <password>` | Set unencrypted enable password |
| `enable secret <password>` | Set encrypted enable password (preferred) |
| `service password-encryption` | Encrypt all plaintext passwords in config |
| `line console 0` | Enter console line configuration mode |
| `line vty 0 15` | Enter VTY (virtual terminal) line configuration mode |
| `password <password>` | Set password for console/VTY line |
| `login` | Enable password checking on the line |
| `login local` | Use local username database for authentication |
| `username <name> secret <password>` | Create local user with encrypted password |

## Banner Configuration

| Command | Description |
|---------|-------------|
| `banner motd #<message>#` | Set Message of the Day banner |
| `banner login #<message>#` | Set login banner |

## Saving Configuration

| Command | Description |
|---------|-------------|
| `copy running-config startup-config` | Save running config to NVRAM |
| `write` | Save running config (shortcut) |
| `write memory` | Save running config (shortcut) |
| `copy startup-config running-config` | Load startup config into running config |
| `erase startup-config` | Delete startup configuration |
| `reload` | Restart the device |

## Viewing Configuration

| Command | Description |
|---------|-------------|
| `show running-config` | Display current running configuration |
| `show startup-config` | Display saved startup configuration |
| `show version` | Display IOS version and hardware info |
| `show history` | Display command history |

## Clock Configuration

| Command | Description |
|---------|-------------|
| `clock set <hh:mm:ss> <day> <month> <year>` | Set the system clock |
| `show clock` | Display current time |
| `clock timezone <name> <offset>` | Set timezone |

## DNS Configuration

| Command | Description |
|---------|-------------|
| `ip domain-name <domain>` | Set domain name |
| `ip name-server <ip-address>` | Set DNS server |
| `ip domain-lookup` | Enable DNS lookup (default) |
| `no ip domain-lookup` | Disable DNS lookup |

## Description Commands

| Command | Description |
|---------|-------------|
| `description <text>` | Add description to interface |
