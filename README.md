# Cybersecurity Internship – Virtual Lab Setup & Linux Basics

## Overview

This repository documents my hands-on cybersecurity internship practical assignments focused on virtual lab setup, Linux system administration, networking, and basic penetration testing concepts. The lab environment was built using Oracle VM VirtualBox and multiple virtual machines including Kali Linux, Windows 10, and Metasploitable2. 

## The internship activities covered:

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

## Assignment 1 – Build Your Virtual Lab Environment

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

## Assignment 2 – Kali Linux Environment Exploration

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

## Assignment 3 – Linux File System Treasure Hunt

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

## Assignment 5 – Secure Lab Configuration Challenge

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


# Assignment 6: Network Mapping & IP Address Mastery

## Learning Outcomes

* IP Addressing
* Subnetting
* Network Discovery
* Protocol Identification



### 1. Network Discovery

* Used `Nmap` to scan virtual lab network
* Identified active hosts and IP addresses
* Detected open ports and services
* Created network topology diagram

### 2. IP Addressing Practice

* Configured static IPv4 addresses
* Practiced subnetting calculations
* Configured IPv6 on one VM
* Tested inter-subnet connectivity

### 3. Protocol Identification

* Captured packets using Wireshark
* Identified protocols:

  * TCP
  * UDP
  * ICMP
  * ARP
  * DNS
  * HTTP
* Analyzed packet headers and payloads
* Applied protocol filters

### 4. Port Exploration

Scanned common ports:

| Port | Service |
| ---- | ------- |
| 21   | FTP     |
| 22   | SSH     |
| 23   | Telnet  |
| 25   | SMTP    |
| 53   | DNS     |
| 80   | HTTP    |
| 443  | HTTPS   |
| 3389 | RDP     |
| 445  | SMB     |

### Useful Commands

```bash
# Basic Nmap Scan
nmap 192.168.1.0/24

# Service Detection
nmap -sV 192.168.1.1

# Ping Test
ping google.com
```

---

# Assignment 7: Protocol Analysis with Wireshark

## Learning Outcomes

* Network Protocol Analysis
* Packet Inspection
* Traffic Monitoring

### Packet Capture

* Captured HTTP traffic
* Generated DNS traffic using `nslookup`
* Captured ICMP packets using `ping`
* Observed SSH/Telnet sessions

### Deep Packet Inspection

* Followed TCP streams
* Analyzed TCP three-way handshake:

  * SYN
  * SYN-ACK
  * ACK
* Identified HTTP GET & POST requests
* Extracted HTTP transferred files

### Wireshark Filters Used

```bash
tcp
udp
http
dns
arp
icmp
```

### Filter by IP

```bash
ip.addr == 192.168.1.10
```

### Filter by Port

```bash
tcp.port == 80
```

### Combined Filters

```bash
http && ip.addr == 192.168.1.10
```

---

# Assignment 8: Windows Login Bypass Techniques

##  Learning Outcomes

* Desktop Security
* Authentication Bypass
* Password Recovery

## ⚠️ Educational Purpose Only

Performed only in a controlled virtual lab environment.

## Techniques Practiced

### Sticky Keys Bypass

* Booted Windows VM using Linux live ISO
* Backed up `sethc.exe`
* Replaced with `cmd.exe`
* Triggered Sticky Keys at login screen

### chntpw Password Reset

* Mounted Windows partition
* Viewed user accounts
* Reset/Cleared passwords

### Utilman.exe Bypass

* Replaced `utilman.exe`
* Opened system-level CMD from login screen

### Ophcrack Password Recovery

* Booted using Ophcrack Live CD
* Observed rainbow table attack

### VM Snapshot Practice

* Created snapshots before testing
* Restored clean VM state after experiments

---

#  Assignment 9: Password Attack Lab

##  Learning Outcomes

* Password Cracking
* Dictionary Attacks
* Offline & Online Attacks


### Offline Password Cracking

* Extracted password hashes
* Used:

  * John the Ripper
  * Hashcat
* Performed dictionary attacks using `rockyou.txt`

### Hash Identification

Identified:

* MD5
* SHA1
* SHA256
* NTLM

### Online Attack Simulation

* Configured DVWA
* Used Hydra for brute-force attacks
* Monitored successful/failed attempts

### Custom Wordlists

Generated wordlists using:

* Crunch
* CeWL

### Defense Analysis

* Compared weak vs strong passwords
* Observed attack speed differences

---

#  Assignment 10: VPN, Proxy & DNS Configuration Lab

##  Learning Outcomes

* VPN Configuration
* Proxy Setup
* DNS Manipulation
* Traffic Anonymization


### VPN Setup

* Installed OpenVPN/WireGuard
* Connected using ProtonVPN
* Verified IP address changes
* Tested DNS leaks

### Proxy Configuration

* Configured FoxyProxy
* Used Burp Suite as intercepting proxy
* Modified HTTP requests

### DNS Practice

Used:

```bash
nslookup
dig
```

Queried:

* A Records
* AAAA Records
* MX Records
* NS Records
* TXT Records

Configured DNS servers:

```bash
8.8.8.8
1.1.1.1
```

### DNS Spoofing Demo

* Modified `/etc/hosts`
* Redirected domains locally
* Demonstrated DNS cache poisoning concepts

### Tor Network

* Installed Tor Browser
* Explored `.onion` services
* Observed multi-hop routing

---

#  Tools Used

| Tool            | Purpose             |
| --------------- | ------------------- |
| Kali Linux      | Penetration Testing |
| Wireshark       | Packet Analysis     |
| Nmap            | Network Scanning    |
| Burp Suite      | Web Proxy           |
| Hydra           | Brute Force Testing |
| John the Ripper | Password Cracking   |
| Hashcat         | GPU Cracking        |
| DVWA            | Vulnerable Web App  |
| OpenVPN         | VPN Testing         |
| Tor Browser     | Anonymous Browsing  |

---

# ⚠️ Disclaimer

This project is created strictly for:

* Educational purposes
* Ethical hacking practice
* Cybersecurity lab simulations

Do not use these techniques on unauthorized systems.


# Author

Sarfaraj Ahamad

---
