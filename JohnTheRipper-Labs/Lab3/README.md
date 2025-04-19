# 🧨 John the Ripper: Linux Password Cracking Lab

🎯 **Simulated Post-Exploitation Scenario**  
You’ve gained root-level access on a Linux box and exfiltrated the `/etc/passwd` and `/etc/shadow` files. Now it’s time to crack some hashes using **John the Ripper**.

This lab is perfect for anyone learning ethical hacking, red teaming, or how password security can be broken if mismanaged.

---

## 🎓 Objectives

- 🧠 Understand how Linux stores and manages passwords  
- 🛠️ Simulate realistic password hashes  
- 🔓 Crack a SHA-512 hash using John and a real wordlist

---

## 🧰 Tools Used

- `John the Ripper` 🔐  
- `openssl` 🔑  
- `unshadow` 🪞  
- `rockyou.txt` wordlist 📖  

> 💡 Make sure `john` and `rockyou.txt` are installed. On Kali Linux, rockyou is usually at:  
> `/usr/share/wordlists/rockyou.txt.gz` — decompress it with `gunzip`.

---

## 🧪 Lab Steps

---

### ✅ Step 1: Set Up Your Lab Directory

```bash
mkdir john-shadow-lab && cd john-shadow-lab
```

Organize your test files into a dedicated folder.

---

### 👤 Step 2: Create a Fake `/etc/passwd` Entry

```bash
echo 'kuzan:x:1001:1001:Kuzan:/home/kuzan:/bin/bash' > passwd.txt
```

This represents a standard Linux user named **kuzan**.

---

### 🔐 Step 3: Generate a Hashed Password

Let’s hash the password **anime** using SHA-512:

```bash
openssl passwd -6 anime
```

📋 Copy the full output — you’ll use it in the next step.

Example:

```
$6$Z12vX9pN$72XILsGb...lVYu/.R/
```

---

### 🕶️ Step 4: Create a Matching `/etc/shadow` Entry

Insert the hash you copied:

```bash
echo 'kuzan:$6$Z12vX9pN$72XILsGb...lVYu/.R/:19000:0:99999:7:::' > shadow.txt
```

📝 `19000` = days since epoch when the password was last changed.

---

### 🛠️ Step 5: Merge `passwd` and `shadow`

John the Ripper needs a single file with both username and hash:

```bash
unshadow passwd.txt shadow.txt > unshadowed.txt
```

✅ This creates a hybrid file John can read.

---

### 🔓 Step 6: Crack the Password

Use the famous `rockyou.txt` wordlist:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

John begins attempting guesses. If **anime** is in the wordlist, it’ll find it.

---

### 📢 Step 7: Reveal the Cracked Password

```bash
john --show unshadowed.txt
```

Expected output:

```
kuzan:anime
```

🔥 Boom — password cracked!

---

## 🧠 What You Practiced

- Linux password architecture: `/etc/passwd` & `/etc/shadow`  
- How SHA-512 password hashes are created  
- Using `unshadow` to prep for cracking  
- Safe, ethical password cracking in a sandbox

---

## 👨‍💻 About the Author

**Jaiden** — Cybersecurity & Ethical Hacking Student  
🐦 [Twitter/X: @JaidenCyberSec](https://twitter.com/JaidenCyberSec)  
💼 [LinkedIn](https://linkedin.com/in/jaiden)

---

## ⚠️ Disclaimer

This lab is for **educational purposes only**.  
🛑 Never attempt unauthorized access or password cracking on live systems. Always get **explicit permission**.

---

## 📜 Copyright

© 2025 Jaiden Jimerson. All rights reserved.  
This lab and all related materials are provided for educational use only. No part may be reproduced or reused without explicit written permission.


