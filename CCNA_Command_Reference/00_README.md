# CCNA Command Reference Guide

A comprehensive collection of Cisco IOS commands organized by topic for CCNA 200-301 exam preparation.

## Contents

| File | Topic |
|------|-------|
| [01_Basic_Device_Configuration.md](01_Basic_Device_Configuration.md) | Hostname, passwords, banners, saving config |
| [02_Interface_Configuration.md](02_Interface_Configuration.md) | Interface setup, speed/duplex, IP addressing |
| [03_VLAN_Configuration.md](03_VLAN_Configuration.md) | VLANs, trunking, DTP, VTP, inter-VLAN routing |
| [04_Spanning_Tree_Protocol.md](04_Spanning_Tree_Protocol.md) | STP, RSTP, PortFast, BPDU Guard |
| [05_EtherChannel.md](05_EtherChannel.md) | LACP, PAgP, load balancing |
| [06_Static_Routing.md](06_Static_Routing.md) | Static routes, default routes, floating static |
| [07_OSPF.md](07_OSPF.md) | OSPF configuration, areas, authentication |
| [08_EIGRP.md](08_EIGRP.md) | EIGRP configuration, metrics, variance |
| [09_RIP.md](09_RIP.md) | RIP v1/v2 configuration |
| [10_IPv6.md](10_IPv6.md) | IPv6 addressing, routing, DHCPv6 |
| [11_DHCP.md](11_DHCP.md) | DHCP server, relay agent, client |
| [12_NAT.md](12_NAT.md) | Static NAT, Dynamic NAT, PAT |
| [13_NTP.md](13_NTP.md) | NTP server, client, authentication |
| [14_SNMP.md](14_SNMP.md) | SNMPv2c, SNMPv3, traps |
| [15_Syslog.md](15_Syslog.md) | Logging, severity levels, timestamps |
| [16_CDP_LLDP.md](16_CDP_LLDP.md) | Device discovery protocols |
| [17_Access_Control_Lists.md](17_Access_Control_Lists.md) | Standard and extended ACLs |
| [18_SSH_and_Console_Security.md](18_SSH_and_Console_Security.md) | SSH, VTY, console security |
| [19_Port_Security.md](19_Port_Security.md) | Port security, violation modes |
| [20_DHCP_Snooping.md](20_DHCP_Snooping.md) | DHCP snooping, DAI |
| [21_FHRP.md](21_FHRP.md) | HSRP, VRRP, GLBP |
| [22_Wireless.md](22_Wireless.md) | Wireless standards, WLC, 802.1X |
| [23_QoS.md](23_QoS.md) | Classification, marking, queuing |
| [24_WAN_and_VPN.md](24_WAN_and_VPN.md) | WAN types, GRE, IPSec VPN |
| [25_Network_Automation.md](25_Network_Automation.md) | REST APIs, JSON, YAML, SDN |
| [26_Troubleshooting.md](26_Troubleshooting.md) | Debug, show commands, password recovery |

## Quick Reference

### CLI Modes

| Mode | Prompt | Access |
|------|--------|--------|
| User EXEC | `Router>` | Default |
| Privileged EXEC | `Router#` | `enable` |
| Global Config | `Router(config)#` | `configure terminal` |
| Interface Config | `Router(config-if)#` | `interface <type> <num>` |
| Line Config | `Router(config-line)#` | `line <type> <num>` |
| Router Config | `Router(config-router)#` | `router <protocol>` |

### Essential Commands

```
enable                          ! Enter privileged mode
configure terminal              ! Enter global config
interface g0/0                  ! Enter interface config
no shutdown                     ! Enable interface
exit                            ! Go back one level
end                             ! Return to privileged mode
copy running-config startup-config   ! Save configuration
show running-config             ! View current config
```

### Important Port Numbers

| Port | Protocol | Service |
|------|----------|---------|
| 20-21 | TCP | FTP |
| 22 | TCP | SSH |
| 23 | TCP | Telnet |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 67-68 | UDP | DHCP |
| 80 | TCP | HTTP |
| 443 | TCP | HTTPS |
| 161-162 | UDP | SNMP |

### Administrative Distance

| Source | AD |
|--------|-----|
| Connected | 0 |
| Static | 1 |
| EIGRP | 90 |
| OSPF | 110 |
| RIP | 120 |

---

*Based on Jeremy's IT Lab CCNA 200-301 Course*
