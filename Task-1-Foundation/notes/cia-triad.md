# CIA Triad — Cybersecurity Fundamentals

## What is the CIA Triad?
The CIA Triad is the foundation of all cybersecurity. Every security control, policy, and tool maps back to one or more of these three principles.

---

## C — Confidentiality
**Definition:** Ensuring data is accessible only to authorized parties.

**Real-world examples:**
- Encrypting medical records so only the doctor can read them
- Password-protecting a file
- Using HTTPS instead of HTTP

**Attack that violates it:**
- Wireshark capturing HTTP login credentials in plain text ✅ (demonstrated in lab)
- Data breaches where user passwords are leaked

**How to protect it:**
- Encryption (AES-256, TLS)
- Access controls and authentication
- VPNs for secure communication

---

## I — Integrity
**Definition:** Ensuring data is accurate and has not been tampered with.

**Real-world examples:**
- A bank verifying that a transaction amount hasn't been modified in transit
- File hash verification (checking SHA-256 before installing software)
- Digital signatures on emails

**Attack that violates it:**
- Man-in-the-Middle attack modifying data in transit
- SQL Injection altering database records

**How to protect it:**
- Hashing (SHA-256, MD5)
- Digital signatures
- Input validation

---

## A — Availability
**Definition:** Ensuring systems and data are accessible when needed.

**Real-world examples:**
- A hospital's patient system must be online 24/7
- An e-commerce site must handle traffic during sales events
- Backup systems in case primary systems fail

**Attack that violates it:**
- DDoS (Distributed Denial of Service) — floods a server until it crashes
- Ransomware — encrypts files making them unavailable

**How to protect it:**
- Load balancers
- DDoS protection services (Cloudflare)
- Regular backups
- Redundant systems

---

## Lab Observation
In our Metasploitable2 lab:
- **Port 1524 (bindshell)** — violated Confidentiality (anyone can access root)
- **HTTP login capture in Wireshark** — violated Confidentiality (credentials in plain text)
- **22 open ports** — increased attack surface threatening all three principles

