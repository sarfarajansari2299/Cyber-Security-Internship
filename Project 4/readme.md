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
ls -la
```

## Screenshot

```text
kali@kali:~$ ls
Documents  Downloads  Desktop

kali@kali:~$ ls -la
total 48
drwxr-xr-x 12 kali kali 4096 May 22 10:00 .
```

---

### Create Directories

```bash
mkdir LinuxLab
mkdir TestFolder
```

## Screenshot

```text
kali@kali:~$ mkdir LinuxLab
kali@kali:~$ mkdir TestFolder
```

---

### Change Directory

```bash
cd LinuxLab
pwd
```

## Screenshot

```text
kali@kali:~/LinuxLab$ pwd
/home/kali/LinuxLab
```

---

### Create Files

```bash
touch file1.txt
touch notes.txt
```

## Screenshot

```text
kali@kali:~/LinuxLab$ touch file1.txt
kali@kali:~/LinuxLab$ touch notes.txt
```

---

### Copy Files

```bash
cp file1.txt backup.txt
```

## Screenshot

```text
kali@kali:~/LinuxLab$ cp file1.txt backup.txt
```

---

### Move/Rename Files

```bash
mv backup.txt newbackup.txt
```

## Screenshot

```text
kali@kali:~/LinuxLab$ mv backup.txt newbackup.txt
```

---

### Delete Files

```bash
rm newbackup.txt
```

## Screenshot

```text
kali@kali:~/LinuxLab$ rm newbackup.txt
```

---

### Remove Directory

```bash
cd ..
rmdir TestFolder
```

## Screenshot

```text
kali@kali:~$ rmdir TestFolder
```

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

```text
Linux Command Line Practice
Cyber Security Lab
```

---

### View File Using less

```bash
less notes.txt
```

## Screenshot

```text
Linux Command Line Practice
Cyber Security Lab
~
~
(END)
```

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

```text
Cyber Security Lab
```

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

```text
Linux Basics
Advanced Linux Commands
```

---

## d. Edit File Using nano

### Command

```bash
nano notes.txt
```

## Screenshot

```text
GNU nano 7.2               notes.txt

Linux Command Line Practice
Cyber Security Lab
```

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

```text
kali
```

---

### Hostname

```bash
hostname
```

## Screenshot

```text
kali-linux
```

---

### Kernel Information

```bash
uname -a
```

## Screenshot

```text
Linux kali-linux 6.6.9-amd64 x86_64 GNU/Linux
```

---

### Disk Usage

```bash
df -h
```

## Screenshot

```text
Filesystem      Size  Used Avail Use%
/dev/sda1        50G   18G   30G  38%
```

---

### Memory Usage

```bash
free -m
```

## Screenshot

```text
              total   used   free
Mem:           4096   2100   1996
```

---

## b. Process and Network Commands

### Running Processes

```bash
ps aux
```

---

### Real-Time Process Monitoring

```bash
top
```

---

### Network Configuration Using ifconfig

```bash
ifconfig
```

## Screenshot

```text
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>
inet 10.0.2.15
```

---

### IP Address Using ip addr

```bash
ip addr
```

## Screenshot

```text
2: eth0:
inet 10.0.2.15/24
```

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

```text
/home/kali/LinuxLab/notes.txt
```

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

```text
/home/kali/LinuxLab/notes.txt
```

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

```text
-rwxr-xr-x 1 kali kali script.sh
-rw-r--r-- 1 kali kali notes.txt
-rwxrwxrwx 1 kali kali demo.txt
```

---

## d. Change Ownership Using chown

### Command

```bash
sudo chown kali:kali notes.txt
```

## Screenshot

```text
Ownership changed successfully
```

---

## Observation

Linux permissions and ownership provide strong access control mechanisms for system security and file protection.

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

```text
Sorting... Done
Full Text Search... Done
nmap/kali-rolling
```

---

## b. Install Packages

### Command

```bash
sudo apt install nmap
```

## Screenshot

```text
Setting up nmap...
Installation completed successfully.
```

---

## c. Remove Packages

### Command

```bash
sudo apt remove nmap
```

## Screenshot

```text
Removing nmap...
Done.
```

---

## d. Update System

### Command

```bash
sudo apt update && sudo apt upgrade
```

## Screenshot

```text
Reading package lists... Done
Calculating upgrade... Done
```

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

