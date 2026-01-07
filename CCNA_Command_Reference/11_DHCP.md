# DHCP Configuration Commands

## DHCP Server Configuration

| Command | Description |
|---------|-------------|
| `ip dhcp pool <name>` | Create DHCP pool and enter config mode |
| `network <ip> <mask>` | Define network for pool |
| `network <ip> /<prefix>` | Define network with prefix |
| `default-router <ip>` | Set default gateway for clients |
| `dns-server <ip> [ip2]` | Set DNS server(s) |
| `domain-name <name>` | Set domain name |
| `lease <days> [hours] [minutes]` | Set lease duration |
| `lease infinite` | Set infinite lease |

## DHCP Exclusions

| Command | Description |
|---------|-------------|
| `ip dhcp excluded-address <ip>` | Exclude single IP |
| `ip dhcp excluded-address <start-ip> <end-ip>` | Exclude IP range |

## DHCP Server Example

```
! Exclude addresses for static devices
ip dhcp excluded-address 192.168.1.1 192.168.1.10

! Create DHCP pool
ip dhcp pool LAN_POOL
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.1
 dns-server 8.8.8.8 8.8.4.4
 domain-name example.com
 lease 7
```

## DHCP Relay Agent

| Command | Description |
|---------|-------------|
| `ip helper-address <dhcp-server-ip>` | Forward DHCP requests to server (interface config) |

```
interface g0/0
 ip address 192.168.1.1 255.255.255.0
 ip helper-address 10.0.0.100
```

## DHCP Client Configuration

| Command | Description |
|---------|-------------|
| `ip address dhcp` | Obtain IP address via DHCP (interface config) |

```
interface g0/0
 ip address dhcp
 no shutdown
```

## DHCP Show Commands

| Command | Description |
|---------|-------------|
| `show ip dhcp pool` | Display DHCP pool info |
| `show ip dhcp binding` | Display DHCP leases |
| `show ip dhcp server statistics` | Display DHCP server stats |
| `show ip dhcp conflict` | Display IP conflicts |

## DHCP Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip dhcp binding *` | Clear all DHCP bindings |
| `clear ip dhcp binding <ip>` | Clear specific binding |
| `clear ip dhcp conflict *` | Clear conflict log |

## DHCP Debug Commands

| Command | Description |
|---------|-------------|
| `debug ip dhcp server events` | Debug DHCP server events |
| `debug ip dhcp server packet` | Debug DHCP packets |

## DHCP Process (DORA)

| Step | Message | Description |
|------|---------|-------------|
| 1 | **Discover** | Client broadcasts to find servers |
| 2 | **Offer** | Server offers IP address |
| 3 | **Request** | Client requests offered address |
| 4 | **Acknowledge** | Server confirms lease |

## DHCP Ports

| Port | Protocol | Direction |
|------|----------|-----------|
| UDP 67 | DHCP Server | Server listens |
| UDP 68 | DHCP Client | Client listens |

## DHCP Options

| Option | Description |
|--------|-------------|
| Option 1 | Subnet Mask |
| Option 3 | Default Gateway |
| Option 6 | DNS Server |
| Option 15 | Domain Name |
| Option 51 | Lease Time |
| Option 150 | TFTP Server (Cisco IP Phones) |

## Additional DHCP Pool Options

| Command | Description |
|---------|-------------|
| `option 150 ip <ip>` | Set TFTP server for IP phones |
| `netbios-name-server <ip>` | Set WINS server |
| `next-server <ip>` | Set TFTP/boot server |
| `bootfile <filename>` | Set boot filename |
