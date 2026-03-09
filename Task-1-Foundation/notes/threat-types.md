# Threat Types & Attack Vectors

## Common Cyber Threats

### 1. Phishing
**What it is:** Fake emails, websites, or messages that trick users into revealing credentials or installing malware.

**How it works:**
- Attacker creates a fake login page (e.g., fake Gmail login)
- Sends email saying "Your account will be suspended — login now"
- Victim enters credentials → attacker captures them

**Real example:** Fake bank emails asking you to "verify your account"

**Prevention:** Email filtering, user awareness training, MFA (Multi-Factor Authentication)

---

### 2. Malware
**What it is:** Malicious software installed without user consent.

**Types:**
| Type | Description |
|------|-------------|
| Virus | Attaches to files, spreads when files are shared |
| Trojan | Disguised as legitimate software |
| Spyware | Silently monitors user activity |
| Adware | Displays unwanted advertisements |
| Worm | Self-replicating, spreads across networks |

**Prevention:** Antivirus, keeping software updated, not downloading from untrusted sources

---

### 3. Ransomware
**What it is:** Encrypts victim's files and demands payment (usually cryptocurrency) for the decryption key.

**Famous attacks:** WannaCry (2017), NotPetya, Colonial Pipeline attack

**How it works:**
1. Delivered via phishing email or exploit
2. Encrypts all files on the system
3. Displays ransom note demanding payment
4. Files remain inaccessible without paying

**Prevention:** Regular backups, patch management, email filtering

---

### 4. DDoS (Distributed Denial of Service)
**What it is:** Floods a server with traffic from many sources until it crashes and becomes unavailable.

**How it works:**
- Attacker controls thousands of infected computers (botnet)
- Commands them all to send requests to target simultaneously
- Target server gets overwhelmed and crashes

**Lab connection:** hping3 can simulate SYN flood attacks (Task 2)

**Prevention:** CDN/DDoS protection (Cloudflare), rate limiting, traffic analysis

---

### 5. SQL Injection
**What it is:** Injecting malicious SQL code into input fields to manipulate databases.

**Example:**
```
Normal query: SELECT * FROM users WHERE username='admin'
Injected:     SELECT * FROM users WHERE username='' OR '1'='1'
Result: Returns ALL users — bypasses authentication
```

**Lab connection:** DVWA SQL Injection module (Task 3)

**Prevention:** Prepared statements, input validation, parameterized queries

---

### 6. Brute Force
**What it is:** Systematically trying every possible password until the correct one is found.

**Types:**
- **Pure brute force:** Try every combination (aaa, aab, aac...)
- **Dictionary attack:** Try common words from a wordlist
- **Credential stuffing:** Try known leaked username/password pairs

**Lab connection:** Hydra for SSH brute force (Task 4)

**Prevention:** Account lockout policies, MFA, strong password requirements, CAPTCHA

---

## Attack Vectors

### Social Engineering
Manipulating people psychologically to reveal sensitive information.

**Examples:**
- **Pretexting:** "Hi, I'm from IT support, I need your password to fix your account"
- **Baiting:** Leaving a USB drive labeled "Salary Data" in a parking lot
- **Vishing:** Voice calls impersonating bank officials

**Key insight:** The weakest link in security is always the human element.

### Wireless Attacks
Exploiting weaknesses in Wi-Fi protocols.

**Types:**
- **Evil Twin:** Create a fake Wi-Fi hotspot with same name as legitimate one
- **WEP Cracking:** WEP encryption is broken and crackable in minutes
- **Deauthentication:** Force devices to disconnect and reconnect (capture handshake)

### Insider Threats
Malicious or negligent actions by people with legitimate internal access.

**Types:**
- **Malicious insider:** Employee selling company secrets
- **Negligent insider:** Employee clicking phishing links, using weak passwords
- **Compromised insider:** Employee's credentials stolen and used by attacker

---

## Lab Findings — Threats Observed in Metasploitable2
| Port | Service | Threat Type |
|------|---------|-------------|
| 1524 | Bindshell | Unauthorized Access (no auth) |
| 21 | vsftpd 2.3.4 | Backdoor Malware in software |
| 23 | Telnet | Credential Exposure (plain text) |
| 80 | HTTP Apache | Web Application Attacks |
| 6667 | UnrealIRCd | Backdoored Software |
