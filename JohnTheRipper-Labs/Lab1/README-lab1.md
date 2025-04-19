# 🧠 John the Ripper Labs  
📜 **Author**: Jaiden Jimerson  
©️ 2025 Jaiden Jimerson. All rights reserved.

This folder contains my hands-on labs using **John the Ripper** to crack SHA-512 password hashes. This particular lab demonstrates how I cracked a password hash for the user `zuko` from a file named `test_passwd.txt`.

---

## 🛠️ Tools & Technologies Used  
- 💻 Kali Linux  
- 🔐 John the Ripper  
- 📂 rockyou.txt wordlist  

---

## 🧪 Lab Breakdown

### 🔍 **Lab: Cracking a SHA-512 Password Hash**  
**🎯 Objective**: Crack a SHA-512 password hash stored in `test_passwd.txt`.

#### 📋 Steps:

1. ✅ Generated the SHA-512 hash for `123456` using:

   ```bash
   openssl passwd -6 123456
   ```

2. 📝 Manually saved the hash in `test_passwd.txt` under the username `zuko`.

3. 🧠 Used **John the Ripper** with the **RockYou** wordlist to crack the hash:

   ```bash
   john --wordlist=/usr/share/wordlists/rockyou.txt test_passwd.txt
   ```

4. 👁️ Displayed the cracked credentials:

   ```bash
   john --show test_passwd.txt
   ```

---

### ✅ **Outcome**  
- 👤 Username: `zuko`  
- 🔓 Password: `123456`  

📄 [View Full Walkthrough](./Lab1_walkthrough.md)

---

## 📝 Notes  
- This lab shows how to generate and crack SHA-512 password hashes using `openssl` and John the Ripper.  
- The `john --show` command is essential for revealing cracked credentials post-crack.  
- 📸 Screenshots are included in the `screenshots` folder for reference.

---

## 📷 Screenshot  
![Cracked zuko's SHA-512 hash](./JohnTheRipper-Labs/Lab1/John-zuko-crack.png)

