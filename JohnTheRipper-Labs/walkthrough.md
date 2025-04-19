# 🔐 Lab 2 Walkthrough: Cracking a Password-Protected ZIP File  
📜 **Author**: Jaiden Jimerson  
©️ 2025 Jaiden Jimerson. All rights reserved.

In this lab, I simulated a real-world password cracking scenario using a ZIP archive and **John the Ripper**.

---

## 🎯 Objective

Crack the password of a `.zip` file and retrieve its contents using **John the Ripper** and the **RockYou** wordlist.

---

## 🧪 Walkthrough

### 1. ✍️ Created a Secret File

```bash
echo "This is a secret message." > secret.txt
```

Wrote a secret message to a file.

---

### 2. 🔐 Encrypted the File into a ZIP

```bash
zip -e secret.zip secret.txt
```

Password-protected the file using ZIP encryption.

---

### 3. 🧬 Extracted the ZIP Hash

```bash
zip2john secret.zip > zip_hash.txt
```

Converted the ZIP file into a format John the Ripper can crack.

---

### 4. 🧠 Cracked the Password with John

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

Used a dictionary attack to reveal the password. ✅ Success!

---

### 5. 🔓 Revealed the Cracked Password

```bash
john --show zip_hash.txt
```

Displayed the cracked password for verification.

---

### 6. 📂 Unzipped the File with the Cracked Password

```bash
unzip secret.zip
```

Successfully extracted `secret.txt` using the cracked password.

---

### 7. 🕵️ Read the Hidden Message

```bash
cat secret.txt
```

Final output:
> _"This is a secret message."_

---

## 📝 Summary

This lab demonstrated a complete cracking workflow:

- 🔐 Encrypting a file  
- 🧬 Extracting a hash  
- 🧠 Cracking the password  
- 🗝️ Accessing the hidden content  

It reinforced how attackers use weak passwords to their advantage and showcased the power of **John the Ripper** in real-world password auditing.
