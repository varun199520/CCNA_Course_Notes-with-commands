# EIGRP Configuration Commands

## Enable EIGRP

| Command | Description |
|---------|-------------|
| `router eigrp <AS-number>` | Enter EIGRP router configuration mode |
| `eigrp router-id <id>` | Set EIGRP router ID |
| `network <ip>` | Enable EIGRP on classful network |
| `network <ip> <wildcard>` | Enable EIGRP with wildcard mask |

## Basic Configuration Example

```
router eigrp 100
 eigrp router-id 1.1.1.1
 network 10.0.0.0
 network 192.168.1.0 0.0.0.255
 no auto-summary
```

## EIGRP Settings

| Command | Description |
|---------|-------------|
| `no auto-summary` | Disable automatic summarization |
| `passive-interface <interface>` | Stop sending EIGRP hellos on interface |
| `passive-interface default` | Make all interfaces passive |
| `no passive-interface <interface>` | Enable EIGRP on specific interface |

## EIGRP Metric (Bandwidth & Delay)

| Command | Description |
|---------|-------------|
| `bandwidth <kbps>` | Set interface bandwidth (interface config) |
| `delay <tens-of-microseconds>` | Set interface delay (interface config) |
| `metric weights 0 <k1> <k2> <k3> <k4> <k5>` | Modify K-values |

## EIGRP Authentication

| Command | Description |
|---------|-------------|
| `key chain <name>` | Create key chain |
| `key <number>` | Create key in key chain |
| `key-string <password>` | Set key password |
| `ip authentication mode eigrp <AS> md5` | Enable MD5 auth on interface |
| `ip authentication key-chain eigrp <AS> <keychain>` | Apply key chain to interface |

## EIGRP Variance and Load Balancing

| Command | Description |
|---------|-------------|
| `variance <multiplier>` | Enable unequal-cost load balancing |
| `maximum-paths <number>` | Set max equal-cost paths (default 4) |

## EIGRP Timers

| Command | Description |
|---------|-------------|
| `ip hello-interval eigrp <AS> <seconds>` | Set hello interval (interface) |
| `ip hold-time eigrp <AS> <seconds>` | Set hold time (interface) |

## Named EIGRP Configuration

```
router eigrp <name>
 address-family ipv4 unicast autonomous-system <AS>
  eigrp router-id <id>
  network <ip> <wildcard>
  af-interface <interface>
   passive-interface
  exit-af-interface
```

## EIGRP for IPv6

| Command | Description |
|---------|-------------|
| `ipv6 router eigrp <AS>` | Enter EIGRP for IPv6 config |
| `eigrp router-id <id>` | Set router ID (required) |
| `no shutdown` | Enable EIGRP for IPv6 |
| `ipv6 eigrp <AS>` | Enable on interface |

## Show Commands

| Command | Description |
|---------|-------------|
| `show ip eigrp neighbors` | Display EIGRP neighbors |
| `show ip eigrp topology` | Display EIGRP topology table |
| `show ip eigrp topology all-links` | Display all routes in topology |
| `show ip eigrp interfaces` | Display EIGRP-enabled interfaces |
| `show ip route eigrp` | Display EIGRP routes |
| `show ip protocols` | Display routing protocol info |
| `show ip eigrp traffic` | Display EIGRP packet statistics |

## EIGRP Terminology

| Term | Description |
|------|-------------|
| **Successor** | Best route to destination |
| **Feasible Successor** | Backup route meeting feasibility condition |
| **Feasible Distance (FD)** | Metric to reach destination via successor |
| **Reported Distance (RD)** | Neighbor's metric to destination |
| **Feasibility Condition** | RD < FD of current successor |

## EIGRP Metric Formula

```
Metric = 256 * ((K1 * BW) + (K2 * BW)/(256 - Load) + (K3 * Delay)) * (K5/(Reliability + K4))

Default K-values: K1=1, K2=0, K3=1, K4=0, K5=0
Simplified: Metric = 256 * (BW + Delay)

BW = 10^7 / lowest bandwidth in kbps
Delay = sum of delays in tens of microseconds
```

## Clear Commands

| Command | Description |
|---------|-------------|
| `clear ip eigrp neighbors` | Reset all EIGRP neighbors |
| `clear ip eigrp neighbors <ip>` | Reset specific neighbor |
