# 🧨 Walkthrough: Cracking Linux Passwords with John the Ripper  
📜 **Author**: Jaiden Jimerson  
©️ 2025 Jaiden Jimerson. All rights reserved.

This lab simulates a **real-world attack scenario** where an attacker gains access to the `passwd` and `shadow` files from a compromised Linux system. You’ll recreate the environment, hash a password, and crack it using **John the Ripper**. 💻🔓

---

## 🎯 Scenario

You’ve escalated privileges on a Linux box and extracted the system’s `passwd` and `shadow` files. Your mission:

- 🔧 Simulate realistic Linux user files  
- 🔐 Generate a hashed password  
- 🧠 Use `unshadow` + `john` to crack it

---

## 🧱 Step 1: Set Up the Lab Environment

Create a fresh working directory to keep everything organized:

```bash
mkdir john-shadow-lab && cd john-shadow-lab
```

🧼 Keeping it clean and contained.

---

## 👤 Step 2: Create a Fake `passwd` File

You’re simulating a user named **Kuzan**:

```bash
echo 'kuzan:x:1001:1001:Kuzan:/home/kuzan:/bin/bash' > passwd.txt
```

🔍 Breakdown:  
- `kuzan` = username  
- `x` = points to `shadow` file  
- `1001:1001` = UID:GID  
- `/home/kuzan` = home dir  
- `/bin/bash` = login shell

---

## 🔐 Step 3: Generate a SHA-512 Password Hash

Let’s hash the password **anime**:

```bash
openssl passwd -6 anime
```

🧾 Example output:

```
$6$Z12vX9pN$72XILsGb...lVYu/.R/
```

Copy the entire hash — you’ll need it in the next step.

---

## 🕶️ Step 4: Create a Matching `shadow` File

Paste the hash into your fake shadow file:

```bash
echo 'kuzan:$6$Z12vX9pN$72XILsGb...lVYu/.R/:19000:0:99999:7:::' > shadow.txt
```

🧠 Shadow file anatomy:
- `19000` = days since last change  
- `99999` = max days before change  
- `7` = warning days before expiration

---

## 🛠️ Step 5: Combine `passwd` and `shadow` Using `unshadow`

This merges both files into a format John understands:

```bash
unshadow passwd.txt shadow.txt > unshadowed.txt
```

📦 Now you’ve got full username + password hash pairs.

---

## 💥 Step 6: Crack the Password with John the Ripper

Use the popular **rockyou.txt** wordlist:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

📊 John will begin cracking by testing common passwords — including **anime**.

---

## 🧾 Step 7: Reveal the Cracked Password

Once done, run:

```bash
john --show unshadowed.txt
```

✅ Output:
```
kuzan:anime
```

Boom — password cracked! 🔓🔥

---

## 📚 What You Learned

- 🧬 How Linux separates user credentials between `/etc/passwd` and `/etc/shadow`
- 🔑 SHA-512 password hashing basics
- ⚙️ How to simulate Linux auth environments
- 🐉 Wordlist cracking using John the Ripper

---

## 🧼 Cleanup

Ready to reset the lab?

```bash
cd ..
rm -rf john-shadow-lab
```

Fresh slate for the next run 🧹

---

## 🧑‍💻 About the Author  

**Jaiden**  
Cybersecurity student | Ethical hacker in training  
🐦 [@JaidenCyberSec](https://twitter.com/JaidenCyberSec)  
💼 [LinkedIn](https://linkedin.com/in/jaiden)

---

## ⚠️ Disclaimer

This walkthrough is for **educational purposes only**.  
🚫 Do **not** attempt unauthorized access or cracking on systems you don’t own or have explicit permission to test.
