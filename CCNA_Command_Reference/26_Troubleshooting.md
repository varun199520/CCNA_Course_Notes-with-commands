# Troubleshooting Commands

## General Show Commands

| Command | Description |
|---------|-------------|
| `show running-config` | Display current configuration |
| `show startup-config` | Display saved configuration |
| `show version` | Display IOS version and uptime |
| `show inventory` | Display hardware inventory |
| `show processes cpu` | Display CPU utilization |
| `show memory` | Display memory utilization |
| `show flash` | Display flash contents |
| `show history` | Display command history |

---

## Interface Troubleshooting

| Command | Description |
|---------|-------------|
| `show interfaces` | Display all interface details |
| `show interfaces <int>` | Display specific interface |
| `show ip interface brief` | Display interface summary |
| `show interfaces status` | Display switch port status |
| `show interfaces counters` | Display interface statistics |
| `show interfaces counters errors` | Display interface errors |

### Common Interface States

| Line Status | Protocol | Meaning |
|-------------|----------|---------|
| up | up | Working properly |
| up | down | Layer 2 problem (encapsulation, keepalives) |
| down | down | Layer 1 problem (cable, no carrier) |
| administratively down | down | Interface shutdown |

### Interface Error Types

| Error | Description |
|-------|-------------|
| CRC | Bad frame, noise, duplex mismatch |
| Collisions | Half-duplex, network congestion |
| Runts | Frames < 64 bytes |
| Giants | Frames > 1518 bytes |
| Input errors | Total receive errors |
| Output errors | Total transmit errors |

---

## Connectivity Troubleshooting

| Command | Description |
|---------|-------------|
| `ping <ip>` | Test Layer 3 connectivity |
| `ping <ip> source <interface>` | Ping from specific source |
| `traceroute <ip>` | Trace path to destination |
| `show arp` | Display ARP table |
| `show ip arp` | Display IP ARP table |
| `clear arp-cache` | Clear ARP cache |

### Extended Ping

```
Router# ping
Protocol [ip]: 
Target IP address: 10.0.0.1
Repeat count [5]: 100
Datagram size [100]: 1500
Timeout in seconds [2]: 
Extended commands [n]: y
Source address or interface: 192.168.1.1
```

---

## Routing Troubleshooting

| Command | Description |
|---------|-------------|
| `show ip route` | Display routing table |
| `show ip route <network>` | Display route to network |
| `show ip route summary` | Display routing summary |
| `show ip protocols` | Display routing protocols |
| `show ip ospf neighbor` | Display OSPF neighbors |
| `show ip ospf interface` | Display OSPF interfaces |
| `show ip eigrp neighbors` | Display EIGRP neighbors |

---

## Switching Troubleshooting

| Command | Description |
|---------|-------------|
| `show mac address-table` | Display MAC address table |
| `show mac address-table interface <int>` | Display MACs on interface |
| `show vlan brief` | Display VLANs |
| `show interfaces trunk` | Display trunk ports |
| `show spanning-tree` | Display STP status |
| `show etherchannel summary` | Display EtherChannel |

---

## DHCP Troubleshooting

| Command | Description |
|---------|-------------|
| `show ip dhcp binding` | Display DHCP leases |
| `show ip dhcp pool` | Display DHCP pools |
| `show ip dhcp conflict` | Display IP conflicts |
| `debug ip dhcp server events` | Debug DHCP events |

---

## NAT Troubleshooting

| Command | Description |
|---------|-------------|
| `show ip nat translations` | Display NAT table |
| `show ip nat statistics` | Display NAT statistics |
| `debug ip nat` | Debug NAT operations |
| `clear ip nat translation *` | Clear NAT translations |

---

## ACL Troubleshooting

| Command | Description |
|---------|-------------|
| `show access-lists` | Display all ACLs |
| `show ip interface <int>` | Display ACLs on interface |
| `show access-lists <name/num>` | Display specific ACL |

---

## Debug Commands

| Command | Description |
|---------|-------------|
| `debug ip packet` | Debug IP packets |
| `debug ip routing` | Debug routing updates |
| `debug ip ospf events` | Debug OSPF events |
| `debug ip ospf adj` | Debug OSPF adjacencies |
| `debug spanning-tree events` | Debug STP events |
| `terminal monitor` | Enable debug to VTY |
| `undebug all` | Disable all debugging |

**Warning**: Debug commands can impact device performance. Use with caution.

---

## Logging Commands

| Command | Description |
|---------|-------------|
| `show logging` | Display log buffer |
| `show logging history` | Display logging history |
| `clear logging` | Clear log buffer |

---

## CDP/LLDP Troubleshooting

| Command | Description |
|---------|-------------|
| `show cdp neighbors` | Display CDP neighbors |
| `show cdp neighbors detail` | Display detailed CDP info |
| `show lldp neighbors` | Display LLDP neighbors |

---

## Password Recovery

### Router Password Recovery

1. Power cycle and send break signal
2. Change config register: `confreg 0x2142`
3. Boot router: `reset`
4. Enter privileged mode: `enable`
5. Copy startup to running: `copy startup-config running-config`
6. Change password: `enable secret <password>`
7. Reset config register: `config-register 0x2102`
8. Save config: `write memory`

### Switch Password Recovery

1. Hold MODE button during boot
2. Initialize flash: `flash_init`
3. Rename config: `rename flash:config.text flash:config.old`
4. Boot switch: `boot`
5. Recover config: `rename flash:config.old flash:config.text`
6. Load config: `copy flash:config.text running-config`
7. Change password and save

---

## Common Troubleshooting Steps

1. **Define the problem** - Gather symptoms
2. **Gather information** - Use show commands
3. **Analyze data** - Compare to baseline
4. **Eliminate possibilities** - Test hypotheses
5. **Propose solution** - Plan fix
6. **Implement solution** - Make changes
7. **Verify solution** - Test fix
8. **Document** - Record findings
