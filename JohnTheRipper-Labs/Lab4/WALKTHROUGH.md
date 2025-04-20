# 🔓 Lab Walkthrough — Cracking Hashes with John the Ripper

This walkthrough accompanies the `README.md` and provides an **in-depth guide** for successfully completing this hash-cracking lab.

---

## 🧠 Purpose of the Lab

This lab simulates real-world scenarios where:
- You are analyzing compromised password hashes
- You need to crack them using industry tools
- You understand the difference between **salted** and **unsalted** hashes

---

## 🧩 Part 1: Cracking an Unsalted MD5 Hash

---

### ✅ Step 1: Generate a Hash to Crack

```bash
echo -n "hunter2" | md5sum
```

- `-n` omits the newline.
- `md5sum` generates a 32-character hash.

You’ll get:
```
2ab96390c7dbe3439de74d0c9b0b1767  -
```

---

### ✅ Step 2: Save Hash for Cracking

```bash
echo "2ab96390c7dbe3439de74d0c9b0b1767" > md5hash.txt
```

Why? John the Ripper needs the hash saved in a plain text file.

---

### ✅ Step 3: Crack the Hash with John

```bash
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt md5hash.txt
```

Explanation:
- `--format=raw-md5` tells John it’s a plain MD5 hash (no salt).
- `rockyou.txt` is a massive password list used for brute force.
- You’ll see something like:

```
Using default input encoding: UTF-8
Loaded 1 password hash (Raw-MD5 [MD5 128/128 AVX 4x3])
Press 'q' or Ctrl-C to abort, almost any other key for status
hunter2           (?)
```

---

### ✅ Step 4: View Cracked Password

```bash
john --show --format=raw-md5 md5hash.txt
```

Output:
```
?:hunter2
```

Done — cracked the unsalted hash!

---

## 🧩 Part 2: Cracking a Salted DES Hash

---

### ✅ Step 1: Generate DES Hash with Salt

```bash
mkpasswd --method=des --salt=hx hunter2
```

Result:
```
hx17.b/1BoFCk
```

This simulates a DES hash from `/etc/shadow`.

---

### ✅ Step 2: Format Like a Linux passwd Entry

```bash
echo "crackme:hx17.b/1BoFCk:0:0::/root:/bin/bash" > deshash.txt
```

Why this format?
- John expects a fake `/etc/passwd`-like structure.
- This makes the hash readable as a user password.

---

### ✅ Step 3: Crack It

```bash
john --format=descrypt --wordlist=/usr/share/wordlists/rockyou.txt deshash.txt
```

This might take longer than MD5 due to the added complexity from the salt.

---

### ✅ Step 4: Show Cracked Password

```bash
john --show --format=descrypt deshash.txt
```

Result:
```
crackme:hunter2:0:0::/root:/bin/bash
```

---

## 🧹 Resetting & Troubleshooting

### 🔄 Restart the Lab

```bash
rm md5hash.txt deshash.txt
rm ~/.john/john.pot
```

This removes:
- Your saved hashes
- John’s memory of cracked passwords

---

## 🧰 Troubleshooting Tips

| Issue                                    | Fix |
|------------------------------------------|-----|
| `No password hashes loaded`              | Ensure file is saved correctly and in correct format |
| `Unknown ciphertext format`              | Use `--format=raw-md5` or `--format=descrypt` |
| File exists but nothing loads            | Double-check file path and structure (e.g., passwd-style for DES) |
| Still failing                            | Try this to test supported formats: `john --list=formats | grep -i des` |

---

## 🎓 What You Learn from This Lab

- How hashing works (MD5 vs DES)
- What salting does to a hash
- Real Linux-style formatting for passwords
- Using John the Ripper’s syntax and formats
- Wordlist brute forcing techniques
- Resetting a cracking environment cleanly

---

## 👨‍💻 Author

Made with care by **Jaiden**  
🔐 Cybersecurity student | Ethical hacker in training  
[X (Twitter) @JaidenCyberSec](https://x.com/JaidenCyberSec)

---

## 🚫 Reproduction Policy

This walkthrough is for **personal reference only**.  
Do **not reproduce, modify, or redistribute** this content or lab without **explicit permission from the author**.

© 2025 Jaiden — All Rights Reserved.
