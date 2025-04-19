## 🔍 Walkthrough Overview

These labs simulate real-world password cracking scenarios using **John the Ripper**.  
Each walkthrough breaks down the process step-by-step with real commands and outputs.

---

### 🔓 Lab 1: Crack SHA-512 Password (zuko:123456)

- 🧪 Created a SHA-512 hash using:  
  `openssl passwd -6 123456`
- 📄 Saved the hash in a file called `test_passwd.txt`
- 🛠️ Ran John the Ripper using the default wordlist
- ✅ Verified the cracked password using:  
  `john --show test_passwd.txt`

> ✅ **Outcome:** Cracked password `123456` for user `zuko`

---

### 🗜️ Lab 2: Crack Encrypted ZIP File (zip2john)

- 📁 Created a password-protected ZIP file using `zip -e`
- 🔓 Extracted password hash using:  
  `zip2john secret.zip > ziphash.txt`
- 📖 Used the `rockyou.txt` wordlist with John to crack it:  
  `john --wordlist=/usr/share/wordlists/rockyou.txt ziphash.txt`
- ✅ Recovered the original password from the ZIP archive

> ✅ **Outcome:** Successfully cracked ZIP password and accessed contents

---

### 👤 Lab 3: Simulated Linux Shadow File Crack (kuzan:anime)

- 🧱 Built fake `/etc/passwd` and `/etc/shadow` entries for user `kuzan`
- 🔐 Hashed the password `anime` using SHA-512:  
  `openssl passwd -6 anime`
- 📄 Created `passwd.txt` and `shadow.txt` with matching entries
- 🪞 Used `unshadow` to generate a crackable file:  
  `unshadow passwd.txt shadow.txt > unshadowed.txt`
- 📖 Ran John with `rockyou.txt` wordlist:  
  `john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt`
- 🔍 Verified cracked password:  
  `john --show unshadowed.txt`

> ✅ **Outcome:** Successfully cracked password `anime` for user `kuzan`

---

Each walkthrough is designed to be beginner-friendly while reinforcing real-world offensive security techniques.  
More labs coming soon!

---

## 👨‍💻 Author

Created by **Jaiden Jimerson**  
🐦 [@JaidenCyberSec](https://x.com/JaidenCyberSec)  
💼 [LinkedIn](https://linkedin.com/in/jaiden)

---

## 📜 Copyright

© 2025 **Jaiden Jimerson**. All rights reserved.  
This content is for educational purposes only. Do not use these techniques without proper authorization.

