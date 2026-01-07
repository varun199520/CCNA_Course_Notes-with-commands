# Syslog Configuration Commands

## Syslog Destinations

| Command | Description |
|---------|-------------|
| `logging console <level>` | Log to console |
| `logging monitor <level>` | Log to VTY lines |
| `logging buffered <size> <level>` | Log to buffer (RAM) |
| `logging host <ip>` | Log to external syslog server |
| `logging <ip>` | Log to external server (shortcut) |

## Syslog Severity Levels

| Level | Keyword | Description |
|-------|---------|-------------|
| 0 | emergencies | System unusable |
| 1 | alerts | Immediate action required |
| 2 | critical | Critical conditions |
| 3 | errors | Error conditions |
| 4 | warnings | Warning conditions |
| 5 | notifications | Normal but significant |
| 6 | informational | Informational messages |
| 7 | debugging | Debug messages |

**Memory Aid**: "**E**very **A**wesome **C**isco **E**ngineer **W**ill **N**eed **I**ce cream **D**aily"

## Logging Configuration Examples

```
! Log to console (only critical and above)
logging console critical

! Log to buffer with 16KB size
logging buffered 16384 informational

! Log to external server
logging host 10.0.0.100
logging trap informational

! Disable console logging
no logging console
```

## Syslog Options

| Command | Description |
|---------|-------------|
| `logging trap <level>` | Set level for external server |
| `logging source-interface <int>` | Set source interface for syslog |
| `logging origin-id hostname` | Include hostname in messages |
| `logging origin-id ip` | Include IP in messages |
| `logging facility <facility>` | Set syslog facility |

## Timestamp Configuration

| Command | Description |
|---------|-------------|
| `service timestamps log datetime` | Add date/time to logs |
| `service timestamps log datetime msec` | Add milliseconds |
| `service timestamps log datetime localtime` | Use local timezone |
| `service timestamps log datetime show-timezone` | Show timezone |
| `service timestamps log uptime` | Use uptime instead of datetime |
| `no service timestamps` | Disable timestamps |

## Timestamp Example

```
service timestamps log datetime msec localtime show-timezone
service timestamps debug datetime msec localtime show-timezone
```

## Terminal Monitor

| Command | Description |
|---------|-------------|
| `terminal monitor` | Enable logging to current VTY session |
| `terminal no monitor` | Disable logging to current VTY |

## Show Commands

| Command | Description |
|---------|-------------|
| `show logging` | Display logging configuration and buffer |
| `show logging history` | Display logging history |
| `clear logging` | Clear logging buffer |

## Syslog Message Format

```
*Mar 1 00:00:00.000: %FACILITY-SEVERITY-MNEMONIC: Message
```

Example:
```
*Jan 5 14:30:00.123: %LINK-3-UPDOWN: Interface GigabitEthernet0/1, changed state to down
```

## Common Facilities

| Facility | Description |
|----------|-------------|
| %LINK | Interface link status |
| %LINEPROTO | Line protocol status |
| %SYS | System messages |
| %SEC | Security messages |
| %OSPF | OSPF messages |
| %CDP | CDP messages |

## Debug Commands

| Command | Description |
|---------|-------------|
| `debug <feature>` | Enable debugging for feature |
| `undebug all` | Disable all debugging |
| `no debug all` | Disable all debugging |
| `show debug` | Display active debug settings |

## Syslog Best Practices

1. Use external syslog server for log retention
2. Set appropriate severity levels per destination
3. Enable timestamps with timezone
4. Use buffered logging for local storage
5. Secure syslog traffic in production
