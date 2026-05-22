# ASSIGNMENT 4: LINUX COMMAND LINE BOOTCAMP

## Objective

The objective of this assignment is to practice essential Linux command line operations including file management, text processing, system monitoring, file permissions, and package management using Kali Linux.

---

# 1. File and Directory Operations

## Objective

Learn basic Linux commands for managing files and directories.

---

## a. Commands Practiced

| Command | Purpose                    |
| ------- | -------------------------- |
| `ls`    | List files and directories |
| `cd`    | Change directory           |
| `pwd`   | Show current directory     |
| `mkdir` | Create directory           |
| `rmdir` | Remove empty directory     |
| `touch` | Create empty file          |
| `cp`    | Copy files/directories     |
| `mv`    | Move or rename files       |
| `rm`    | Delete files/directories   |

---

## Practical Commands

### Check Current Directory

```bash
pwd
```

## Screenshot

<img width="503" height="201" alt="image" src="https://github.com/user-attachments/assets/da4ee60d-59e9-449d-b9a9-ca5e5e1301af" />



---

### List Files and Directories

```bash
ls

```

## Screenshot


<img width="512" height="288" alt="image" src="https://github.com/user-attachments/assets/67417312-4eea-4756-a12a-2ab641668ffa" />

---

### Create Directories

```bash
mkdir LinuxLab
mkdir TestFolder
```

## Screenshot

<img width="937" height="657" alt="image" src="https://github.com/user-attachments/assets/59649192-d0fc-4729-a88e-317f9c148eb1" />
<img width="1057" height="822" alt="image" src="https://github.com/user-attachments/assets/2cf34c3c-9cb1-43cf-812f-8908d542e801" />



---

### Change Directory

```bash
cd LinuxLab
pwd
```

## Screenshot

<img width="1057" height="822" alt="image" src="https://github.com/user-attachments/assets/eb34b116-d437-40c9-b6b8-cd27ee4cd8a1" />


---

### Create Files

```bash
touch file1.txt
touch notes.txt
```

## Screenshot

<img width="1057" height="822" alt="image" src="https://github.com/user-attachments/assets/401c5bee-d3d4-4604-a7ba-51eb196c883e" />


### Copy Files

```bash
cp file1.txt backup.txt
```

## Screenshot

<img width="1057" height="822" alt="image" src="https://github.com/user-attachments/assets/05bec2a3-dbbd-4d0b-8470-d71753b33e36" />


---

### Move/Rename Files

```bash
mv backup.txt newbackup.txt
```

## Screenshot

<img width="1057" height="822" alt="image" src="https://github.com/user-attachments/assets/5aa97cef-db8c-4c0f-bec7-d6843bccda8c" />

---

### Delete Files

```bash
rm newbackup.txt
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/ad039cb1-ece7-44b2-b810-e9c22337489f" />


---

### Remove Directory

```bash
cd ..
rmdir TestFolder
```

## Screenshot

<img width="1196" height="1017" alt="image" src="https://github.com/user-attachments/assets/cc0e2213-81e2-402a-8b99-17865bfe0df3" />

---

## Observation

Linux provides powerful command-line tools for file and directory management. These commands help users efficiently create, organize, move, and delete files and folders.

---

# 2. Text File Manipulation

## Objective

Learn to view, search, edit, and write text files using Linux commands.

---

## a. Viewing File Content

### Create Sample File

```bash
echo "Linux Command Line Practice" > notes.txt
echo "Cyber Security Lab" >> notes.txt
```

---

### View File Using cat

```bash
cat notes.txt
```

## Screenshot

<img width="1230" height="1017" alt="image" src="https://github.com/user-attachments/assets/7c0e431d-02ab-4b6d-9f1b-8b8ae6a937ee" />


---

### View File Using less

```bash
less notes.txt
```

## Screenshot

<img width="1351" height="1017" alt="image" src="https://github.com/user-attachments/assets/9d766f9a-ef41-4366-b349-e47b83ebce30" />


---

### View File Using more

```bash
more notes.txt
```

---

### View First Lines Using head

```bash
head notes.txt
```

---

### View Last Lines Using tail

```bash
tail notes.txt
```

---

## b. Search Text Using grep

### Command

```bash
grep "Cyber" notes.txt
```

## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/0a4192ac-a3fa-4b53-ba24-15523389dfc9" />


<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/084328c2-f58e-47d6-af9a-98fb6fe6907e" />

<img width="1246" height="1017" alt="image" src="https://github.com/user-attachments/assets/80264264-602c-4169-b7b6-1fbf0a21586a" />

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/ff42d091-dfe8-486e-9912-12dfee22903f" />


---

## c. Echo and Redirection

### Overwrite File

```bash
echo "Linux Basics" > demo.txt
```

### Append Data

```bash
echo "Advanced Linux Commands" >> demo.txt
```

## Screenshot
<img width="1235" height="1017" alt="image" src="https://github.com/user-attachments/assets/419355e7-24cd-413d-a0f6-4aa2d8efbc19" />

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/5b528531-b445-431e-a391-de78371dfe4c" />


---

## d. Edit File Using nano

### Command

```bash
nano notes.txt
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/bce65bc7-64c3-4aa7-a5d2-d957f1f332bc" />


---

## Observation

Linux text processing commands help users efficiently view, search, and edit files directly from the terminal.

---

# 3. System Information Commands

## Objective

Learn commands used for checking system information, memory usage, running processes, and network configuration.

---

## a. User and System Information

### Current User

```bash
whoami
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/c31d645d-ff6c-4c48-9c34-ee9ee9fa9b23" />

---

### Hostname

```bash
hostname
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/720de967-ea7c-4a64-8e5e-7ccb1f2c2db4" />


---

### Kernel Information

```bash
uname -a
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/0ccb9408-4ecc-4f04-be7b-be9830cd983c" />


---

### Disk Usage

```bash
df -h
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/783ba134-8a64-4380-9841-d0fed8f9cb29" />


---

### Memory Usage

```bash
free -m
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/28f2a0c9-31ad-468c-90d9-36b8df2018a7" />

---

## b. Process and Network Commands

### Running Processes

```bash
ps aux
```


## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/07f7c91d-8e6d-4e59-b323-7f8b9ad4ef8c" />

---
### Real-Time Process Monitoring

```bash
top
```
## Screenshot

<img width="1068" height="1017" alt="image" src="https://github.com/user-attachments/assets/bc248dc3-69f2-4e44-aacd-f4d58b6c514a" />

---

### Network Configuration Using ifconfig

```bash
ifconfig
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/581e7b40-fe6a-4aa4-ab9d-663d3b03c4d7" />


---

### IP Address Using ip addr

```bash
ip addr
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/3b27a596-2e94-45fc-8cc4-fb74f098e956" />


---

## Observation

System information commands provide detailed insights into Linux system performance, hardware usage, and network connectivity.

---

# 4. File Search and Permissions

## Objective

Learn how to search for files and manage Linux file permissions.

---

## a. Find Files Using find

### Command

```bash
find /home/kali -name notes.txt
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/451fcf06-fc3c-4827-a70b-f317ac5f7771" />


---

## b. Locate Files Using locate

### Update Database

```bash
sudo updatedb
```

### Search File

```bash
locate notes.txt
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/897fabd7-29da-4df9-8f39-ef1b5a046772" />


---

## c. Change File Permissions Using chmod

### Permission 755

```bash
chmod 755 script.sh
```

### Permission 644

```bash
chmod 644 notes.txt
```

### Permission 777

```bash
chmod 777 demo.txt
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/5c3e2262-f9e1-4a5d-85cb-db7ca52fb6b3" />


---

# 5. Package Management

## Objective

Learn how to manage software packages in Linux using APT package manager.

---

## a. Search for Packages

### Command

```bash
apt search nmap
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/aac3ebf5-eaa8-41c5-b7de-757ac86fa11c" />


---

## b. Install Packages

### Command

```bash
sudo apt install nmap
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/e51850a9-6584-4d66-86e9-bf2d8dcdede0" />


---

## c. Remove Packages

### Command

```bash
sudo apt remove nmap
```

## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/18443490-d9d8-4eee-be62-9e55d527e83b" />


---

## d. Update System

### Command

```bash
sudo apt update && sudo apt upgrade
```

## Screenshot

<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/273ea0e5-a889-42a9-b4e2-f925ceb116db" />


---

## Observation

APT package management allows users to install, update, and remove software efficiently in Debian-based Linux distributions like Kali Linux.

---

# Challenges Faced

| Problem                    | Solution                          |
| -------------------------- | --------------------------------- |
| Permission denied errors   | Used sudo privileges              |
| locate command not working | Ran updatedb command              |
| Package installation slow  | Updated repository mirrors        |
| File permission confusion  | Practiced chmod values repeatedly |

---

# Conclusion

In this assignment, essential Linux command line operations were successfully practiced using Kali Linux. Various commands related to file management, text processing, system monitoring, permissions, and package management were executed and verified successfully.

This bootcamp improved practical Linux administration and command-line skills required for cybersecurity and system administration tasks.

---

# Tools and Platforms Used

* Kali Linux
* Linux Terminal
* APT Package Manager
* Nano Text Editor

---

# Author

sarfaraj Ahamad

