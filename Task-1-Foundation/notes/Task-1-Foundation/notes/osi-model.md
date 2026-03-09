# OSI Model — 7 Layers of Networking

## What is the OSI Model?
The OSI (Open Systems Interconnection) model describes how data travels across a network in 7 standardized layers. Every network communication passes through these layers.

---

## The 7 Layers

| Layer | Name | Function | Protocol Examples | Security Threats |
|-------|------|----------|-------------------|-----------------|
| 7 | Application | End-user apps and protocols | HTTP, FTP, DNS, SMTP | XSS, SQL Injection, Phishing |
| 6 | Presentation | Data formatting, encryption | SSL/TLS, JPEG, ASCII | SSL stripping attacks |
| 5 | Session | Manages sessions between apps | NetBIOS, RPC | Session hijacking |
| 4 | Transport | Reliable delivery, port numbers | TCP, UDP | SYN flood DDoS, port scanning |
| 3 | Network | IP addressing and routing | IP, ICMP, ARP | IP spoofing, routing attacks |
| 2 | Data Link | MAC addressing, frames | Ethernet, Wi-Fi | ARP spoofing, MAC flooding |
| 1 | Physical | Physical bit transmission | Cables, Wi-Fi radio | Network tapping, jamming |

---

## Memory Trick
**"Please Do Not Throw Sausage Pizza Away"**
- Physical, Data Link, Network, Transport, Session, Presentation, Application

---

## TCP vs UDP (Layer 4)

### TCP — Transmission Control Protocol
- **Connection-oriented** — establishes connection first (3-way handshake)
- **3-way handshake:** SYN → SYN-ACK → ACK
- **Reliable** — guarantees delivery, retransmits lost packets
- **Slower** due to overhead
- Used by: HTTP, HTTPS, SSH, FTP

### UDP — User Datagram Protocol
- **Connectionless** — sends data without establishing connection
- **Faster** — no overhead, no guarantees
- **No delivery confirmation**
- Used by: DNS, VoIP, video streaming, gaming

### Security Note:
Attackers exploit TCP's 3-way handshake in **SYN flood attacks** — sending thousands of SYN packets without completing the handshake, exhausting server resources.

---

## Key Protocols

### DNS (Domain Name System) — Port 53
- Translates domain names to IP addresses
- Example: google.com → 142.250.x.x
- **Security risk:** DNS poisoning/spoofing can redirect users to malicious sites

### HTTP vs HTTPS
- **HTTP (Port 80):** Plain text — all data visible to anyone capturing packets
- **HTTPS (Port 443):** TLS encrypted — data unreadable to eavesdroppers
- **Lab proof:** Wireshark captured HTTP login credentials in plain text instantly

### IP Addressing
- **IPv4:** 32-bit address (e.g., 192.168.32.128)
- **CIDR notation:** 192.168.32.0/24 = 256 addresses (254 usable)
- **NAT:** Hides internal IPs behind one public IP

---

## Lab Relevance
- Nmap operates at **Layers 3 & 4** (Network + Transport)
- Wireshark captures at **Layer 2** (Data Link) and above
- Our HTTP credential capture happened at **Layer 7** (Application)
- The open bindshell (port 1524) is a **Layer 4** vulnerability (Transport — TCP port)
