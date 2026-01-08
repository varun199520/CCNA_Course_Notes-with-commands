[README.md](https://github.com/user-attachments/files/24484801/README.md)
# CCNA Resources

A comprehensive collection of CCNA (Cisco Certified Network Associate) study materials including detailed course notes and a command reference guide.

## 📁 Folder Structure

### CCNA_Command_Reference/
A quick-reference guide containing all essential Cisco IOS commands organized by topic:
- Basic device configuration
- Interface & VLAN configuration
- Routing protocols (OSPF, EIGRP, RIP, Static)
- Switching (STP, EtherChannel)
- Security (ACLs, Port Security, SSH)
- Services (DHCP, NAT, NTP, SNMP)
- Troubleshooting commands
- And more...

### CCNA_Course_Notes/
In-depth study notes covering the complete CCNA curriculum:
- Network fundamentals (OSI model, TCP/IP)
- LAN switching technologies
- IPv4 and IPv6 addressing & subnetting
- Routing concepts and protocols
- WAN technologies
- Network security
- Wireless networking
- Automation and programmability

---

## 🤖 Using with AI Assistants (Windsurf/Cursor)

These resources are designed to work as **context** for AI-powered coding assistants like **Windsurf** or **Cursor AI**. This allows you to ask networking questions and get accurate answers based on CCNA knowledge.

### Setup Instructions

1. **Open the folder in your AI IDE**
   - In Windsurf/Cursor, open the `ccna_resources` folder as your workspace
   - Or add it to an existing workspace

2. **Reference files in your prompts**
   - Use `@` mentions to include specific files as context
   - Example: `@CCNA_Command_Reference/07_OSPF.md` 

3. **Use the AI chat to ask questions**

### Example Prompts

#### Command Lookup
```
What is the command to configure OSPF on a Cisco router? 
Use @CCNA_Command_Reference as reference.
```

#### Concept Explanation
```
Explain how Spanning Tree Protocol prevents loops. 
Reference @CCNA_Course_Notes/Course_Notes/Spanning_Tree_Protocol_Part1.md
```

#### Troubleshooting Help
```
My OSPF neighbors aren't forming. What should I check? 
Use the OSPF notes as context.
```

#### Configuration Examples
```
Show me how to configure inter-VLAN routing with 
Router-on-a-Stick. Use the VLAN notes.
```

#### Study & Review
```
Quiz me on subnetting concepts based on the subnetting notes.
```

### Pro Tips

1. **Index the whole folder** - Let the AI index all files for comprehensive answers
2. **Be specific** - Reference specific files for more accurate responses
3. **Ask for commands + explanations** - The command reference has syntax, the course notes have theory
4. **Use for lab prep** - Ask the AI to generate practice scenarios based on the notes
5. **Cross-reference** - Ask questions that combine multiple topics

---

## 📚 Topics Covered

| Category | Topics |
|----------|--------|
| **Fundamentals** | OSI Model, TCP/IP, Ethernet, Cables & Interfaces |
| **Switching** | VLANs, STP, RSTP, EtherChannel, DTP, VTP |
| **Routing** | Static Routing, OSPF, EIGRP, RIP, IPv6 |
| **IP Services** | DHCP, DNS, NAT, NTP, SNMP, Syslog, FTP/TFTP |
| **Security** | ACLs, Port Security, DHCP Snooping, DAI, SSH |
| **Wireless** | Fundamentals, Architectures, Security, Configuration |
| **WAN** | WAN Architectures, VPNs |
| **Automation** | SDN, REST APIs, JSON/XML/YAML, Ansible/Puppet/Chef |
| **Infrastructure** | QoS, FHRP (HSRP/VRRP/GLBP), Virtualization, Cloud |

---

## 🎯 Best Use Cases

- **Quick command lookup** during lab practice
- **Concept review** before exams
- **Troubleshooting guidance** for network issues
- **Configuration templates** for common scenarios
- **Study companion** with AI-powered Q&A

---

*These notes are based on the CCNA 200-301 exam objectives.*
