# 🧠 **John the Ripper Lab Series**

Welcome to my **John the Ripper** lab series!  
In this series, we’ll dive into **password cracking** techniques that simulate real-world security challenges. Each lab walks through hands-on examples using **Kali Linux**, **John the Ripper**, and other critical offensive security tools.

Through these labs, you’ll learn how to break encrypted or hashed data, simulating real-world attacks to recover passwords.

---

## 📂 **Labs Overview**

### 🔐 **[Lab 1: Crack SHA-512 Password Hash](./Lab1/README-lab1.md)**  
In this lab, you’ll simulate post-exploitation of a Linux system, cracking a **SHA-512** password hash using tools like `openssl`, `unshadow`, and **John the Ripper**.

### 🗜️ **[Lab 2: Crack Encrypted ZIP File](./Lab2/README.md)**  
Learn to crack the password of a **ZIP file** encrypted with `zip -e`. You’ll use `zip2john` to extract the hash and **John the Ripper** to crack it with the popular `rockyou.txt` wordlist.

### 🧪 **[Lab 3: Custom User Shadow Attack - Kuzan](./Lab3/README.md)**  
Simulate an attack on a fake Linux user named **kuzan**. You’ll retrieve and crack SHA-512 hashes from `/etc/passwd` and `/etc/shadow` to gain access.

### 💥 **[Lab 4: Crack Raw MD5 Hash](./Lab4/README.md)**  
This lab focuses on cracking an unsalted **MD5** hash. You’ll create the hash using `md5sum`, feed it into John the Ripper with the proper format, and recover the original password.

### 🧱 **[Lab 5: Crack NTLM Hash with John the Ripper](./Lab5/README.md)**  
In this lab, you’ll generate and crack a Windows **NTLM hash** using `python3`, format it for John, and use `rockyou.txt` to crack the hash. This simulates a real-world post-exploitation scenario on a Windows machine.

---

## 🛠️ **Tools Used**

- **Kali Linux**
- **John the Ripper**
- **OpenSSL**
- **zip2john**
- **rockyou.txt** (wordlist)
- **unshadow**
- **unzip**
- **md5sum**
- **Python 3**

---

## 🧪 **Lab Structure**

Each lab in this series includes:
- 🔍 **Step-by-step walkthroughs**  
- 📄 **Command and file examples**  
- 📸 **Screenshots** (where needed)  
- 🧠 **Key lessons learned** and recommendations for next steps

These labs are beginner-friendly but packed with real-world, hands-on security skills that you can use for offensive and defensive work.

---

## 💡 **Why This Series?**

I’m deeply committed to mastering tools that are crucial for both **red team** and **blue team** operations. These labs are my way of sharpening my skills in cybersecurity and sharing the knowledge I gain with others along the way. 💻🔥

---

## 🌐 **Connect With Me**

- 🧑‍💻 **LinkedIn**: [Jaiden Jimerson](https://www.linkedin.com/in/jaiden-jimerson-319995140)  
- 🐦 **X (Twitter)**: [@JaidenCyberSec](https://x.com/JaidenCyberSec)  
- 🧩 **TryHackMe**: [Jaiden.Jimerson](https://tryhackme.com/p/Jaiden.Jimerson)

---

> “Train like you already have the job.”

---

## 📜 **Copyright**

© 2025 Jaiden Jimerson. All rights reserved.  
This series and the content within it are for educational purposes only. Unauthorized use or reproduction of any materials in this series is prohibited without prior permission.
