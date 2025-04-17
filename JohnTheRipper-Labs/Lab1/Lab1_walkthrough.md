# John the Ripper Walkthrough

This walkthrough documents cracking a SHA-512 password hash for user `zuko` using John the Ripper in Kali Linux.

---

## Lab: Cracking a SHA-512 Password Hash for User Zuko

### Objective:
Crack a SHA-512 hashed password manually saved into `test_passwd.txt`.

### Steps:

1. Generated a SHA-512 password hash for `123456`:
   ```bash
   openssl passwd -6 123456
   ```

   Example output:
   ```
   $6$randomsalt$u1xN7...restOfTheHash
   ```

2. Opened `test_passwd.txt` to paste the hash:
   ```bash
   nano test_passwd.txt
   ```

3. Pasted the SHA-512 hash into the file and saved it:
   - CTRL + O to save
   - ENTER to confirm
   - CTRL + X to exit

4. Ran John the Ripper to crack the password:
   ```bash
   john --wordlist=/usr/share/wordlists/rockyou.txt test_passwd.txt
   ```

5. Displayed the cracked credentials:
   ```bash
   john --show test_passwd.txt
   ```

   Output:
   ```
   zuko:123456
   ```

### Screenshot:
![Cracked zuko's SHA-512 hash](./screenshots/John-zuko-crack.png)

---

## Notes

- `openssl passwd -6` generates SHA-512 hashes used in Linux shadow files.
- No need to specify a format — John detects the hash type automatically.
- `john --show` is useful to confirm which users/passwords were cracked.
```
