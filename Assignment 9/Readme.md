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


<img width="1280" height="1032" alt="1" src="https://github.com/user-attachments/assets/b0e9031d-2ac1-4f54-a7a0-046d7f7e2d5f" />


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

<img width="1280" height="1032" alt="1" src="https://github.com/user-attachments/assets/f17e4f41-ca00-463e-9142-8989a275c07e" />



---


## Results

* Successfully loaded the RockYou password wordlist.
* Performed a dictionary attack against extracted password hashes.
* Tested millions of commonly used passwords.
* Recovered multiple weak passwords from the target system.
* Demonstrated the effectiveness of dictionary-based password attacks. However Password not found from the rockyou.text.

---

## Observation

Dictionary attacks are significantly faster than brute-force attacks because they use previously leaked and commonly used passwords. Weak passwords are often cracked within seconds when included in large password databases such as RockYou.

---

## Conclusion

The RockYou wordlist successfully demonstrated how attackers can leverage publicly available password databases to recover weak credentials. The exercise highlights the importance of strong, unique passwords and proper password management practices to defend against dictionary-based attacks.

# 1(d) Brute Force Attack with Custom Rules

## Objective

Perform a brute-force password attack using John the Ripper's rule-based and incremental cracking modes to understand how automated password generation techniques can recover weak passwords.

---

## Step 1: Create a Custom Wordlist

### Command

```bash
nano custom_words.txt
```

### Wordlist Contents

```text
admin
password
user
service
msfadmin
root
```

### Verify

```bash
cat custom_words.txt
```

### Purpose

Create a small custom wordlist containing common usernames and passwords that will be used during the rule-based password attack.

### Screenshot

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/0e9fbea7-e392-4ddd-993c-d693ac837334" />

---

## Step 3: Display Cracked Passwords

### Command

```bash
john --show hashes.txt
```

### Purpose

Display all passwords successfully recovered during the rule-based attack.

### Screenshot

















---

## Step 4: Perform Incremental Brute Force Attack

### Command

```bash
john --incremental hashes.txt
```

### Purpose

Generate password combinations automatically and attempt to crack hashes through exhaustive search.

### Note

Allow the attack to run for 1–2 minutes and then stop it using:

```text
CTRL + C
```

### Screenshot

Insert screenshot showing incremental mode running.

---

## Step 5: Review Results

### Command

```bash
john --show hashes.txt
```

### Purpose

Review the final list of cracked passwords after the brute-force attack.

### Screenshot

Insert screenshot showing the final cracking results.

---

## Results

* Successfully created a custom password wordlist.
* Executed a rule-based password attack using John the Ripper.
* Generated multiple password variations automatically.
* Performed an incremental brute-force attack.
* Demonstrated the effectiveness of automated password-cracking techniques.

---

## Observation

Rule-based attacks are significantly faster than pure brute-force attacks because they generate realistic password variations from known words. Incremental brute-force attacks require more time and computational resources but can discover passwords that do not exist in standard dictionaries.

---

## Conclusion

John the Ripper successfully demonstrated both rule-based and brute-force password-cracking techniques. The exercise highlighted how weak passwords can be recovered through automated password generation and exhaustive search methods, emphasizing the importance of strong password policies and complexity requirements.

---

## Commands Summary

```bash
nano custom_words.txt

cat custom_words.txt

john --wordlist=custom_words.txt --rules hashes.txt

john --show hashes.txt

john --incremental hashes.txt

john --show hashes.txt
```
