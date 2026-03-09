# OpenSSL Commands — Hands-On Reference

## What is OpenSSL?
OpenSSL is a toolkit that implements SSL/TLS protocols and provides cryptographic functions. Pre-installed on Kali Linux.

---

## Encryption Commands

### AES-256-CBC Encryption (performed in lab)
```bash
# Encrypt a file
openssl enc -aes-256-cbc -salt -in secret.txt -out encrypted.enc

# Decrypt a file
openssl enc -d -aes-256-cbc -in encrypted.enc -out decrypted.txt

# Encrypt with specific iterations (more secure)
openssl enc -aes-256-cbc -pbkdf2 -iter 100000 -in secret.txt -out encrypted.enc
```

---

## Hashing Commands

### SHA-256 (performed in lab)
```bash
# Hash a string
echo -n "Anshu" | openssl dgst -sha256
# Output: SHA2-256(stdin)= 752b0f06b8a813d7af1c199d9dee0fbf...

echo -n "anshu" | openssl dgst -sha256
# Output: SHA2-256(stdin)= 77aa5a4f9aa447478c828c48cd9af469...
# ↑ Completely different — Avalanche Effect!

# Hash a file
openssl dgst -sha256 filename.txt

# Other hash algorithms
echo -n "text" | openssl dgst -md5
echo -n "text" | openssl dgst -sha1
echo -n "text" | openssl dgst -sha512
```

---

## Key Generation

### Generate RSA Key Pair
```bash
# Generate private key (2048-bit RSA)
openssl genrsa -out private.pem 2048

# Extract public key from private key
openssl rsa -in private.pem -pubout -out public.pem

# View key details
openssl rsa -in private.pem -text -noout
```

### Generate Self-Signed Certificate
```bash
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
```

---

## SSL/TLS Analysis

### Check a Website's Certificate
```bash
# View SSL certificate of a website
openssl s_client -connect google.com:443

# Check certificate expiry
echo | openssl s_client -connect google.com:443 2>/dev/null | openssl x509 -noout -dates

# View full certificate details
echo | openssl s_client -connect google.com:443 2>/dev/null | openssl x509 -noout -text
```

---

## Lab Results — Actual Output

### Encryption Demo
```
Input file: secret.txt
Content: "This is anshu's secret message"

After encryption → encrypted.enc:
Salted__[binary garbage — completely unreadable]

After decryption → decrypted.txt:
"This is anshu's secret message"  ← perfectly restored!
```

### Hashing Demo — Avalanche Effect Proven
```
Input: "Anshu"
Hash:  752b0f06b8a813d7af1c199d9dee0fbf1990187168d304c1e0ae0e30e34dbe26

Input: "Anshu" (same)
Hash:  752b0f06b8a813d7af1c199d9dee0fbf1990187168d304c1e0ae0e30e34dbe26
       ↑ IDENTICAL — deterministic property confirmed

Input: "anshu" (one char changed: A→a)
Hash:  77aa5a4f9aa447478c828c48cd9af46975d9bb0375a7cb5bbba03be5f4aa8d31
       ↑ COMPLETELY DIFFERENT — avalanche effect confirmed
```

---

## Key Takeaways
1. AES-256-CBC is military-grade symmetric encryption
2. SHA-256 is one-way — the hash cannot be reversed
3. Even a single character change produces a completely different hash
4. OpenSSL warning about "deprecated key derivation" → use `-pbkdf2` flag in production
5. Real-world passwords should use bcrypt/argon2, not raw SHA-256 (needs salt + iterations)
