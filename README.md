# 🛡️ ApexPlanet Cybersecurity & Ethical Hacking Internship

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-blue)
![Ethical Hacking](https://img.shields.io/badge/Track-Ethical%20Hacking-red)
![Duration](https://img.shields.io/badge/Duration-60%20Days-green)
![Status](https://img.shields.io/badge/Status-In%20Progress-yellow)
![Institution](https://img.shields.io/badge/Institute-ABVGIET%20Shimla-purple)

> **Intern:** Anshu | **Institution:** Atal Bihari Vajpayee Government Institute of Engineering and Technology, Shimla | **Program:** B.Tech ECE (2022–2026)

---

## 📋 About This Repository

This repository documents my complete journey through the **ApexPlanet Software Pvt. Ltd. Cybersecurity & Ethical Hacking Internship** — a structured 60-day hands-on program covering everything from cybersecurity fundamentals to advanced penetration testing and incident response.

Every task includes:
- 📝 Detailed notes and findings
- 💻 Commands used with explanations
- 📸 Screenshots as evidence
- 🔧 Tools and techniques applied
- 🛡️ Mitigation strategies

---

## 🗺️ Program Structure

| Task | Topic | Timeline | Status |
|------|-------|----------|--------|
| [Task 1](#task-1) | Foundation & Environment Setup | Days 1–12 | ✅ Complete |
| [Task 2](#task-2) | Network Security & Scanning | Days 13–24 | ⏳ Upcoming |
| [Task 3](#task-3) | Web Application Security | Days 25–36 | ⏳ Upcoming |
| [Task 4](#task-4) | Exploitation & System Security | Days 37–48 | ⏳ Upcoming |
| [Task 5](#task-5) | Capstone Project & Incident Response | Days 49–60 | ⏳ Upcoming |

---

## 📁 Repository Structure

```
apexplanet-cybersecurity-internship/
│
├── README.md
│
├── Task-1-Foundation/
│   ├── notes/
│   │   ├── cia-triad.md
│   │   ├── osi-model.md
│   │   ├── threat-types.md
│   │   ├── cryptography-basics.md
│   │   └── hashing-demo.md
│   ├── screenshots/
│   │   ├── kali-boot.png
│   │   ├── metasploitable-nmap-scan.png
│   │   ├── netcat-root-shell.png
│   │   ├── wireshark-http-capture.png
│   │   ├── openssl-encryption.png
│   │   └── sha256-hashing.png
│   ├── linux-cheatsheet.md
│   ├── openssl-commands.md
│   └── Task1-Report.pdf
│
├── Task-2-Network-Scanning/        ← Coming Soon
├── Task-3-Web-App-Security/        ← Coming Soon
├── Task-4-Exploitation/            ← Coming Soon
└── Task-5-Capstone/                ← Coming Soon
```

---

## 🔵 Task 1 — Foundation & Environment Setup {#task-1}
**Timeline: Days 1–12 | Status: ✅ Complete**

### 🎯 Objective
Build strong fundamentals in cybersecurity, networking, cryptography, and set up a professional ethical hacking lab.

### 🖥️ Lab Environment

| Component | Details |
|-----------|---------|
| Hypervisor | VMware Workstation |
| Attacker Machine | Kali Linux 2025.4 (IP: 192.168.32.128) |
| Target Machine | Metasploitable2 (IP: 192.168.32.129) |
| Network Type | Host-Only (isolated, no internet) |

### 📚 Concepts Covered

**CIA Triad:**
- **Confidentiality** — Only authorized users access data
- **Integrity** — Data cannot be tampered with
- **Availability** — Systems accessible when needed

**Threat Types Studied:**
Phishing, Malware, Ransomware, DDoS, SQL Injection, Brute Force, Social Engineering, Wireless Attacks, Insider Threats

**OSI Model:** All 7 layers studied with security relevance for each layer

**Cryptography:**
- Symmetric vs Asymmetric encryption
- Hashing (MD5, SHA-256) and the Avalanche Effect
- SSL/TLS and Digital Certificates

### 🔧 Tools Used

| Tool | Purpose | Key Finding |
|------|---------|-------------|
| Nmap | Network scanning | Found 22 open ports on Metasploitable2 |
| Netcat | Network debugging | Got root shell via open bindshell (port 1524) |
| Wireshark | Packet capture | Captured HTTP credentials in plain text |
| OpenSSL | Encryption/Hashing | Demonstrated AES-256-CBC + SHA-256 |

### 💻 Key Commands Used

```bash
# Network discovery
nmap -sn 192.168.32.0/24

# Service version detection
nmap -sV 192.168.32.129

# Root shell via open bindshell
nc 192.168.32.129 1524

# Capture HTTP POST traffic in Wireshark
http.request.method == "POST"

# AES-256 Encryption
openssl enc -aes-256-cbc -salt -in secret.txt -out encrypted.enc

# SHA-256 Hashing
echo -n "Anshu" | openssl dgst -sha256
```

### 🔑 Key Findings & Observations

1. **Metasploitable2 has 22 open ports** — including backdoored services (vsftpd 2.3.4, UnrealIRCd) and an open root shell on port 1524
2. **HTTP credentials are visible in plain text** in Wireshark — login username/password captured instantly
3. **SHA-256 Avalanche Effect proven** — changing "Anshu" to "anshu" (one character) produces a completely different hash
4. **Port 1524 (bindshell)** — gained root access with zero credentials using just netcat
5. **/etc/shadow readable** — all password hashes extracted after gaining root access

### 📸 Screenshots
All evidence screenshots are in the `Task-1-Foundation/screenshots/` folder.

### 📦 Deliverables
- [x] Lab Setup Report (PDF)
- [x] GitHub Repository with notes & cheatsheet
- [x] 5-min Video Walkthrough

---

## 🟢 Task 2 — Network Security & Scanning {#task-2}
**Timeline: Days 13–24 | Status: ⏳ Upcoming**

Topics: Reconnaissance (Passive & Active), Nmap Advanced Scanning, Vulnerability Scanning with OpenVAS, Wireshark Advanced Analysis, Firewall Rules with iptables.

---

## 🟡 Task 3 — Web Application Security {#task-3}
**Timeline: Days 25–36 | Status: ⏳ Upcoming**

Topics: SQL Injection, XSS, CSRF, File Inclusion Attacks, Burp Suite Advanced, Web Security Headers.

---

## 🔴 Task 4 — Exploitation & System Security {#task-4}
**Timeline: Days 37–48 | Status: ⏳ Upcoming**

Topics: Metasploit Framework, Password Attacks (Hydra, John the Ripper), Social Engineering Simulation, Malware Analysis, System Hardening.

---

## 🏆 Task 5 — Capstone Project & Incident Response {#task-5}
**Timeline: Days 49–60 | Status: ⏳ Upcoming**

Topics: Full Penetration Test Report, Incident Response Simulation, Final Presentation.

---

## 🛠️ Tools & Technologies

![Kali Linux](https://img.shields.io/badge/Kali_Linux-557C94?style=flat&logo=kali-linux&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-Network_Scanner-blue)
![Wireshark](https://img.shields.io/badge/Wireshark-Packet_Analyzer-1679A7)
![Metasploit](https://img.shields.io/badge/Metasploit-Framework-red)
![Burp Suite](https://img.shields.io/badge/Burp_Suite-Web_Proxy-orange)
![OpenSSL](https://img.shields.io/badge/OpenSSL-Cryptography-green)

---

## 📜 Certifications & Background

- 🏅 CCNA 200-301 (Simplilearn, February 2026)
- 🔐 Cybersecurity Fundamentals Certification
- 🐍 Python Programming Certification
- 💼 Network & IT Internship Experience (Active Directory, DNS/DHCP, Squid Proxy, Windows Server)

---

## 📞 Contact

**Anshu** | B.Tech ECE | ABVGIET Shimla
- 🔗 LinkedIn: [Your LinkedIn URL]
- 📧 Email: [Your Email]

---

> *"The quieter you become, the more you can hear." — Kali Linux motto*
