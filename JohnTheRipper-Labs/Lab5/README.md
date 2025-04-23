# 🔐 Lab 5 – Cracking an NTLM Hash with John the Ripper

## 🧠 Objective

In this lab, we demonstrate how to crack an NTLM hash using **John the Ripper** and the **rockyou.txt** wordlist. This simulates a real-world scenario where weak passwords can be exposed through dictionary attacks.

---

## 🛠️ Tools Used

- **John the Ripper** – password cracking tool  
- **rockyou.txt** – common password wordlist  
- **Python 3** – to generate an NTLM hash  

---

## 🧪 Steps

### ✅ Step 1: Generate the NTLM Hash

We used Python to hash the password `kingdom` using the NTLM (MD4 + UTF-16LE) format:

```bash
python3 -c 'import hashlib; print(hashlib.new("md4", "kingdom".encode("utf-16le")).hexdigest())'
```

**Output:**
```
c0e84e870874dd37ed0d164c7986f03a
```

---

### ✅ Step 2: Create the NTLM Hash File

We formatted the hash into a file that John the Ripper can read. NTLM hashes are placed in `username:hash` format without special prefixes.

```bash
echo "user:c0e84e870874dd37ed0d164c7986f03a" > ntlm_hashes.txt
```

🛑 **Note:** No `$1$`, `$NT$`, or any prefix is used. This is a raw NT hash.

---

### ✅ Step 3: Crack the Hash

Run John the Ripper using the `rockyou.txt` wordlist and specify the correct format for NTLM hashes:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt --format=NT ntlm_hashes.txt
```

---

### ✅ Step 4: View the Cracked Password

After cracking, we confirm the result with:

```bash
john --show ntlm_hashes.txt
```

**Output:**
```
user:kingdom:c0e84e870874dd37ed0d164c7986f03a
```

✅ Success – the password `kingdom` was found in the wordlist.

---

## 🔍 Summary

| Item | Details |
|------|---------|
| **Password** | `kingdom` |
| **Hash Type** | NTLM (MD4 + UTF-16LE) |
| **Wordlist** | `/usr/share/wordlists/rockyou.txt` |
| **Cracking Tool** | John the Ripper |
| **Result** | Password cracked successfully |

---

## 🧠 Key Takeaways

- Weak passwords like `kingdom` are easily cracked using public wordlists.
- NTLM hashes are fast to compute and vulnerable to dictionary attacks.
- Always use strong, unique, randomly generated passwords in practice.
