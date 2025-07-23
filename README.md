# Networking Guide

## **🧠 Purpose of Networks — Quick Reference**

### **🔗 What is a Network?**

- A **network** is a group of interconnected devices (computers, phones, IoT, etc.) that communicate and share data.
- Two main connection types:
    - **Wired:** e.g., Ethernet cables (CAT5, CAT6, RJ45)
    - **Wireless:** e.g., Wi-Fi (WLAN), Cellular (LTE/5G)

### **🌍 Types of Networks (by scope)**

| **Type** | **Acronym** | **Description** |
| --- | --- | --- |
| Personal Area Network | **PAN** | Very short-range (e.g., Bluetooth game controller) |
| Local Area Network | **LAN** | Home or office-level network |
| Campus Area Network | **CAN** | Connects multiple LANs within a campus |
| Metropolitan Area Network | **MAN** | Covers a city or metro region |
| Wide Area Network | **WAN** | Covers large geographic areas (national/global); often uses the internet + **VPN** for secure data transfer |

---

### **✅ Benefits of Networking**

- **Resource Sharing:** Printers, files, servers
- **Communication:** Email, VoIP, video conferencing
- **Redundancy & Backups:** Off-site or cloud data protection
- **Internet Access:** Global connectivity
- **Device Monitoring:** Alerts from smart devices or equipment
- **Centralized Management:** Remote configuration and updates

---

### **💡 Everyday Use Cases**

- Streaming (Hulu, YouTube), cloud DVRs
- Video/audio calls (Skype, Zoom)
- Social media, web browsing
- **IoT devices:** Smart thermostats, fridges, lights, doorbells, etc.
- **Voice assistants:** Amazon Alexa & home automation

---

### **🛠️ Key Technologies**

- **VoIP** = Voice over IP
- **VPN** = Virtual Private Network
- **IoT** = Internet of Things
- **WLAN** = Wireless Local Area Network

---

## **🧠 Network Addresses — Quick Reference**

### **🔒 MAC Address (Physical Address)**

- **Definition:** A **48-bit hardware address** assigned at manufacture (also called **burned-in address**).
- **Structure:**
    - First 24 bits: **OUI** (Organizationally Unique Identifier / Vendor Code)
    - Last 24 bits: Unique to device
- **Use Case:** Switches use MAC addresses to forward data within a LAN.

---

### **🌐 IPv4 Address (Logical Address)**

- **Definition:** A **32-bit software-assigned** address used for routing over IP networks.
- **Format:** Dotted decimal notation (e.g., 192.168.1.1)
    - Divided into **4 octets** (8 bits each)
- **Address Parts:**
    - **Network portion** (e.g., street name)
    - **Host portion** (e.g., house number)
    - **Subnet mask** separates these two (e.g., /16 means first 16 bits = network)
- **Limitation:** IPv4 space is exhausted.
- **Solution:** **NAT** (Network Address Translation) allows multiple private devices to share one public IP.

---

### **🧮 IPv6 Address (Logical Address)**

- **Definition:** A **128-bit** address designed to replace IPv4.
- **Format:** 8 **quartets** (4 hexadecimal digits each), e.g.:

```
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

- **Notation:**
    - Uses **hexadecimal** digits (0–9, A–F)
    - **Prefix length** (e.g., /64) replaces subnet mask
        - /64 = first 64 bits = network prefix
        - last 64 bits = host identifier
- **Scalability:** 2¹²⁸ possible addresses — enough for every device globally

---

### **🛠️ Key Terms**

| **Term** | **Meaning** |
| --- | --- |
| **MAC Address** | Physical address, 48-bit, set by manufacturer |
| **IPv4** | Logical, 32-bit address, uses subnet mask |
| **IPv6** | Logical, 128-bit address, uses prefix length |
| **OUI** | Organizationally Unique Identifier (first 24 bits of MAC) |
| **NAT** | Network Address Translation — allows multiple devices to share one IP |
| **Octet** | 8-bit IPv4 segment |
| **Quartet** | 16-bit IPv6 segment in hexadecimal |

---

## **🧠 Network Parts — Quick Reference**

### **💻 Network Interface Card (NIC)**

- **Function:** Hardware enabling devices to connect to wired/wireless networks.
- **Types:**
    - **Internal NIC:** Built-in or slotted into a PC.
    - **External NIC:** USB-based, e.g., USB-C to Ethernet adapter.
- **Wired vs. Wireless:** Some laptops may have only wireless NICs.

---

### **🔀 Switch**

- **Role:** Connects multiple devices in a LAN and forwards **frames** based on MAC addresses.
- **MAC Address Table:**
    - Learns MAC ↔ Port mappings.
    - Unknown destination = **floods** frame to all ports (except source port).
- **Intelligent Forwarding:** Once learned, frames are forwarded only to correct port.

---

### **🌐 Router**

- **Function:** Connects multiple networks and routes **packets** based on IP addresses.
- **Routing Table:**
    - Directly connected networks added automatically.
    - Can use routing protocols (e.g., **OSPF**) to exchange routes.
    - **Default Route** (0.0.0.0/0): Used when no specific match is found.
- **Longest Prefix Match:** Chooses route with the most specific subnet mask.

---

### **📡 Wireless Access Point (WAP / AP)**

- **Use Case:** Expands wireless coverage.
- **Not a Router:** Connects to an Ethernet switch, not directly to the internet.
- **Roaming:** Clients auto-switch to the strongest AP signal while moving.

---

### **🧵 Copper Cabling**

- **Type:** Twisted Pair (UTP or STP)
- **Shielding:**
    - **UTP:** No shielding
    - **STP:** Foil/braided shielding for interference-heavy environments
- **Plenum-Rated Cables:** Safe for airflow spaces (no toxic fumes)
- **Standards:**
    - **Connectors:** RJ-45 (8 pins)
    - **Wiring Schemes:** T568A / T568B (use consistently)
    - **Categories:**

| **Cat** | **Max Speed** | **Max Distance** |
| --- | --- | --- |
| 5e | 1 Gbps | 100 m |
| 6 | 10 Gbps | 55 m |
| 6a+ | 10 Gbps+ | 100 m |

---

### **🔦 Fiber Optic Cabling**

- **Medium:** Uses **light** (laser/LED), immune to electromagnetic interference
- **Better for:** Long distances, high-speed backbone links
- **Types:**

| **Type** | **Core Size** | **Mode** | **Use Case** |
| --- | --- | --- | --- |
| **SMF** | Small (single mode) | 1 path | Long-distance, high-precision |
| **MMF** | Larger (multi mode) | Many paths | Short-distance, cheaper |

- **Distortion:** MMF may suffer **modal dispersion** (signal overlap)
- **Structure:**
    - **Core:** Carries light
    - **Cladding:** Reflects light internally (different refractive index)

---

### **📌 Key Takeaways**

| **Component** | **Forwarding Based On** | **Protocol Unit** | **Role** |
| --- | --- | --- | --- |
| **NIC** | N/A | Bits/Frames | Connects device to network |
| **Switch** | MAC Address | Frame | Connects devices in LAN |
| **Router** | IP Address | Packet | Connects networks |
| **WAP** | Signal Strength | Frame | Extends wireless coverage |
| **Copper** | Electrical Signals | N/A | Common for LAN wiring |
| **Fiber** | Light Signals | N/A | Long-distance high-speed |

---

## **🧠 OSI Model & Protocols — Quick Reference**

### **📚 The 7 OSI Layers**

### **(Bottom → Top)**

| **Layer** | **Name** | **Description** | **Data Unit** | **Key Examples** |
| --- | --- | --- | --- | --- |
| 7 | Application | User-level interface (HTTP, DNS, etc.) | — | HTTP, HTTPS, DNS, NTP |
| 6 | Presentation | Data formatting, compression, encryption | — | JPEG, SSL/TLS, MP3 |
| 5 | Session | Manages sessions (start, maintain, end) | — | API sessions, RPC |
| 4 | Transport | End-to-end delivery, reliability (TCP/UDP) | Segments | TCP, UDP |
| 3 | Network | Logical addressing & routing | Packets | IP, ICMP, Routers |
| 2 | Data Link | Physical addressing (MAC) & frame delivery | Frames | Ethernet, Switches, MAC addresses |
| 1 | Physical | Physical media & signals | Bits | Cables, radio waves, NICs |

---

### **🔄 TCP/IP vs OSI Model**

| **TCP/IP Layer** | **Corresponds to OSI Layers** |
| --- | --- |
| Application | Layers 5–7 (Application, Presentation, Session) |
| Transport | Layer 4 (TCP, UDP) |
| Internet | Layer 3 (IP, ICMP) |
| Network Access | Layers 1–2 (Physical + Data Link) |
- **Variants:**
    - “Network Access” also called *Link Layer* or *Network Interface Layer*
    - Some models show **5 layers** (splitting Physical and Data Link)

---

### **🌐 Key Application Layer Protocols**

| **Protocol** | **Transport** | **Port(s)** | **Function** |
| --- | --- | --- | --- |
| **HTTP** | TCP | 80 | Web browsing |
| **HTTPS** | TCP | 443 | Secure web browsing (TLS) |
| **DNS** | TCP/UDP | 53 | Name → IP resolution |
| **NTP** | UDP | 123 | Time sync across devices |
| **DHCP** | UDP | 67 | Auto IP address assignment |

---

### **📌 Key Points**

- **TCP = Reliable**, connection-oriented, slower
- **UDP = Unreliable**, connectionless, faster
- **Layer 4** uses TCP/UDP to deliver **segments** to specific ports
- **Layer 7** protocols rely on these ports to identify services

---

## **🧠 Network Services — Quick Reference**

### **📦 DHCP (Dynamic Host Configuration Protocol)**

| **Purpose** | **Automatically assigns IP config to devices** |
| --- | --- |
| Port | UDP 67 (server), UDP 68 (client) |
| Process (DORA) | Discover → Offer → Request → Acknowledge |
| Requires DHCP Relay | If client/server are on different subnets |
- **DHCPv6 Modes:**
    - **Stateful:** DHCPv6 server assigns full address (prefix + host)
    - **Stateless:** Router assigns prefix (via **NDP**), DHCPv6 gives extras (e.g., DNS)

---

### **🌐 DNS (Domain Name System)**

| **Purpose** | **Resolves domain names to IP addresses** |
| --- | --- |
| Port(s) | UDP & TCP 53 |
| Example Workflow | PC queries DNS → DNS responds with IP |
| Integration | DNS server info often learned via DHCP |
- Without DNS, routers can’t forward to hostnames — only IPs are routable.

---

### **🔁 NAT (Network Address Translation)**

| **Purpose** | **Converts private IPs → public IPs** |
| --- | --- |
| Type | **Dynamic NAT** (uses a pool of public IPs) |
| Internal Terminology |  |
|  | Inside Local: private IP (e.g., 10.0.0.1) |
|  | Inside Global: public IP (e.g., 192.0.2.1) |
- Enables reuse of private IPs across many orgs
- Translation tables stored on NAT-enabled routers

---

### **⏱️ NTP (Network Time Protocol)**

| **Purpose** | **Keeps all devices on synchronized time** |
| --- | --- |
| Port | UDP 123 |
| Time Accuracy | Based on **Stratum levels**: |
|  | Stratum 0 = atomic clock (most accurate) |
|  | Stratum 1 = syncs from Stratum 0, etc. |
|  | Stratum ≥16 = invalid |
- Used for:
    - **Troubleshooting logs**
    - **TLS certificate validation**
    - **General clock consistency**

---

### **🎯 QoS (Quality of Service)**

| **Purpose** | **Prioritizes critical traffic during congestion** |
| --- | --- |
| Key Idea | **Managed unfairness** — favor important traffic |
| Used When | Bandwidth is temporarily insufficient |

### **✳️ Key QoS Features:**

| **Feature** | **Description** |
| --- | --- |
| **Classification & Marking** | Assigns traffic classes (e.g., VoIP) early via DSCP or CoS tags |
| **Queuing** | Buffers traffic; separates queues (e.g., VoIP vs. Best Effort) |
- Example: Split output queues → VoIP traffic gets priority queue, others go to standard queue.

---

## **📡 Wireless Networks — Quick Reference**

### **🏠 Types of Wireless LANs**

| **Type** | **Description** | **Use Case** |
| --- | --- | --- |
| **Ad Hoc** | Direct device-to-device, no AP needed | Simple file transfers (e.g., AirDrop) |
| **Infrastructure** | Clients connect via Access Points (APs), which are wired to the network | Home/Enterprise networks |
| **Mesh** | Wireless APs extend coverage by relaying signals without Ethernet cabling | Areas without cabling (e.g., parking lot guard shack) |

---

### **🌐 Wi-Fi Frequency Bands**

| **Band** | **Range** | **Notes** |
| --- | --- | --- |
| **2.4 GHz** | Longer range | 3 non-overlapping channels: **1, 6, 11**High interference, lower throughput |
| **5 GHz** | Medium range | 20+ non-overlapping channels (with 20 MHz width)Supports **channel bonding** (up to 160 MHz) |
| **6 GHz** | Shorter range | Introduced in **Wi-Fi 6E**Supports **WPA3 only**Up to **59 non-overlapping 20 MHz channels**7 non-overlapping 160 MHz channels |

### **📶 Channel Bonding (Throughput Boost):**

| **Width** | **Channels Used** | **Notes** |
| --- | --- | --- |
| **20 MHz** | 1 | Base config |
| **40 MHz** | 2 | Doubles throughput |
| **80 MHz** | 4 | High throughput |
| **160 MHz** | 8 | Maximum throughput (shortest range) |

---

### **📡 Antenna Types**

| **Type** | **Radiation Pattern** | **Use Case** |
| --- | --- | --- |
| **Omnidirectional** | 360° horizontal (dipole) | General coverage in offices and homes |
| **Directional** | Focused beam (e.g. parabolic) | Point-to-point links (e.g. between buildings) |
- **MU-MIMO:** Multiple antennas enable simultaneous client communication

---

### **🔐 Security Note**

- **6 GHz (Wi-Fi 6E)** requires **WPA3** (stronger encryption and privacy)

---

## **🚀 Recent Networking Trends — Quick Reference**

### **🔧 SDN (Software-Defined Networking)**

| **Element** | **Description** |
| --- | --- |
| **Goal** | Centralized, programmable control of network devices |
| **Controller** | Manages all routers/switches centrally |
| **Southbound Interface (SBI)** | Connects **controller → devices** (e.g., via OpenFlow, SSH) |
| **Northbound Interface (NBI)** | Connects **apps → controller**, usually via REST APIs |
| **Benefits** | Automation, faster policy deployment, scalable control |
| **Languages/Tools** | Python, REST, HTTP verbs (GET/POST) |

---

### **🖥️ Virtualization**

| **Type** | **Description** |
| --- | --- |
| **VMs (Virtual Machines)** | Full OS per instance, managed by a **hypervisor** |
| **Type 1 Hypervisor** | Bare-metal (no OS underneath), e.g., VMware ESXi |
| **Type 2 Hypervisor** | Runs on top of OS, e.g., VMware Fusion |
| **Containers** | Share OS kernel, lighter and more portable than VMs (e.g., **Docker**) |
| **Network Virtualization** | Includes **virtual switches/routers** |

---

### **☁️ Cloud Technologies**

| **Model** | **Description** |
| --- | --- |
| **IaaS** | Infrastructure as a Service (e.g., VMs, storage) |
| **PaaS** | Platform as a Service (developer tools/platforms) |
| **SaaS** | Software as a Service (apps via browser, e.g., Gmail) |

| **Deployment** | **Description** |
| --- | --- |
| **Public Cloud** | Shared infrastructure (e.g., AWS, Azure) |
| **Private Cloud** | Dedicated for one org (self-hosted or outsourced) |
| **Hybrid Cloud** | Mix of public + private resources |
- **VPN**: Encrypts office↔cloud traffic for secure data transit

---

### **📶 5G (Cellular Technology)**

| **Spec** | **Value** |
| --- | --- |
| **Max Theoretical Speed** | 20 Gbps |
| **Typical Speed** | ~1.5 Gbps |
| **Latency** | ~1 ms |
| **Frequency Range** | 30–300 GHz (mmWave) |
| **Challenges** | Poor penetration, needs dense small-cell deployment |
| **Use Cases** | Smart cities, autonomous vehicles, high-speed mobile internet |

---

### **📡 Wi-Fi 6 (802.11ax)**

| **Spec** | **Value** |
| --- | --- |
| **Max Throughput** | 9.6 Gbps |
| **Frequencies Used** | 2.4 GHz, 5 GHz |
| **Compared To** | Wi-Fi 5 (3.5 Gbps), Wi-Fi 4 (150 Mbps) |
| **Features** (partial list) | OFDMA, MU-MIMO, Target Wake Time |
| **Wi-Fi 6E** | Adds support for 6 GHz band (WPA3 required) |
