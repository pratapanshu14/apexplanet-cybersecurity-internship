# Cryptography Basics

## What is Cryptography?
Cryptography is the science of securing information by transforming it into an unreadable format, ensuring only authorized parties can read it.

---

## Encryption Types

### Symmetric Encryption
- **Same key** is used to both encrypt AND decrypt
- Fast and efficient for large amounts of data
- Challenge: How do you securely share the key?

**Example Algorithm: AES-256-CBC**
```
Plain text + Key → [Encryption] → Ciphertext
Ciphertext + Same Key → [Decryption] → Plain text
```

**Lab Demo:**
```bash
# Encrypt
openssl enc -aes-256-cbc -salt -in secret.txt -out encrypted.enc

# Decrypt
openssl enc -d -aes-256-cbc -in encrypted.enc -out decrypted.txt
```

**Use cases:** Disk encryption, file encryption, VPN tunnels

---

### Asymmetric Encryption
- Uses **two mathematically linked keys:**
  - **Public key:** Can be shared with anyone — used to ENCRYPT
  - **Private key:** Must be kept secret — used to DECRYPT
- Solves the key-sharing problem
- Slower than symmetric encryption

**Example Algorithm: RSA**
```
Sender uses recipient's PUBLIC key to encrypt
Recipient uses their own PRIVATE key to decrypt
```

**Use cases:** HTTPS, email encryption (PGP), digital signatures, SSH

---

### How HTTPS Uses Both:
1. Browser connects to server
2. Server sends its **public key** (in SSL certificate)
3. Browser generates a random **session key** (symmetric)
4. Browser encrypts session key with server's **public key** → sends it
5. Server decrypts with its **private key** → gets session key
6. Both now share session key → use **symmetric encryption** for speed
This is the **TLS Handshake**

---

## Hashing

### What is Hashing?
- **One-way transformation** — converts any input to a fixed-length output
- **Cannot be reversed** — you cannot get the original input from the hash
- Same input **always** produces same output (deterministic)
- Different inputs produce different outputs (ideally)

### SHA-256 Demo (Actual Lab Results)
```bash
$ echo -n "Anshu" | openssl dgst -sha256
SHA2-256= 752b0f06b8a813d7af1c199d9dee0fbf1990187168d304c1e0ae0e30e34dbe26

$ echo -n "Anshu" | openssl dgst -sha256
SHA2-256= 752b0f06b8a813d7af1c199d9dee0fbf1990187168d304c1e0ae0e30e34dbe26
(Identical — DETERMINISTIC property proven)

$ echo -n "anshu" | openssl dgst -sha256
SHA2-256= 77aa5a4f9aa447478c828c48cd9af46975d9bb0375a7cb5bbba03be5f4aa8d31
(Completely different — AVALANCHE EFFECT proven)
```

### Key Properties of Hashing
| Property | Description |
|----------|-------------|
| Deterministic | Same input always = same hash |
| Avalanche Effect | 1 character change = completely different hash |
| One-way | Cannot reverse hash to get original |
| Fixed length | SHA-256 always outputs 256 bits regardless of input size |
| Collision resistant | Practically impossible for two inputs to produce same hash |

### Common Hash Algorithms
| Algorithm | Output Size | Status |
|-----------|-------------|--------|
| MD5 | 128 bits | BROKEN — do not use for security |
| SHA-1 | 160 bits | WEAK — being phased out |
| SHA-256 | 256 bits | SECURE — widely used |
| SHA-512 | 512 bits | VERY SECURE |
| bcrypt | Variable | BEST for passwords (includes salt) |

### Why MD5 is Broken
- Metasploitable2's /etc/shadow uses `$1$` prefix = MD5 hashing
- MD5 hashes can be cracked using rainbow tables
- Modern GPUs can compute billions of MD5 hashes per second
- Always use bcrypt or SHA-256 for password storage

---

## Digital Certificates & SSL/TLS

### What is a Digital Certificate?
A digital certificate is like a passport for a website — it proves the website is who it claims to be.

**Contains:**
- Website's public key
- Website's domain name
- Issuing Certificate Authority (CA)
- Expiry date
- Digital signature from CA

### Certificate Authorities (CA)
Trusted organizations that issue certificates:
- DigiCert, Let's Encrypt, Comodo, GlobalSign

### Lab Observation
- Visiting `http://192.168.32.129` → No padlock, credentials in plain text
- Visiting `https://google.com` → Padlock shown, TLS encrypted
- Wireshark proof: HTTP shows readable data, HTTPS shows only ciphertext

---

## Hashing — Use Cases in Security
1. **Password storage:** Store hash of password, not plain text
2. **File integrity:** Verify downloaded files match expected hash
3. **Digital signatures:** Hash a document, then sign the hash
4. **Blockchain:** Each block contains hash of previous block
