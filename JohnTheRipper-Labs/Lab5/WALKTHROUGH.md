# 🧭 Lab 5: Full Walkthrough – Cracking an NTLM Hash with John the Ripper

---

## 🔍 Scenario

You’ve recovered an **NTLM hash** from a Windows machine and your objective is to **crack the hash to reveal the password**. In this lab, you’ll generate the NTLM hash for the password `kingdom`, format it correctly, and use **John the Ripper** with the **rockyou.txt** wordlist to perform a dictionary attack.

---

## ✅ Requirements

Make sure the following tools are available on your system:

| Tool | Description |
|------|-------------|
| `Python3` | To generate an NTLM hash manually |
| `John the Ripper` | Password-cracking tool |
| `rockyou.txt` | A wordlist of common passwords located at `/usr/share/wordlists/rockyou.txt` |
| Terminal (Linux or WSL) | To run commands |

---

## 🧱 Step-by-Step Instructions

---

### 🔢 Step 1: Generate the NTLM Hash from the Password

**Command:**

```bash
python3 -c 'import hashlib; print(hashlib.new("md4", "kingdom".encode("utf-16le")).hexdigest())'
```

**What this does:**

| Part | Meaning |
|------|--------|
| `python3 -c` | Runs a Python command from the terminal |
| `import hashlib` | Loads the hashing library |
| `"kingdom".encode("utf-16le")` | NTLM uses the UTF-16LE (little-endian) format |
| `hashlib.new("md4", ...)` | NTLM is based on the MD4 hashing algorithm |
| `.hexdigest()` | Outputs the hash in readable hex format |

**Output:**

```
c0e84e870874dd37ed0d164c7986f03a
```

✅ This is the NTLM hash of the password `kingdom`.

---

### 📁 Step 2: Format the Hash for John the Ripper

John expects a specific format:

```
username:NTLM_hash
```

We’ll simulate a user named `user` and place this in a file.

**Command:**

```bash
echo "user:c0e84e870874dd37ed0d164c7986f03a" > ntlm_hashes.txt
```

**Explanation:**

| Part | Meaning |
|------|--------|
| `echo` | Prints text to the terminal |
| `>` | Redirects the output to a file |
| `ntlm_hashes.txt` | The file that will store our hash info |

✅ This creates a hash input file that John can read.

---

### 💥 Step 3: Crack the NTLM Hash with John the Ripper

**Command:**

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --format=NT ntlm_hashes.txt
```

**What this means:**

| Option | Purpose |
|--------|---------|
| `john` | Launches John the Ripper |
| `--wordlist=...` | Tells John to use the rockyou.txt wordlist |
| `--format=NT` | Specifies that we are cracking NT (NTLM) hashes |
| `ntlm_hashes.txt` | The file containing the hash we want to crack |

**Example Output:**

```
Loaded 1 password hash (NT [MD4 128/128 AVX 4x3])
Press 'q' or Ctrl-C to abort, almost any other key for status
kingdom          (user)
```

✅ John has cracked the hash and found that the password is `kingdom`.

---

### 📖 Step 4: Show Cracked Passwords

To see the cracked password(s) again:

**Command:**

```bash
john --show ntlm_hashes.txt
```

**Output:**

```
user:kingdom:c0e84e870874dd37ed0d164c7986f03a
```

✅ This confirms the username was `user` and their password was `kingdom`.

---

## 🧠 Key Concept Glossary

| Term | Meaning |
|------|---------|
| **NTLM** | Windows authentication hash based on MD4 and UTF-16LE encoding |
| **MD4** | A cryptographic hashing algorithm (not secure by modern standards) |
| **UTF-16LE** | Unicode encoding required by NTLM |
| **John the Ripper** | Open-source password-cracking tool |
| **rockyou.txt** | Common password list used for dictionary attacks |
| **Dictionary Attack** | Trying every word in a list against a hash |
| **Hash** | A one-way transformation of a password (not easily reversible) |
| **Hash Cracking** | Finding the original input (password) that produces a given hash |
| **`--format=NT`** | Tells John the hash is an NTLM (Windows NT) hash |
| **`--wordlist`** | Specifies which dictionary to use for the attack |

---

## 📄 File Structure

```
.
├── ntlm_hashes.txt         # Contains: user:c0e84e870874dd37ed0d164c7986f03a
├── README.md               # Summary of lab steps
└── WALKTHROUGH.md          # Full explanation (this file)
```

---

## 🛡️ Ethical Notice

This lab is intended for authorized training environments only.  
⚠️ **Do not perform password cracking on real systems without explicit permission.**

---

## 🧠 Summary

In this lab, you:

1. Generated the NTLM hash for `kingdom`
2. Saved the hash in a valid format for cracking
3. Used John the Ripper with `rockyou.txt` to crack the hash
4. Verified the recovered password

This exercise demonstrates the importance of using strong, unique passwords that don’t appear in common wordlists.

---

## ©️ Copyright

© 2025 Jaiden. All rights reserved.  
This walkthrough is for personal, academic, and authorized use only.

