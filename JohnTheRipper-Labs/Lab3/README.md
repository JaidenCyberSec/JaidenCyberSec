# John the Ripper: Linux Password Cracking Lab

This lab simulates a post-exploitation scenario where an attacker extracts password hashes from a Linux system and uses John the Ripper to crack them. It’s a hands-on exercise in password security, ideal for learners in cybersecurity and ethical hacking.

---

## Objectives

- Understand how Linux authentication works
- Practice extracting and cracking password hashes
- Use John the Ripper effectively with real wordlists

---

## Tools Used

- `John the Ripper`
- `openssl`
- `unshadow`
- `rockyou.txt` wordlist

---

## Lab Steps

### 1. Setup Your Lab Directory

```bash
mkdir john-shadow-lab && cd john-shadow-lab

```

---

### 2. Create a Fake /etc/passwd Entry

```bash
echo 'kuzan:x:1001:1001:Kuzan:/home/kuzan:/bin/bash' > passwd.txt
```

This entry represents a normal Linux user. The "x" means the password is stored in the shadow file.

---

### 3. Generate a Hashed Password

```bash
openssl passwd -6 anime
```

Copy the resulting SHA-512 hash.

---

### 4. Create the Matching /etc/shadow Entry

Replace `<your_hash>` with the one you copied:

```bash
echo 'kuzan:<your_hash>:19000:0:99999:7:::' > shadow.txt
```

This creates a realistic shadow file entry.

---

### 5. Merge passwd and shadow

```bash
unshadow passwd.txt shadow.txt > unshadowed.txt
```

This creates a combined file that John can work with.

---

### 6. Crack the Password

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

John will try each word in the list until it finds a match for the hash.

---

### 7. Show the Cracked Password

```bash
john --show unshadowed.txt
```

Expected output:

```
kuzan:anime
```

---

## What You Practiced

- How Linux stores usernames and passwords
- Creating and understanding hashed passwords (SHA-512)
- Combining and cracking hashes with John the Ripper
- Safe password cracking in a lab environment

---

## Author

**Jaiden** — Cybersecurity & Ethical Hacking Student  
[X (Twitter)](https://twitter.com/JaidenCyberSec) | [LinkedIn](https://linkedin.com/in/jaiden)

---

## Disclaimer

This lab is for **educational purposes only**. Do not use these techniques on real systems without permission.

