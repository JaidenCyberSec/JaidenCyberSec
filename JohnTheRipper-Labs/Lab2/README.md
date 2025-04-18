```markdown
# Lab 2: Cracking a Password-Protected ZIP File with John the Ripper

In this lab, I successfully cracked an encrypted `.zip` file using **John the Ripper** and revealed a hidden message.

---

## Steps Performed

### 1. Created the Secret File

```bash
echo "This is a secret message." > secret.txt
```

**Wrote a hidden message to a file.**

---

### 2. Encrypted It with a Password-Protected ZIP

```bash
zip -e secret.zip secret.txt
```

**Created a ZIP file that prompts for a password before opening.**

---

### 3. Extracted the Hash from the ZIP

```bash
zip2john secret.zip > zip_hash.txt
cat zip_hash.txt
```

**Pulled out the ZIP’s hash so it could be cracked by John the Ripper.**

---

### 4. Cracked the Password

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

**Used the rockyou.txt wordlist to run a dictionary attack.**  
✅ John found the password!

---

### 5. Revealed the Cracked Password

```bash
john --show zip_hash.txt
```

**Displayed the cracked password.**

---

### 6. Unzipped the File Using the Cracked Password

```bash
unzip secret.zip
```

**Entered the cracked password and successfully extracted `secret.txt`.**

---

### 7. Read the Secret Message

```bash
cat secret.txt
```

**Final message revealed:**
> _"This is a secret message."_

---

## What I Learned

- How to use `zip`, `zip2john`, and `john` together.
- How hash extraction from ZIP files works.
- How to perform a wordlist-based password cracking attack.
- Full encryption-to-decryption workflow.

---

## Tools Used

- Kali Linux  
- John the Ripper  
- RockYou wordlist  
- zip2john  
- unzip

---
```
