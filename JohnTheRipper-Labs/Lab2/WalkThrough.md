---

```markdown
# Lab 2 Walkthrough: Cracking a Password-Protected ZIP File

In this lab, I simulated a real-world password cracking scenario using a ZIP archive and John the Ripper.

---

## Objective

Crack the password of a ZIP file and retrieve its contents using John the Ripper and the RockYou wordlist.

---

## Walkthrough

1. **Created a Secret File**

I started by writing a message to a file using:

```bash
echo "This is a secret message." > secret.txt
```

2. **Encrypted the File in a ZIP**

I zipped the file using password protection:

```bash
zip -e secret.zip secret.txt
```

This prompted me to set a password.

3. **Converted ZIP to Hash**

I used `zip2john` to extract a crackable hash:

```bash
zip2john secret.zip > zip_hash.txt
```

4. **Cracked the Password with John**

I ran John with the RockYou wordlist to find the password:

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```

John successfully cracked the password.

5. **Displayed the Cracked Password**

To see the cracked credentials:

```bash
john --show zip_hash.txt
```

6. **Unzipped the File Using Cracked Password**

Finally, I extracted the contents:

```bash
unzip secret.zip
```

After entering the cracked password, I accessed the secret message.

7. **Viewed the Hidden Message**

```bash
cat secret.txt
```

It revealed: _"This is a secret message."_

---

## Summary

This lab demonstrated the full cycle of:

- Creating encrypted data
- Extracting a hash
- Using a wordlist to crack it
- Retrieving the data

It reinforced my understanding of how easily weak passwords can be broken with the right tools.

```
