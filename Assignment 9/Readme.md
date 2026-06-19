# a. Extract Password Hashes from Metasploitable2

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

# b. Use John the Ripper to Crack Passwords

## Objective

Use John the Ripper to perform offline password cracking against the password hashes extracted from Metasploitable2.

---

## Step 1: Verify John the Ripper Installation

### Command

```bash
john --version
```

### Purpose

Verify that John the Ripper is installed and available on the Kali Linux system.


---

## Step 2: Verify Hash File

### Commands

```bash
cd ~/PasswordLab
ls -la
```

```bash
cat hashes.txt
```

### Purpose

Confirm that the combined password hash file was successfully created and is ready for password cracking.

---

## Step 3: Start Password Cracking

### Command

```bash
john hashes.txt
```

### Purpose

Run John the Ripper in default mode to automatically identify and crack weak passwords stored in the hash file.

### Screenshot

<img width="1280" height="1032" alt="image" src="https://github.com/user-attachments/assets/48b90b1d-42b7-4d83-9a58-7744fd2da43b" />


---

## Results

* Successfully loaded password hashes extracted from Metasploitable2.
* Identified the hash format automatically using John the Ripper.
* Recovered multiple weak passwords from the hash database.


---

## Observation

John the Ripper successfully cracked several weak passwords within a short period of time. Systems that rely on weak or predictable passwords are highly vulnerable to offline password attacks once password hashes are obtained. This demonstrates the importance of strong password policies and secure password storage mechanisms.

---

## Conclusion

Password hashes extracted from Metasploitable2 were successfully analyzed and cracked using John the Ripper. The exercise demonstrated how attackers can recover weak passwords from compromised hash databases and highlighted the importance of strong password complexity requirements and proper security controls.

# c. Dictionary Attack Using rockyou.txt

## Objective

Perform a dictionary attack against extracted password hashes using the RockYou password wordlist and evaluate the effectiveness of common password dictionaries in recovering weak credentials.

---

## Step 1: Verify RockYou Wordlist

### Command

```bash
ls -lh /usr/share/wordlists/
```

### Purpose

Verify that the RockYou wordlist is available on the Kali Linux system.

### Screenshot



---

## Step 2: Extract the Wordlist

### Command

```bash
sudo gzip -d /usr/share/wordlists/rockyou.txt.gz
```

### Verify

```bash
ls -lh /usr/share/wordlists/rockyou.txt
```

### Purpose

Extract the compressed RockYou password database for use in the dictionary attack.

### Screenshot

Insert screenshot showing successful extraction of the RockYou wordlist.

---


## Step 4: Execute Dictionary Attack

### Navigate to Lab Directory

```bash
cd ~/PasswordLab
```

### Command

```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

### Purpose

Perform a dictionary attack by comparing passwords in the RockYou wordlist against the extracted password hashes.

### Screenshot







---

## Step 5: Display Cracked Passwords

### Command

```bash
john --show hashes.txt
```

### Sample Output

```text
msfadmin:msfadmin
postgres:postgres
service:service
user:user
```

### Purpose

Display all passwords successfully recovered during the dictionary attack.

### Screenshot

Insert screenshot showing the cracked passwords.

---

## Step 6: Save Results

### Commands

```bash
john --show hashes.txt > rockyou_results.txt
```

```bash
cat rockyou_results.txt
```

### Purpose

Save recovered credentials to a text file for documentation and analysis.

### Screenshot

Insert screenshot showing the contents of `rockyou_results.txt`.

---

## Results

* Successfully loaded the RockYou password wordlist.
* Performed a dictionary attack against extracted password hashes.
* Tested millions of commonly used passwords.
* Recovered multiple weak passwords from the target system.
* Demonstrated the effectiveness of dictionary-based password attacks.

---

## Observation

Dictionary attacks are significantly faster than brute-force attacks because they use previously leaked and commonly used passwords. Weak passwords are often cracked within seconds when included in large password databases such as RockYou.

---

## Conclusion

The RockYou wordlist successfully demonstrated how attackers can leverage publicly available password databases to recover weak credentials. The exercise highlights the importance of strong, unique passwords and proper password management practices to defend against dictionary-based attacks.

