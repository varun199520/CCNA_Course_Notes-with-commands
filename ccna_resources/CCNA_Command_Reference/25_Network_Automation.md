# Network Automation Commands

## Network Planes

| Plane | Function | Examples |
|-------|----------|----------|
| **Data Plane** | Forwards traffic | Switching, routing, NAT |
| **Control Plane** | Learns routes, builds tables | OSPF, STP, ARP |
| **Management Plane** | Manages device | SSH, SNMP, Syslog |

---

## REST API Concepts

### HTTP Methods (CRUD)

| Method | CRUD | Description |
|--------|------|-------------|
| GET | Read | Retrieve data |
| POST | Create | Create new resource |
| PUT | Update/Replace | Replace entire resource |
| PATCH | Update/Modify | Modify part of resource |
| DELETE | Delete | Remove resource |

### HTTP Status Codes

| Code | Description |
|------|-------------|
| 200 | OK - Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 403 | Forbidden |
| 404 | Not Found |
| 500 | Internal Server Error |

---

## JSON Format

### JSON Syntax

```json
{
  "hostname": "R1",
  "interfaces": [
    {
      "name": "GigabitEthernet0/0",
      "ip_address": "192.168.1.1",
      "enabled": true
    },
    {
      "name": "GigabitEthernet0/1",
      "ip_address": "10.0.0.1",
      "enabled": false
    }
  ],
  "vlans": [10, 20, 30]
}
```

### JSON Data Types

| Type | Example |
|------|---------|
| String | `"hostname": "R1"` |
| Number | `"vlan": 10` |
| Boolean | `"enabled": true` |
| Null | `"description": null` |
| Array | `"vlans": [10, 20, 30]` |
| Object | `{"name": "Gi0/0"}` |

---

## XML Format

### XML Syntax

```xml
<?xml version="1.0" encoding="UTF-8"?>
<device>
  <hostname>R1</hostname>
  <interfaces>
    <interface>
      <name>GigabitEthernet0/0</name>
      <ip_address>192.168.1.1</ip_address>
      <enabled>true</enabled>
    </interface>
  </interfaces>
</device>
```

---

## YAML Format

### YAML Syntax

```yaml
hostname: R1
interfaces:
  - name: GigabitEthernet0/0
    ip_address: 192.168.1.1
    enabled: true
  - name: GigabitEthernet0/1
    ip_address: 10.0.0.1
    enabled: false
vlans:
  - 10
  - 20
  - 30
```

---

## Configuration Management Tools

| Tool | Language | Agent | Push/Pull |
|------|----------|-------|-----------|
| Ansible | Python/YAML | Agentless | Push |
| Puppet | Ruby | Agent | Pull |
| Chef | Ruby | Agent | Pull |
| SaltStack | Python | Agent/Agentless | Push/Pull |

---

## Cisco DNA Center APIs

### DNA Center REST API

| Endpoint | Method | Description |
|----------|--------|-------------|
| /dna/intent/api/v1/network-device | GET | List devices |
| /dna/intent/api/v1/site | GET | List sites |
| /dna/intent/api/v1/topology | GET | Get topology |

---

## SDN Controllers

### Southbound Interfaces (SBI)

| Protocol | Description |
|----------|-------------|
| OpenFlow | Flow-based forwarding |
| NETCONF | XML-based config |
| RESTCONF | REST-based config |
| OnePK | Cisco proprietary |

### Northbound Interfaces (NBI)

| Type | Description |
|------|-------------|
| REST API | HTTP-based |
| Python SDK | Native libraries |

---

## NETCONF/RESTCONF

### NETCONF

| Feature | Description |
|---------|-------------|
| Protocol | SSH (TCP 830) |
| Data Format | XML |
| Operations | get, get-config, edit-config, copy-config, delete-config, lock, unlock |

### RESTCONF

| Feature | Description |
|---------|-------------|
| Protocol | HTTPS |
| Data Format | JSON or XML |
| Methods | GET, POST, PUT, PATCH, DELETE |

### Enable NETCONF/RESTCONF on IOS-XE

```
! Enable NETCONF
netconf-yang

! Enable RESTCONF
restconf
ip http secure-server
```

---

## Python for Network Automation

### Common Libraries

| Library | Purpose |
|---------|---------|
| Netmiko | SSH connections |
| Paramiko | Low-level SSH |
| NAPALM | Multi-vendor abstraction |
| Nornir | Automation framework |
| requests | REST API calls |

### Netmiko Example

```python
from netmiko import ConnectHandler

device = {
    'device_type': 'cisco_ios',
    'host': '192.168.1.1',
    'username': 'admin',
    'password': 'password'
}

connection = ConnectHandler(**device)
output = connection.send_command('show ip interface brief')
print(output)
connection.disconnect()
```

### REST API Example

```python
import requests

url = "https://sandboxdnac.cisco.com/api/v1/network-device"
headers = {
    "X-Auth-Token": "your-token",
    "Content-Type": "application/json"
}

response = requests.get(url, headers=headers, verify=False)
print(response.json())
```

---

## Cisco IOS-XE Commands for Automation

| Command | Description |
|---------|-------------|
| `netconf-yang` | Enable NETCONF |
| `restconf` | Enable RESTCONF |
| `ip http secure-server` | Enable HTTPS |
| `show netconf-yang sessions` | Display NETCONF sessions |
| `show platform software yang-management process` | Display YANG status |
