# QoS (Quality of Service) Commands

## QoS Concepts

### Traffic Characteristics

| Metric | Description |
|--------|-------------|
| **Bandwidth** | Capacity of link |
| **Delay** | Time for packet to travel |
| **Jitter** | Variation in delay |
| **Loss** | Dropped packets |

### Traffic Types and Requirements

| Traffic Type | Bandwidth | Delay Sensitive | Loss Tolerant |
|--------------|-----------|-----------------|---------------|
| Voice | Low | Very High | Low |
| Video | High | High | Low |
| Data | Variable | Low | Very Low |

---

## Classification and Marking

### DSCP Values

| DSCP Name | DSCP Value | IP Precedence | Description |
|-----------|------------|---------------|-------------|
| EF | 46 | 5 | Expedited Forwarding (Voice) |
| AF41 | 34 | 4 | Video |
| AF31 | 26 | 3 | Critical Data |
| AF21 | 18 | 2 | Transactional Data |
| AF11 | 10 | 1 | Bulk Data |
| CS0/BE | 0 | 0 | Best Effort (Default) |

### Class of Service (CoS) - Layer 2

| CoS | Traffic Type |
|-----|--------------|
| 7 | Reserved |
| 6 | Reserved |
| 5 | Voice |
| 4 | Video |
| 3 | Voice Signaling |
| 2 | High-Priority Data |
| 1 | Medium-Priority Data |
| 0 | Best Effort |

---

## MQC (Modular QoS CLI)

### Class Map Configuration

| Command | Description |
|---------|-------------|
| `class-map [match-all|match-any] <name>` | Create class map |
| `match dscp <value>` | Match DSCP value |
| `match access-group <acl>` | Match ACL |
| `match protocol <protocol>` | Match protocol (NBAR) |
| `match cos <value>` | Match CoS value |

### Policy Map Configuration

| Command | Description |
|---------|-------------|
| `policy-map <name>` | Create policy map |
| `class <class-name>` | Reference class map |
| `set dscp <value>` | Set DSCP marking |
| `set cos <value>` | Set CoS marking |
| `bandwidth <kbps>` | Guarantee bandwidth |
| `bandwidth percent <percent>` | Guarantee bandwidth % |
| `priority <kbps>` | Low-latency queue (LLQ) |
| `police <bps> <burst>` | Rate limit traffic |
| `shape average <bps>` | Traffic shaping |
| `queue-limit <packets>` | Set queue depth |

### Apply Policy to Interface

| Command | Description |
|---------|-------------|
| `service-policy input <policy>` | Apply policy inbound |
| `service-policy output <policy>` | Apply policy outbound |

---

## QoS Configuration Example

```
! Define class maps
class-map match-all VOICE
 match dscp ef
class-map match-all VIDEO
 match dscp af41
class-map match-all CRITICAL
 match access-group 101

! Define policy map
policy-map WAN-QOS
 class VOICE
  priority 256
 class VIDEO
  bandwidth 1024
 class CRITICAL
  bandwidth 512
 class class-default
  fair-queue

! Apply to interface
interface g0/1
 service-policy output WAN-QOS
```

---

## Policing vs Shaping

| Feature | Policing | Shaping |
|---------|----------|---------|
| Excess Traffic | Drops/Remarks | Buffers |
| Delay | No | Yes |
| Direction | Input/Output | Output only |
| Burst | Yes | Yes |

### Policing Configuration

```
policy-map POLICE-TRAFFIC
 class class-default
  police 1000000 8000 conform-action transmit exceed-action drop
```

### Shaping Configuration

```
policy-map SHAPE-TRAFFIC
 class class-default
  shape average 1000000
```

---

## Voice VLAN Configuration

| Command | Description |
|---------|-------------|
| `switchport voice vlan <vlan-id>` | Configure voice VLAN |
| `mls qos trust cos` | Trust CoS from phone |
| `mls qos trust dscp` | Trust DSCP markings |

```
interface g0/1
 switchport mode access
 switchport access vlan 10
 switchport voice vlan 20
 mls qos trust cos
```

---

## Show Commands

| Command | Description |
|---------|-------------|
| `show class-map` | Display class maps |
| `show policy-map` | Display policy maps |
| `show policy-map interface <int>` | Display applied policies |
| `show mls qos` | Display QoS status |
| `show mls qos interface <int>` | Display interface QoS |

---

## QoS Models

| Model | Description |
|-------|-------------|
| **Best Effort** | No QoS, FIFO queuing |
| **IntServ** | Per-flow reservation (RSVP) |
| **DiffServ** | Per-hop behavior, scalable |

## Queuing Methods

| Method | Description |
|--------|-------------|
| FIFO | First In, First Out |
| PQ | Priority Queuing |
| WFQ | Weighted Fair Queuing |
| CBWFQ | Class-Based WFQ |
| LLQ | Low Latency Queuing |
