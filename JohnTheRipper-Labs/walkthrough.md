# 🧠 Walkthrough Overview  
📜 **Author**: Jaiden Jimerson  
©️ 2025 Jaiden Jimerson. All rights reserved.

These labs simulate real-world password cracking scenarios using **John the Ripper**.  
Each walkthrough breaks down the process step-by-step, helping you understand how password security can be broken when poor practices are used.

---

### ✅ Lab 1: Crack SHA-512 Password (zuko:123456)

- Created SHA-512 hash using `openssl passwd -6`
- Saved it to `test_passwd.txt`
- Ran John the Ripper with default wordlist to crack the password
- Verified cracked credentials with `john --show`

> 🔓 **Outcome**: Successfully cracked the hash and revealed password `123456` for user `zuko`

---

### ✅ Lab 2: Crack Password-Protected ZIP File

- Created a file `secret.txt` with hidden content
- Encrypted the file with `zip -e secret.zip secret.txt`
- Used `zip2john` to extract a hash and fed it to John the Ripper
- Cracked the password using the `rockyou.txt` wordlist
- Verified and unzipped the file with the recovered password

> 🔓 **Outcome**: Password cracked and hidden message revealed from the ZIP

---

### ✅ Lab 3: Crack SHA-512 Hash for Custom User (kuzan:anime)

- Created fake `passwd` and `shadow` files for user `kuzan`
- Generated a SHA-512 password hash using `openssl passwd -6 anime`
- Used `unshadow` to merge files into a John-readable format
- Ran John with the `rockyou.txt` wordlist
- Verified successful cracking using `john --show`

> 🔓 **Outcome**: Cracked password for user `kuzan` — the password was `anime`

---

### ✅ Lab 4: Crack Unsalted MD5 Hash (hunter2)

- Generated a raw MD5 hash using `echo -n "hunter2" | md5sum`
- Saved the hash into a file named `md5hash.txt`
- Ran John the Ripper with `--format=raw-md5` using `rockyou.txt`
- Revealed password successfully using `john --show`

> 🔓 **Outcome**: Cracked raw MD5 hash — the password was `hunter2`

---

Each walkthrough is beginner-friendly and designed to reinforce ethical hacking fundamentals and password auditing techniques.  

More labs coming soon! 🧪

