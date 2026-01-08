# First Hop Redundancy Protocol (FHRP) Commands

## FHRP Overview

| Protocol | Standard | Virtual MAC | Load Balancing |
|----------|----------|-------------|----------------|
| HSRP | Cisco | 0000.0c07.acXX | Per-group |
| VRRP | IEEE | 0000.5e00.01XX | Per-group |
| GLBP | Cisco | 0007.b400.XXYY | Automatic |

---

## HSRP (Hot Standby Router Protocol)

### HSRP Version 1 Configuration

| Command | Description |
|---------|-------------|
| `standby <group> ip <virtual-ip>` | Configure HSRP virtual IP |
| `standby <group> priority <0-255>` | Set priority (default 100) |
| `standby <group> preempt` | Enable preemption |
| `standby <group> timers <hello> <hold>` | Set timers |

### HSRP Version 2 Configuration

| Command | Description |
|---------|-------------|
| `standby version 2` | Enable HSRP version 2 |
| `standby <group> ip <virtual-ip>` | Configure virtual IP |

### HSRP Configuration Example

```
! Router 1 (Active)
interface g0/0
 ip address 192.168.1.2 255.255.255.0
 standby version 2
 standby 1 ip 192.168.1.1
 standby 1 priority 110
 standby 1 preempt

! Router 2 (Standby)
interface g0/0
 ip address 192.168.1.3 255.255.255.0
 standby version 2
 standby 1 ip 192.168.1.1
 standby 1 preempt
```

### HSRP Tracking

| Command | Description |
|---------|-------------|
| `standby <group> track <interface> <decrement>` | Track interface |
| `standby <group> track <object-num> decrement <value>` | Track object |

```
! Decrement priority if WAN goes down
interface g0/0
 standby 1 track g0/1 20
```

### HSRP Show Commands

| Command | Description |
|---------|-------------|
| `show standby` | Display HSRP status |
| `show standby brief` | Display HSRP summary |
| `show standby <interface>` | Display HSRP for interface |

---

## VRRP (Virtual Router Redundancy Protocol)

### VRRP Configuration

| Command | Description |
|---------|-------------|
| `vrrp <group> ip <virtual-ip>` | Configure VRRP virtual IP |
| `vrrp <group> priority <1-254>` | Set priority (default 100) |
| `vrrp <group> preempt` | Enable preemption (default enabled) |
| `vrrp <group> timers advertise <seconds>` | Set advertisement interval |

### VRRP Configuration Example

```
! Router 1 (Master)
interface g0/0
 ip address 192.168.1.2 255.255.255.0
 vrrp 1 ip 192.168.1.1
 vrrp 1 priority 110

! Router 2 (Backup)
interface g0/0
 ip address 192.168.1.3 255.255.255.0
 vrrp 1 ip 192.168.1.1
```

### VRRP Show Commands

| Command | Description |
|---------|-------------|
| `show vrrp` | Display VRRP status |
| `show vrrp brief` | Display VRRP summary |

---

## GLBP (Gateway Load Balancing Protocol)

### GLBP Configuration

| Command | Description |
|---------|-------------|
| `glbp <group> ip <virtual-ip>` | Configure GLBP virtual IP |
| `glbp <group> priority <1-255>` | Set priority (default 100) |
| `glbp <group> preempt` | Enable preemption |
| `glbp <group> load-balancing <method>` | Set load-balancing method |

### GLBP Load Balancing Methods

| Method | Description |
|--------|-------------|
| `round-robin` | Rotate through AVFs (default) |
| `weighted` | Based on weighting |
| `host-dependent` | Based on client MAC |

### GLBP Configuration Example

```
! Both routers (AVG election based on priority)
interface g0/0
 ip address 192.168.1.2 255.255.255.0
 glbp 1 ip 192.168.1.1
 glbp 1 priority 110
 glbp 1 preempt
 glbp 1 load-balancing round-robin
```

### GLBP Show Commands

| Command | Description |
|---------|-------------|
| `show glbp` | Display GLBP status |
| `show glbp brief` | Display GLBP summary |

---

## FHRP Comparison

| Feature | HSRP | VRRP | GLBP |
|---------|------|------|------|
| **Active/Master** | Active | Master | AVG |
| **Standby/Backup** | Standby | Backup | AVF |
| **Default Priority** | 100 | 100 | 100 |
| **Preempt Default** | Disabled | Enabled | Disabled |
| **Load Balancing** | Manual | Manual | Automatic |
| **Groups (v1)** | 0-255 | 1-255 | 0-1023 |
| **Groups (v2)** | 0-4095 | - | - |

## HSRP States

1. **Initial** - Starting state
2. **Learn** - Waiting for hello from active
3. **Listen** - Receiving hellos
4. **Speak** - Participating in election
5. **Standby** - Backup router
6. **Active** - Forwarding traffic
