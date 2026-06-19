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



