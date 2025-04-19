# Walkthrough: Cracking Linux Passwords with John the Ripper

This walkthrough simulates a real-world scenario where an attacker gains access to a Linux system and attempts to crack a user’s password using **John the Ripper**.

---

## Scenario

You’ve obtained the system’s `passwd` and `shadow` files after privilege escalation. Your mission is to:
- Simulate realistic Linux user data
- Hash a known password
- Use `unshadow` and `John` to crack it

---

## Step 1: Set Up the Lab

Create a fresh working directory:

```bash
mkdir john-shadow-lab && cd john-shadow-lab
```

This helps keep your files clean and isolated.

---

## Step 2: Create a Fake passwd File

We're faking a Linux user named **Kuzan**:

```bash
echo 'kuzan:x:1001:1001:Kuzan:/home/kuzan:/bin/bash' > passwd.txt
```

- `kuzan` = username  
- `x` = placeholder for password (points to shadow file)  
- `1001:1001` = UID and GID  
- `/home/kuzan` = home directory  
- `/bin/bash` = default shell

---

## Step 3: Generate a Password Hash

Use OpenSSL to hash the password **anime** using SHA-512 (`-6`):

```bash
openssl passwd -6 anime
```

You’ll get something like:

```
$6$Z12vX9pN$72XILsGb...lVYu/.R/
```

Copy that entire hash.

---

## Step 4: Create a Matching shadow File

Paste the copied hash here:

```bash
echo 'kuzan:$6$Z12vX9pN$72XILsGb...lVYu/.R/:19000:0:99999:7:::' > shadow.txt
```

- `19000` = last changed (days since epoch)
- `99999` = max password age
- `7` = warning days

---

## Step 5: Combine the Files with unshadow

This prepares the format John needs:

```bash
unshadow passwd.txt shadow.txt > unshadowed.txt
```

This merges the two files into one with full user + hash info.

---

## Step 6: Crack the Password

Use `rockyou.txt`, one of the most common wordlists:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt unshadowed.txt
```

John starts checking every password until it finds **anime**.

---

## Step 7: Reveal the Cracked Password

Once finished, show the result:

```bash
john --show unshadowed.txt
```

You’ll see:

```
kuzan:anime
```

Boom — password cracked!

---

## What You Learned

- How Linux stores and separates user/password info
- How SHA-512 password hashes work
- How to simulate cracking hashes safely
- Wordlist-based password cracking with John the Ripper

---

## Cleanup

Want to do it again? Delete the lab folder:

```bash
cd ..
rm -rf john-shadow-lab
```

---

## About the Author

**Jaiden**  
Cybersecurity student | Ethical hacker in training  
[X (Twitter)](https://twitter.com/JaidenCyberSec) | [LinkedIn](https://linkedin.com/in/jaiden)

---

## Disclaimer

This lab is for **educational purposes only**. Do not use these techniques on live systems without permission.
