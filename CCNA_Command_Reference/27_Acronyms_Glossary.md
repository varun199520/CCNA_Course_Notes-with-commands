# CCNA Acronyms Glossary

---

## A

**AAA (Authentication, Authorization, Accounting):** A security framework that controls who can access the network (authentication), what they can do (authorization), and tracks their activities (accounting). Example: RADIUS server verifying user credentials.

**ABR (Area Border Router):** An OSPF router that connects two or more OSPF areas together. It maintains separate link-state databases for each area it belongs to. Example: A router connecting Area 0 to Area 10.

**ACE (Access Control Entry):** A single permit or deny statement within an access control list that defines what traffic is allowed or blocked. Example: `permit tcp any host 10.0.0.1 eq 80`

**ACL (Access Control List):** A set of rules applied to an interface that filters incoming or outgoing traffic based on criteria like source/destination IP, protocol, or port. Example: Standard ACL (1-99), Extended ACL (100-199).

**AD (Administrative Distance):** A number from 0-255 that indicates how trustworthy a routing source is. Lower values are more trusted. Example: Connected=0, Static=1, EIGRP=90, OSPF=110, RIP=120.

**AES (Advanced Encryption Standard):** A symmetric encryption algorithm that encrypts data in 128-bit blocks using keys of 128, 192, or 256 bits. It replaced DES and is used in WPA2/WPA3 wireless security.

**AH (Authentication Header):** An IPSec protocol that provides data integrity and authentication but not encryption. It uses protocol number 51 and protects the entire IP packet including the header.

**AP (Access Point):** A wireless networking device that allows Wi-Fi clients to connect to a wired network. It acts as a bridge between wireless and wired networks. Example: Cisco Aironet series.

**API (Application Programming Interface):** A set of protocols and tools that allows different software applications to communicate with each other. Example: REST APIs used for network automation.

**ARP (Address Resolution Protocol):** A protocol that maps a known IP address to a MAC address on a local network. When a device needs to send data, ARP finds the destination's MAC address. View with `show arp`.

**AS (Autonomous System):** A collection of networks under a single administrative domain that share a common routing policy. Identified by a unique AS number (1-65535). Used in BGP and EIGRP.

**ASBR (Autonomous System Boundary Router):** An OSPF router that connects the OSPF domain to external networks or other routing protocols. It redistributes routes between OSPF and other protocols.

**ASIC (Application-Specific Integrated Circuit):** A specialized chip designed for a specific task like packet forwarding. Switches use ASICs to forward traffic at wire speed without CPU involvement.

---

## B

**BGP (Border Gateway Protocol):** The routing protocol used between autonomous systems on the Internet. It is a path-vector protocol that makes routing decisions based on policies and AS paths. ISPs use BGP for peering.

**BPDU (Bridge Protocol Data Unit):** A message sent between switches in Spanning Tree Protocol containing information about bridge IDs, root bridge, and path costs. The root bridge sends BPDUs every 2 seconds.

**BRI (Basic Rate Interface):** An ISDN service providing two 64 kbps B channels for data and one 16 kbps D channel for signaling (2B+D). Total bandwidth is 128 kbps for data transmission.

**BSS (Basic Service Set):** The most basic wireless network topology consisting of one access point and its associated wireless clients. Example: A home Wi-Fi network with one router.

**BSSID (Basic Service Set Identifier):** The MAC address of an access point's radio interface. It uniquely identifies each BSS and is used by clients to associate with the correct AP.

---

## C

**CAM (Content Addressable Memory):** A type of memory in switches that stores the MAC address table. It allows extremely fast lookups by searching all entries simultaneously. View with `show mac address-table`.

**CAPWAP (Control and Provisioning of Wireless Access Points):** A protocol that enables a wireless LAN controller to manage multiple lightweight access points. Control traffic uses UDP 5246, data uses UDP 5247.

**CBWFQ (Class-Based Weighted Fair Queuing):** A QoS queuing mechanism that allows you to define traffic classes and assign each class a guaranteed minimum bandwidth during congestion.

**CDP (Cisco Discovery Protocol):** A Cisco proprietary Layer 2 protocol that discovers directly connected Cisco devices and gathers information about them. View neighbors with `show cdp neighbors`.

**CEF (Cisco Express Forwarding):** A Cisco switching technology that uses prebuilt forwarding tables (FIB) and adjacency tables for fast, hardware-based packet forwarding without CPU involvement.

**CHAP (Challenge Handshake Authentication Protocol):** A PPP authentication method where the server sends a challenge, and the client responds with a hash of the challenge and password. More secure than PAP because passwords are never sent.

**CIDR (Classless Inter-Domain Routing):** An IP addressing method that replaces classful addressing, allowing flexible subnet masks. Written as IP/prefix (e.g., 192.168.1.0/24). Helps conserve IP addresses.

**CLI (Command Line Interface):** A text-based interface for configuring and managing network devices by typing commands. Cisco IOS uses a hierarchical CLI with different modes (user, privileged, config).

**CoS (Class of Service):** A Layer 2 QoS marking stored in the 3-bit priority field of an 802.1Q VLAN tag. Values range from 0 (best effort) to 7 (highest priority).

**CRC (Cyclic Redundancy Check):** An error-detection code added to Ethernet frames. The receiver calculates its own CRC and compares it to detect transmission errors. High CRC errors indicate cable or noise problems.

**CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance):** The wireless access method where devices listen before transmitting and use techniques like RTS/CTS to avoid collisions. Used by 802.11 Wi-Fi.

**CSMA/CD (Carrier Sense Multiple Access with Collision Detection):** The Ethernet access method for half-duplex links where devices listen, transmit, detect collisions, and retransmit after a random backoff time.

---

## D

**DAI (Dynamic ARP Inspection):** A switch security feature that validates ARP packets against the DHCP snooping binding table. It prevents ARP spoofing and man-in-the-middle attacks.

**DCE (Data Communications Equipment):** In serial communications, the device that provides the clock signal. On back-to-back router connections, one side must be configured as DCE with `clock rate`.

**DHCP (Dynamic Host Configuration Protocol):** A protocol that automatically assigns IP addresses, subnet masks, default gateways, and DNS servers to network clients. Uses the DORA process (Discover, Offer, Request, Acknowledge).

**DH (Diffie-Hellman):** A key exchange algorithm that allows two parties to establish a shared secret over an insecure channel. Used in IPSec IKE Phase 1 to securely exchange encryption keys.

**DMVPN (Dynamic Multipoint VPN):** A Cisco VPN technology that allows dynamic creation of tunnels between spoke sites without going through the hub. Combines GRE tunnels, NHRP, and IPSec.

**DNS (Domain Name System):** A hierarchical system that translates human-readable domain names (www.cisco.com) into IP addresses. Uses UDP port 53 for queries, TCP 53 for zone transfers.

**DORA (Discover, Offer, Request, Acknowledge):** The four-step process a DHCP client uses to obtain an IP address. Client broadcasts Discover, server responds with Offer, client Requests, server Acknowledges.

**DoS (Denial of Service):** An attack that attempts to make a network resource unavailable by overwhelming it with traffic or exploiting vulnerabilities. Example: SYN flood attack.

**DR (Designated Router):** In OSPF multi-access networks, the router elected to represent the segment and reduce LSA flooding. The router with highest priority (or highest RID if tied) becomes DR.

**DSCP (Differentiated Services Code Point):** A 6-bit field in the IP header used for QoS marking. Values range from 0-63. Common values: EF (46) for voice, AF classes for data.

**DSL (Digital Subscriber Line):** A technology that delivers internet over existing telephone lines. Types include ADSL (asymmetric) and VDSL (very high speed).

**DTE (Data Terminal Equipment):** In serial communications, the device that receives the clock signal from the DCE. Typically the router side connected to a service provider's equipment.

**DTP (Dynamic Trunking Protocol):** A Cisco protocol that automatically negotiates trunk links between switches. Modes include auto, desirable, and nonegotiate.

**DUAL (Diffusing Update Algorithm):** The algorithm EIGRP uses to calculate loop-free routes. It identifies successor (best) and feasible successor (backup) routes.

---

## E

**EAP (Extensible Authentication Protocol):** A framework for authentication used in 802.1X. It supports multiple authentication methods like EAP-TLS, PEAP, and EAP-FAST.

**eBGP (External BGP):** BGP sessions between routers in different autonomous systems. eBGP peers are typically directly connected. Used for ISP peering and Internet routing.

**EF (Expedited Forwarding):** A DSCP per-hop behavior providing low delay, low jitter, and guaranteed bandwidth. Uses DSCP value 46. Typically used for voice traffic.

**EGP (Exterior Gateway Protocol):** A category of routing protocols used to route between autonomous systems. BGP is the only EGP currently used on the Internet.

**EIGRP (Enhanced Interior Gateway Routing Protocol):** A Cisco advanced distance-vector routing protocol that combines features of distance-vector and link-state protocols. AD=90, uses bandwidth and delay for metrics.

**ESP (Encapsulating Security Payload):** An IPSec protocol that provides confidentiality (encryption), data integrity, and authentication. Uses protocol number 50. More commonly used than AH.

**ESS (Extended Service Set):** A wireless network with multiple access points connected to the same wired network and sharing the same SSID. Enables seamless roaming between APs.

**EUI-64 (Extended Unique Identifier 64-bit):** A method to create a 64-bit IPv6 interface identifier from a 48-bit MAC address. Insert FFFE in the middle and flip the 7th bit.

---

## F

**FCS (Frame Check Sequence):** A 4-byte field at the end of an Ethernet frame containing the CRC value for error detection. The receiver calculates and compares to verify frame integrity.

**FD (Feasible Distance):** In EIGRP, the total calculated metric from the local router to a destination network through the successor (best path) route.

**FHRP (First Hop Redundancy Protocol):** A category of protocols that provide default gateway redundancy. Includes HSRP (Cisco), VRRP (IEEE), and GLBP (Cisco with load balancing).

**FIFO (First In, First Out):** The simplest queuing method where packets are forwarded in the exact order they arrive. No traffic prioritization. Default on high-speed interfaces.

**FTP (File Transfer Protocol):** A protocol for transferring files between systems over TCP. Uses port 21 for control (commands) and port 20 for data transfer.

**FQDN (Fully Qualified Domain Name):** The complete domain name that specifies a host's exact location in the DNS hierarchy. Example: www.cisco.com (includes host, domain, and TLD).

---

## G

**GBIC (Gigabit Interface Converter):** An older hot-swappable transceiver module for Gigabit Ethernet connections. Replaced by the smaller SFP form factor.

**GbE (Gigabit Ethernet):** Ethernet technology operating at 1000 Mbps (1 Gbps). Standards include 1000BASE-T (copper) and 1000BASE-SX/LX (fiber).

**GLBP (Gateway Load Balancing Protocol):** A Cisco FHRP that provides gateway redundancy and automatic load balancing across multiple routers using multiple virtual MAC addresses.

**GRE (Generic Routing Encapsulation):** A tunneling protocol that encapsulates packets inside IP packets. Supports multicast and routing protocols, often combined with IPSec for encryption.

**GUI (Graphical User Interface):** A visual interface with windows, icons, and menus for managing devices. Example: Cisco WLC web interface, ASDM for ASA.

---

## H

**HDLC (High-Level Data Link Control):** A Layer 2 WAN protocol and the default encapsulation on Cisco serial interfaces. Cisco's version is proprietary and incompatible with other vendors.

**HSRP (Hot Standby Router Protocol):** A Cisco FHRP where multiple routers share a virtual IP address. One router is active (forwards traffic), others are standby (ready to take over).

**HTTP (Hypertext Transfer Protocol):** The protocol for transferring web pages over the Internet. Uses TCP port 80. Sends data in plaintext.

**HTTPS (HTTP Secure):** HTTP encrypted with TLS for secure web communication. Uses TCP port 443. Provides confidentiality and server authentication.

---

## I

**iBGP (Internal BGP):** BGP sessions between routers within the same autonomous system. iBGP peers don't need to be directly connected. Requires full mesh or route reflectors.

**ICMP (Internet Control Message Protocol):** A Network layer protocol used for error reporting and diagnostics. Ping uses ICMP Echo Request/Reply. Traceroute uses ICMP Time Exceeded.

**IDF (Intermediate Distribution Frame):** A wiring closet in a building that connects to the MDF. Typically contains access layer switches serving nearby end users.

**IEEE (Institute of Electrical and Electronics Engineers):** An organization that creates networking standards. Examples: 802.3 (Ethernet), 802.11 (Wi-Fi), 802.1Q (VLANs).

**IGMP (Internet Group Management Protocol):** A protocol that manages multicast group membership on a local network. Hosts use IGMP to join or leave multicast groups.

**IGP (Interior Gateway Protocol):** A category of routing protocols used within a single autonomous system. Includes OSPF, EIGRP, RIP, and IS-IS.

**IKE (Internet Key Exchange):** The protocol IPSec uses to set up security associations. Phase 1 establishes a secure channel, Phase 2 negotiates IPSec parameters.

**IMAP (Internet Message Access Protocol):** An email retrieval protocol that keeps messages on the server. Uses TCP port 143 (or 993 with TLS). More features than POP3.

**IOS (Internetwork Operating System):** The operating system running on most Cisco routers and switches. Provides CLI for device configuration and management.

**IP (Internet Protocol):** The primary Network layer protocol responsible for addressing and routing packets across networks. IPv4 uses 32-bit addresses, IPv6 uses 128-bit addresses.

**IPSec (IP Security):** A framework of protocols for securing IP communications through encryption and authentication. Includes IKE, ESP, and AH. Used for VPNs.

**ISDN (Integrated Services Digital Network):** A digital telephone service. BRI provides 2B+D (128 kbps data), PRI provides 23B+D in North America (1.544 Mbps).

**IS-IS (Intermediate System to Intermediate System):** A link-state routing protocol similar to OSPF. Uses areas differently and runs directly over Layer 2. Common in large ISP networks.

**ISL (Inter-Switch Link):** A Cisco proprietary VLAN trunking protocol that encapsulates the entire frame. Obsolete, replaced by IEEE 802.1Q.

**ISP (Internet Service Provider):** A company that provides Internet connectivity to customers. Examples: Comcast, AT&T, Verizon.

---

## J-K

**JSON (JavaScript Object Notation):** A lightweight, human-readable data format used for API communication. Uses key-value pairs. Example: `{"hostname": "R1", "ip": "10.0.0.1"}`

**Kbps (Kilobits per second):** A unit of data transfer rate equal to 1,000 bits per second. 1 Mbps = 1,000 Kbps.

---

## L

**L2TP (Layer 2 Tunneling Protocol):** A VPN tunneling protocol that combines features of PPTP and L2F. Often paired with IPSec for encryption since L2TP doesn't encrypt by itself.

**LACP (Link Aggregation Control Protocol):** An IEEE 802.3ad protocol for negotiating EtherChannel links. Uses active/passive modes. Preferred over PAgP for multi-vendor environments.

**LAN (Local Area Network):** A network covering a small geographic area like an office, building, or campus. Characterized by high bandwidth and low latency.

**LAP (Lightweight Access Point):** An access point that relies on a wireless LAN controller for configuration, firmware, and intelligence. Cannot function independently.

**LDAP (Lightweight Directory Access Protocol):** A protocol for accessing and managing directory services. Used to query Active Directory or other LDAP directories for authentication.

**LLQ (Low Latency Queuing):** A QoS mechanism that combines CBWFQ with strict priority queuing. Provides guaranteed bandwidth and low delay for real-time traffic like voice.

**LLDP (Link Layer Discovery Protocol):** An IEEE 802.1AB vendor-neutral protocol for device discovery. Similar to CDP but works across different vendors. View with `show lldp neighbors`.

**LSA (Link State Advertisement):** A packet OSPF routers use to share routing information. Different types exist: Type 1 (Router), Type 2 (Network), Type 3 (Summary), etc.

**LSDB (Link State Database):** The database containing all LSAs in an OSPF area. All routers in an area have identical LSDBs. View with `show ip ospf database`.

**LSR (Label Switch Router):** A router in an MPLS network that forwards packets based on labels rather than IP addresses. Includes LER (edge) and LSR (core) routers.

---

## M

**MAC (Media Access Control):** A unique 48-bit hardware address assigned to network interfaces. Written in hexadecimal (e.g., 00:1A:2B:3C:4D:5E). Used for Layer 2 communication.

**MAN (Metropolitan Area Network):** A network spanning a city or metropolitan area, larger than LAN but smaller than WAN. Often connects multiple campus LANs.

**Mbps (Megabits per second):** A unit of data transfer rate equal to 1,000,000 bits per second. Fast Ethernet runs at 100 Mbps, Gigabit at 1000 Mbps.

**MD5 (Message Digest 5):** A hashing algorithm that produces a 128-bit hash value. Used for authentication in routing protocols (OSPF, EIGRP) and data integrity verification.

**MDF (Main Distribution Frame):** The central wiring point in a building where outside cables connect to internal cabling. Typically houses core network equipment.

**MIB (Management Information Base):** A hierarchical database of objects that can be monitored or configured via SNMP. Objects are identified by OIDs (Object Identifiers).

**MIMO (Multiple Input Multiple Output):** A wireless technology using multiple antennas to transmit and receive multiple data streams simultaneously. Key feature of 802.11n/ac/ax.

**MPLS (Multiprotocol Label Switching):** A WAN technology where routers forward packets based on labels instead of IP lookups. Commonly used by service providers for VPN services.

**MST (Multiple Spanning Tree):** An IEEE 802.1s STP mode that maps multiple VLANs to a reduced number of STP instances. More efficient than PVST+ for large VLAN deployments.

**MTU (Maximum Transmission Unit):** The largest packet size that can be transmitted over a network without fragmentation. Standard Ethernet MTU is 1500 bytes.

**MQC (Modular QoS CLI):** Cisco's framework for configuring QoS using three components: class-map (classify traffic), policy-map (define actions), and service-policy (apply to interface).

---

## N

**NAC (Network Access Control):** A security approach that checks endpoint compliance before allowing network access. Verifies antivirus, patches, and security posture. Example: Cisco ISE.

**NAT (Network Address Translation):** A technique that modifies IP addresses in packet headers, typically to allow private addresses to communicate over the Internet using public addresses.

**NBI (Northbound Interface):** In SDN, the API between the controller and applications. Allows applications to request network services. Typically uses REST APIs.

**NETCONF (Network Configuration Protocol):** A network management protocol that uses XML for configuration data and runs over SSH. Uses TCP port 830. Supports transactions and validation.

**NIC (Network Interface Card):** Hardware that connects a computer to a network. Contains the MAC address and handles Layer 1 and Layer 2 functions.

**NMS (Network Management System):** Software that monitors and manages network devices. Collects SNMP data, generates alerts, and provides dashboards. Example: Cisco Prime.

**NTP (Network Time Protocol):** A protocol that synchronizes clocks across network devices. Uses UDP port 123. Stratum indicates distance from reference clock (0 = atomic clock).

**NVRAM (Non-Volatile Random Access Memory):** Memory that retains contents when power is lost. Stores the startup-config file on Cisco devices.

---

## O

**OFDM (Orthogonal Frequency Division Multiplexing):** A modulation technique that splits data across multiple subcarrier frequencies. Used by 802.11a/g/n/ac for efficient wireless transmission.

**OID (Object Identifier):** A unique identifier for an object in an SNMP MIB. Written as a series of numbers (e.g., 1.3.6.1.2.1.1.5 for sysName).

**OSI (Open Systems Interconnection):** A seven-layer reference model for networking: Physical, Data Link, Network, Transport, Session, Presentation, Application.

**OSPF (Open Shortest Path First):** A link-state IGP that uses Dijkstra's SPF algorithm to calculate best paths. AD=110. Uses areas for scalability. Supports VLSM and fast convergence.

**OUI (Organizationally Unique Identifier):** The first three bytes (24 bits) of a MAC address assigned by IEEE to identify the manufacturer.

---

## P

**PAgP (Port Aggregation Protocol):** A Cisco proprietary protocol for negotiating EtherChannel links. Uses desirable/auto modes. Only works between Cisco devices.

**PAP (Password Authentication Protocol):** A PPP authentication method that sends username and password in cleartext. Insecure compared to CHAP.

**PAT (Port Address Translation):** A form of NAT that maps multiple private IP addresses to a single public IP address using different port numbers. Also called NAT overload.

**PDU (Protocol Data Unit):** The name for data at each OSI layer: Data (L5-7), Segment (L4), Packet (L3), Frame (L2), Bits (L1).

**PEAP (Protected EAP):** An 802.1X authentication method that creates a TLS tunnel to protect credentials. The inner authentication can use MS-CHAPv2 or other methods.

**PIM (Protocol Independent Multicast):** A multicast routing protocol that works with any unicast routing protocol. Modes include Sparse Mode (PIM-SM) and Dense Mode (PIM-DM).

**PoE (Power over Ethernet):** Technology that delivers DC power over Ethernet cables along with data. IEEE 802.3af provides 15.4W, 802.3at provides 25.5W, 802.3bt provides up to 90W.

**POP3 (Post Office Protocol version 3):** An email retrieval protocol that downloads messages from server to client. Uses TCP port 110 (or 995 with TLS). Simpler than IMAP.

**PPP (Point-to-Point Protocol):** A Layer 2 WAN protocol for serial links that supports authentication (PAP/CHAP), error detection, and multilink. More feature-rich than HDLC.

**PPPoE (PPP over Ethernet):** A protocol for encapsulating PPP frames within Ethernet frames. Commonly used for DSL connections to provide authentication and session management.

**PRI (Primary Rate Interface):** An ISDN service providing 23 B channels and 1 D channel (23B+D) in North America, or 30B+D in Europe. Runs over T1/E1 lines.

**PSK (Pre-Shared Key):** A shared secret used for authentication. In Wi-Fi (WPA2-Personal), all users share the same PSK to connect to the network.

**PVST (Per-VLAN Spanning Tree):** A Cisco STP mode that runs a separate spanning tree instance for each VLAN. Allows per-VLAN load balancing but uses more CPU and bandwidth.

---

## Q

**QoS (Quality of Service):** Network techniques and technologies that prioritize certain types of traffic to ensure performance. Involves classification, marking, queuing, and scheduling.

---

## R

**RADIUS (Remote Authentication Dial-In User Service):** An AAA protocol that centralizes authentication for network access. Uses UDP ports 1812/1813. Encrypts only the password.

**RAM (Random Access Memory):** Volatile memory that loses contents when power is lost. Stores running-config, routing tables, and ARP cache on Cisco devices.

**RD (Reported Distance):** In EIGRP, the metric advertised by a neighbor to reach a destination. Used in the feasibility condition to identify loop-free backup routes.

**REST (Representational State Transfer):** An API architectural style using HTTP methods (GET, POST, PUT, DELETE) to perform CRUD operations on resources.

**RFC (Request for Comments):** Documents published by IETF that define Internet standards and protocols. Example: RFC 1918 defines private IP address ranges.

**RID (Router ID):** A unique 32-bit identifier for a router in OSPF or EIGRP. Usually the highest loopback IP or highest physical interface IP. Can be manually configured.

**RIP (Routing Information Protocol):** A distance-vector IGP that uses hop count as its metric. Maximum 15 hops, AD=120. Simple but slow convergence. RIPv2 supports VLSM.

**ROAS (Router on a Stick):** An inter-VLAN routing method using a single router interface with multiple sub-interfaces, each assigned to a different VLAN with 802.1Q encapsulation.

**ROM (Read-Only Memory):** Non-volatile memory containing the bootstrap program (bootstrap loader) and basic diagnostic software (POST).

**ROMMON (ROM Monitor):** A low-level operating mode used for password recovery and system recovery when IOS fails to load.

**RPF (Reverse Path Forwarding):** A multicast technique that verifies packets arrive on the interface used to reach the source. Prevents multicast loops.

**RSTP (Rapid Spanning Tree Protocol):** IEEE 802.1w, an evolution of STP with faster convergence (seconds vs. 30-50 seconds). Uses port roles and link types for quick transitions.

**RTP (Real-time Transport Protocol):** A protocol for delivering audio and video over IP networks. Provides sequencing and timing. Works with RTCP for quality feedback.

---

## S

**SA (Security Association):** A one-way connection in IPSec that defines security parameters (encryption, authentication, keys). Identified by SPI, destination IP, and protocol.

**SAE (Simultaneous Authentication of Equals):** The WPA3 authentication method that replaces PSK handshake. Provides protection against offline dictionary attacks even if password is weak.

**SBI (Southbound Interface):** In SDN, the interface between the controller and network devices. Protocols include OpenFlow, NETCONF, and RESTCONF.

**SDN (Software-Defined Networking):** A network architecture that separates the control plane from the data plane, centralizing intelligence in a controller. Examples: Cisco ACI, DNA Center.

**SFP (Small Form-factor Pluggable):** A compact, hot-swappable transceiver for Gigabit Ethernet and Fibre Channel. Smaller successor to GBIC. SFP+ supports 10 Gbps.

**SHA (Secure Hash Algorithm):** A family of cryptographic hash functions. SHA-256 produces a 256-bit hash and is commonly used for data integrity verification.

**SLAAC (Stateless Address Autoconfiguration):** An IPv6 method where hosts automatically configure their addresses using Router Advertisement messages and EUI-64. No DHCP server needed.

**SMTP (Simple Mail Transfer Protocol):** The protocol for sending email between servers. Uses TCP port 25 (or 587 for submission). Only handles sending, not receiving.

**SNMP (Simple Network Management Protocol):** A protocol for monitoring and managing network devices. Agent listens on UDP 161, traps sent to UDP 162. Versions: v1, v2c (community strings), v3 (encryption).

**SPF (Shortest Path First):** The Dijkstra algorithm OSPF uses to calculate the shortest path tree from the LSDB. Each router calculates its own SPF tree.

**SPI (Security Parameter Index):** A 32-bit identifier in an IPSec packet header that identifies which security association to use for processing.

**SSH (Secure Shell):** A protocol for secure remote access to network devices. Uses TCP port 22. Encrypts all traffic including passwords. Replaces Telnet.

**SSID (Service Set Identifier):** The name of a wireless network that clients use to identify and connect. Can be broadcast or hidden.

**SSL (Secure Sockets Layer):** An older encryption protocol for securing Internet communications. Deprecated and replaced by TLS due to security vulnerabilities.

**STP (Spanning Tree Protocol):** IEEE 802.1D protocol that prevents Layer 2 loops by blocking redundant paths. Elects a root bridge and determines port states.

**SVI (Switch Virtual Interface):** A virtual Layer 3 interface on a switch representing a VLAN. Used for inter-VLAN routing and switch management. Created with `interface vlan`.

---

## T

**TACACS+ (Terminal Access Controller Access Control System Plus):** A Cisco AAA protocol using TCP port 49. Encrypts entire payload. Separates authentication, authorization, and accounting.

**TCP (Transmission Control Protocol):** A connection-oriented Transport layer protocol providing reliable, ordered delivery. Uses three-way handshake and acknowledgments.

**TCAM (Ternary Content Addressable Memory):** Specialized memory that can store and search three states (0, 1, don't care). Used for fast ACL and routing table lookups.

**TFTP (Trivial File Transfer Protocol):** A simple file transfer protocol using UDP port 69. No authentication. Used for transferring IOS images and configurations.

**TLS (Transport Layer Security):** The modern encryption protocol for securing Internet communications. Successor to SSL. Used by HTTPS, secure email, and VPNs.

**ToS (Type of Service):** An 8-bit field in the IPv4 header originally used for QoS. Redefined as DSCP (6 bits) and ECN (2 bits).

**TTL (Time to Live):** An IP header field that limits packet lifetime by decreasing by 1 at each hop. Prevents infinite routing loops. When TTL reaches 0, packet is discarded.

---

## U

**UDP (User Datagram Protocol):** A connectionless Transport layer protocol providing fast, unreliable delivery. No handshake or acknowledgments. Used by DNS, DHCP, TFTP, SNMP.

**UTP (Unshielded Twisted Pair):** Common copper cabling for Ethernet. Categories include Cat5e (1 Gbps), Cat6 (1-10 Gbps), Cat6a (10 Gbps at 100m).

---

## V

**VACL (VLAN Access Control List):** An ACL applied to VLAN traffic within a switch. Filters traffic regardless of whether it's routed or bridged.

**VLAN (Virtual Local Area Network):** A logical grouping of switch ports into separate broadcast domains. Improves security, performance, and management. Identified by VLAN ID (1-4094).

**VLSM (Variable Length Subnet Mask):** A subnetting technique that allows different subnet masks within the same network. Efficiently allocates IP addresses based on actual need.

**VoIP (Voice over IP):** Technology for transmitting voice communications over IP networks. Converts analog voice to digital packets. Used by IP phones and softphones.

**VPN (Virtual Private Network):** A secure, encrypted tunnel over a public network like the Internet. Types include site-to-site (connecting offices) and remote-access (connecting users).

**VRF (Virtual Routing and Forwarding):** A technology that creates multiple separate routing tables on a single router. Used for network segmentation and MPLS VPNs.

**VRRP (Virtual Router Redundancy Protocol):** An IEEE standard (RFC 5798) FHRP similar to HSRP. Uses master/backup terminology. Preemption enabled by default.

**VTP (VLAN Trunking Protocol):** A Cisco protocol that synchronizes VLAN information across switches. Modes: Server, Client, Transparent. Be careful—deleting VLANs on server affects all clients.

**VTY (Virtual Terminal Line):** Virtual lines used for remote access (SSH/Telnet) to network devices. Configure access with `line vty 0 15`.

---

## W

**WAN (Wide Area Network):** A network spanning large geographic distances, connecting LANs in different locations. Technologies include MPLS, leased lines, and Internet VPNs.

**WAP (Wireless Access Point):** Same as AP—a device that provides wireless connectivity to a network.

**WEP (Wired Equivalent Privacy):** An obsolete wireless security protocol with serious vulnerabilities. Uses RC4 encryption with weak key management. Never use WEP.

**WFQ (Weighted Fair Queuing):** A QoS queuing method that fairly allocates bandwidth based on traffic flows and IP precedence. Gives low-volume flows priority over high-volume flows.

**Wi-Fi (Wireless Fidelity):** Marketing name for IEEE 802.11 wireless LAN technology. Wi-Fi 4 = 802.11n, Wi-Fi 5 = 802.11ac, Wi-Fi 6 = 802.11ax.

**WLAN (Wireless Local Area Network):** A local area network using wireless technology (802.11) instead of or in addition to wired connections.

**WLC (Wireless LAN Controller):** A device that centrally manages and configures lightweight access points. Handles roaming, security policies, and RF management.

**WPA (Wi-Fi Protected Access):** A wireless security standard. WPA2 uses AES-CCMP encryption. WPA3 adds SAE authentication and improved security.

---

## X-Y-Z

**XML (Extensible Markup Language):** A markup language for encoding structured data. Uses tags and attributes. Used by NETCONF for network device configuration.

**YAML (YAML Ain't Markup Language):** A human-readable data format using indentation. Popular for configuration files. Used in Ansible playbooks and Kubernetes.

---

## IEEE 802 Standards

**802.1D:** Original Spanning Tree Protocol standard.

**802.1Q:** VLAN tagging standard for trunk links. Adds 4-byte tag to Ethernet frame.

**802.1s:** Multiple Spanning Tree (MST) standard.

**802.1w:** Rapid Spanning Tree Protocol (RSTP) standard.

**802.1X:** Port-based network access control standard for authentication.

**802.3:** Ethernet standard family.

**802.3af:** Power over Ethernet (PoE) providing up to 15.4W per port.

**802.3at:** PoE+ providing up to 25.5W per port.

**802.3bt:** PoE++ providing up to 90W per port.

**802.11:** Wireless LAN standard family.

**802.11a:** 5 GHz band, up to 54 Mbps, OFDM modulation.

**802.11b:** 2.4 GHz band, up to 11 Mbps, DSSS modulation.

**802.11g:** 2.4 GHz band, up to 54 Mbps, OFDM modulation.

**802.11n (Wi-Fi 4):** Dual-band, up to 600 Mbps, MIMO technology.

**802.11ac (Wi-Fi 5):** 5 GHz band, up to 6.9 Gbps, MU-MIMO, wider channels.

**802.11ax (Wi-Fi 6):** Dual-band, improved efficiency, OFDMA, better in dense environments.
