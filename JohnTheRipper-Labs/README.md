## Walkthrough Overview

These labs simulate real-world password cracking scenarios using John the Ripper.  
Each walkthrough breaks down the process step-by-step:

### Lab 1: Crack SHA-512 Password (zuko:123456)
- Created SHA-512 hash using `openssl passwd -6`
- Saved it to `test_passwd.txt`
- Ran John the Ripper with default wordlist to crack the password
- Verified cracked credentials with `john --show`

> Outcome: Successfully cracked the hash and revealed password `123456` for user `zuko`

---

### Lab 2: Coming Soon
- (Planned) Cracking an MD5 hash using a custom hash file and dictionary attack

---

Each walkthrough includes commands, example files, and optional screenshots for clarity.
