# Cybersecurity Internship – Virtual Lab Setup & Linux Basics

## Overview

This repository documents my hands-on cybersecurity internship practical assignments focused on virtual lab setup, Linux system administration, networking, and basic penetration testing concepts. The lab environment was built using Oracle VM VirtualBox and multiple virtual machines including Kali Linux, Windows 10, and Metasploitable2. :contentReference[oaicite:0]{index=0}

The internship activities covered:
- Virtual machine setup
- Linux command-line practice
- Secure network configuration
- VM communication testing
- File system exploration
- Network monitoring
- Basic cybersecurity lab management

---

# Technologies & Tools Used

## Virtualization
- Oracle VM VirtualBox

## Operating Systems
- Kali Linux
- Windows 10
- Metasploitable2

## Networking & Security Tools
- Nmap
- Wireshark
- Netdiscover
- Burp Suite
- OWASP ZAP
- Nikto

## Linux Utilities
- apt
- grep
- chmod
- find
- ip addr
- ifconfig
- netstat

---

# Virtual Lab Architecture

The virtual cybersecurity lab was configured using a secure NAT Network / Host-Only Network inside VirtualBox.

## Virtual Machines

| Virtual Machine | Role | IP Address |
|---|---|---|
| Kali Linux | Attacker Machine | 192.168.xx.xxx |
| Metasploitable2 | Vulnerable Victim Machine | 192.168.xx.xxx |
| Windows 10 | User Simulation Machine | 192.168.xx.xxx |

---

# Network Topology

```text
                    +----------------------+
                    |      HOST PC         |
                    |      Windows         |
                    +----------------------+
                               |
                        Oracle VirtualBox
                               |
             VirtualBox NAT / Host-Only Network
                               |
        ------------------------------------------------
        |                     |                        |
        |                     |                        |
+----------------+   +----------------+   +----------------------+
|   Windows 10   |   |   Kali Linux   |   |  Metasploitable2    |
|   Virtual VM   |   | Attacker VM    |   |   Victim Machine    |
| 192.168.xx.xxx |   | 192.168.xx.xxx |   | 192.168.xx.xxx      |
|                |   |                |   |                     |
| User Simulation|   | Security Testing|  | Vulnerable Services |
| Browsing       |   | Reconnaissance |   | FTP / SSH / HTTP    |
| File Sharing   |   | Exploitation   |   |                     |
+----------------+   +----------------+   +----------------------+
```

---

# Internship Projects

## Project 1 – Build Your Virtual Lab Environment

### Tasks Performed
- Installed Oracle VM VirtualBox
- Configured Kali Linux VM
- Configured Windows 10 VM
- Configured Metasploitable2 VM
- Created NAT Network
- Tested VM connectivity using ping commands
- Configured secure isolated environment

### Skills Learned
- Virtualization
- VM configuration
- Network setup
- Troubleshooting
- Snapshot management

---

## Project 2 – Kali Linux Environment Exploration

### Tasks Performed
- Explored Kali Linux desktop environment
- Navigated application menus
- Explored Information Gathering tools
- Explored Vulnerability Analysis tools
- Explored Web Application Analysis tools
- Customized Kali Linux interface
- Updated Kali system using apt

### Commands Used

```bash
sudo apt update
```

```bash
sudo apt upgrade
```

```bash
whoami
```

```bash
uname -a
```

---

## Project 3 – Linux File System Treasure Hunt

### Tasks Performed
- Explored Linux directory structure
- Navigated /home, /etc, /var, /usr directories
- Practiced file navigation
- Explored file permissions
- Located configuration and log files

### Linux Directories Explored
- /home
- /etc
- /var
- /usr
- /bin
- /tmp
- /root

---

## Assignment 4 – Linux Command Line Bootcamp

### Commands Practiced

#### File Operations

```bash
ls
```

```bash
cd
```

```bash
mkdir
```

```bash
cp
```

```bash
mv
```

```bash
rm
```

#### System Information

```bash
ip addr
```

```bash
ifconfig
```

```bash
df -h
```

```bash
free -m
```

#### Permission Management

```bash
chmod 755 file.txt
```

```bash
chown user:user file.txt
```

---

## Project 5 – Secure Lab Configuration Challenge

### Tasks Performed
- Configured NAT Network
- Configured Host-Only Network
- Disabled clipboard sharing
- Created VM snapshots
- Configured SSH access
- Monitored traffic using Wireshark
- Tested network isolation

### Security Practices
- Isolated lab environment
- Safe penetration testing
- Controlled VM communication
- Snapshot recovery setup

---

# Connectivity Testing

Connectivity between all virtual machines was verified using ping commands.

## Example

### Kali Linux → Windows 10

```bash
ping 192.168.xx.xxx
```

### Kali Linux → Metasploitable2

```bash
ping 192.168.xx.xxx
```

---

# Challenges Faced During Setup

During lab configuration, several issues were encountered and resolved:

- VirtualBox XML configuration error
- NAT Network misconfiguration
- Windows 10 reinstall loop issue
- Network routing problems
- Windows Firewall blocking ping requests
- Duplicate IP configuration issue

These issues helped improve troubleshooting and networking skills.

---

# Learning Outcomes

Through this internship, I gained practical experience in:
- Linux administration
- Virtualization
- Networking fundamentals
- Virtual machine management
- Cybersecurity lab setup
- Basic penetration testing
- Troubleshooting
- Secure environment configuration

---

# Repository Structure

```text
cybersecurity-internship/
│
├── README.md
├── Project-1/
├── Project-2/
├── Project-3/
├── Project-4/
├── Project-5/

```

---

# Author

Sarfaraj Ahamad

---

# Disclaimer

This project was created strictly for educational and ethical cybersecurity learning purposes inside an isolated virtual lab environment.
