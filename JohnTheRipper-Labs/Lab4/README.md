# Lab #4 — Cracking MD5 and DES Hashes with John the Ripper

![Made with Bash](https://img.shields.io/badge/Bash-Scripting-1f425f?style=flat-square&logo=gnu-bash)
![Cybersecurity Lab](https://img.shields.io/badge/John%20the%20Ripper-Crack%20Hashes-blueviolet?style=flat-square)
![Status: Personal Lab](https://img.shields.io/badge/Status-Private_Use-orange?style=flat-square)

> Hands-on cybersecurity lab to crack MD5 and DES password hashes using **John the Ripper** and a wordlist. Learn how to simulate hash cracking from scratch, reset your environment, and fully understand the process like a pro.

---

## 🛠️ Prerequisites

Ensure the following tools are installed:

```bash
sudo apt install john whois
```

Also unzip the RockYou wordlist:

```bash
gzip -d /usr/share/wordlists/rockyou.txt.gz
```

---

## Part 1: Crack an Unsalted MD5 Hash

### 🔐 Step 1: Generate the MD5 Hash

```bash
echo -n "hunter2" | md5sum
```

Expected output:
```text
2ab96390c7dbe3439de74d0c9b0b1767  -
```

### 💾 Step 2: Save the Hash

```bash
echo "2ab96390c7dbe3439de74d0c9b0b1767" > md5hash.txt
```

### ⚔️ Step 3: Crack the Hash

```bash
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt md5hash.txt
```

### 🔍 Step 4: Show Cracked Password

```bash
john --show --format=raw-md5 md5hash.txt
```

Expected:
```text
?:hunter2
```

---

## Part 2: Crack a Salted DES Hash

### 🧪 Step 1: Generate a DES Hash

```bash
mkpasswd --method=des --salt=hx hunter2
```

Example output:
```text
hx17.b/1BoFCk
```

### 📝 Step 2: Format Like /etc/passwd

```bash
echo "crackme:hx17.b/1BoFCk:0:0::/root:/bin/bash" > deshash.txt
```

### ⚔️ Step 3: Crack the DES Hash

```bash
john --format=descrypt --wordlist=/usr/share/wordlists/rockyou.txt deshash.txt
```

### 🔍 Step 4: Show Cracked Password

```bash
john --show --format=descrypt deshash.txt
```

Expected:
```text
crackme:hunter2
```

---

## ♻️ Reset & Redo the Lab from Scratch

### 1. Remove Hash Files

```bash
rm md5hash.txt deshash.txt
```

### 2. Clear John the Ripper’s Saved Passwords

```bash
rm ~/.john/john.pot
```

### 3. (Optional) Explore All Formats

```bash
john --list=formats | grep -i des
```

---

## 📚 What You Learn

- How MD5 and DES password hashes work
- Difference between salted and unsalted hashes
- How to simulate /etc/passwd entries
- How to use John the Ripper like a professional
- How to fully reset cracking environments for clean retesting

---

## ⚙️ Skills Gained

| Skill                        | Description                                             |
|-----------------------------|---------------------------------------------------------|
| Bash scripting              | Working with terminal commands & pipes                 |
| Hash cracking               | Using `john` to brute force hashes                     |
| Password security analysis  | Understanding weaknesses in MD5 and DES                |
| Linux file handling         | Creating and formatting password files for cracking    |
| Tool familiarity            | `md5sum`, `mkpasswd`, `echo`, `rm`, `cat`, `john`      |
| Wordlist attack strategy    | Using `rockyou.txt` effectively for real-world testing |

---

## ✅ Summary

| Task                     | Tools Used                             |
|--------------------------|----------------------------------------|
| Create MD5 Hash          | `md5sum`, `echo`                       |
| Crack MD5 Hash           | `john --format=raw-md5`                |
| Create DES Hash          | `mkpasswd --method=des`                |
| Format DES Hash File     | `echo` with passwd-style entry         |
| Crack DES Hash           | `john --format=descrypt` or `crypt`    |
| Reset John & Files       | `rm`, delete `~/.john/john.pot`        |

---

## Author

**Jaiden**  
Cybersecurity Researcher & Ethical Hacking Student  
Follow my journey on [X (Twitter) @JaidenCyberSec](https://x.com/JaidenCyberSec)

---

## Legal Notice

© 2025 Jaiden — All rights reserved.  
This lab is for **personal and educational reference only**.  
**No reproduction, redistribution, or commercial use is permitted** without **explicit written permission**.  

