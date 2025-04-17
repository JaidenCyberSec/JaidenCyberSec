# John the Ripper Labs
 
 This folder contains my hands-on labs using John the Ripper to crack SHA-512 password hashes. The lab demonstrates cracking a password hash for the user `zuko` from `test_passwd.txt`.
 
 ---
 
 ## Tools & Technologies Used
 - Kali Linux
 - John the Ripper
 - rockyou.txt wordlist
 
 ---
 
 ## Lab Breakdown
 
 1. **Lab: Cracking a SHA-512 Password Hash**
    - **Objective**: Crack a SHA-512 password hash saved in `test_passwd.txt`.
    - **Steps**:
      1. Generated the SHA-512 hash for `123456` using `openssl`.
      2. Manually saved the hash in `test_passwd.txt`.
      3. Cracked the password using John the Ripper with the RockYou wordlist.
      4. Used `john --show` to display the cracked password.
 
    - **Outcome**:
      - Username: `zuko`
      - Password: `123456`
 
    - [Link to walkthrough.md](./walkthrough.md)
 
 ---
 
 ## Notes
 - This lab demonstrates using `openssl` to create SHA-512 password hashes and cracking them using John the Ripper.
 - The `john --show` command is essential for displaying cracked passwords after the cracking process.
 - Screenshots from the lab are included in the screenshots folder.
 
 ---
 
 ## Screenshot:
 ![Cracked zuko's SHA-512 hash](./JohnTheRipper-Labs/Lab1/John-zuko-crack.png)
