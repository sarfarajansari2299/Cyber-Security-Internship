# Downloading and Setting Up Virtual Machines

## Objective
The objective of this task was to download and configure multiple virtual machines for building a secure cybersecurity lab environment using VirtualBox.

---

# Virtual Machines Used

## 1. Kali Linux

### Description
Kali Linux is a Debian-based Linux distribution designed for penetration testing, ethical hacking, and cybersecurity analysis.

### Download Source
https://www.kali.org/

### Configuration
- RAM Allocated: 2 GB
- Storage: 50 GB (Dynamically Allocated)
- Network Mode: NAT Network
- Processor: 2 CPU Cores

### Purpose
Used for:
- Penetration testing
- Network analysis
- Linux command-line practice
- Security tool exploration

---

## 2. Metasploitable2

### Description
Metasploitable2 is an intentionally vulnerable Linux virtual machine used for practicing penetration testing and vulnerability assessment in a safe lab environment.

### Download Source
https://sourceforge.net/projects/metasploitable/

### Configuration
- RAM Allocated: 1 GB
- Storage: Default VMDK
- Network Mode: NAT Network

### Purpose
Used for:
- Vulnerability testing
- Exploitation practice
- Network scanning
- Learning ethical hacking techniques

---

## 3. Windows 10 Evaluation VM

### Description
Windows 10 Evaluation VM was installed for testing Windows-based environments and performing cross-platform networking practice.

### Download Source
https://www.microsoft.com/software-download/windows10

### Configuration
- RAM Allocated: 4 GB
- Storage: 64 GB
- Network Mode: NAT Network
- Processor: 2 CPU Cores

### Purpose
Used for:
- Windows environment testing
- Network communication testing
- VM connectivity practice
- Security lab simulations


---

# Network Configuration

All virtual machines were connected using NAT Network to allow communication between:
- Kali Linux
- Metasploitable2
- Windows 10

Connectivity was verified using ping commands.

---

# Outcome

Successfully downloaded, configured, and launched all required virtual machines for the cybersecurity virtual lab environment.

---

# Skills Learned

- Virtual machine setup
- Operating system installation
- Virtual networking
- Cybersecurity lab preparation
- Linux and Windows environment management
