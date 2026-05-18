# Network Topology Diagram Documentation

## Objective
The objective of this task was to design and document the network topology of the cybersecurity virtual lab environment created using Oracle VM VirtualBox.

---

# Network Architecture Overview

The cybersecurity lab environment was created on a Windows host machine using Oracle VM VirtualBox. All virtual machines were connected through a VirtualBox NAT Network / Host-Only Network to allow secure communication and isolated testing.

The lab environment included:

- Kali Linux (Attacker Machine)
- Metasploitable2 (Victim Machine)
- Windows 10 Virtual Machine

---

# Network Topology Diagram

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
| 10.0.2.1       |   | 10.0.2.15      |   |      10.0.2.1       |
|                |   |                |   |                     |
| User Simulation|   | Security Testing|  | Vulnerable Services |
| Browsing       |   | Reconnaissance |   | FTP / SSH / HTTP    |
| File Sharing   |   | Exploitation   |   |                     |
+----------------+   +----------------+   +----------------------+
```

---

# Virtual Machines and Roles

## 1. Kali Linux

### Role
Kali Linux was used as the attacker machine for performing:
- Security testing
- Reconnaissance
- Vulnerability scanning
- Exploitation practice

### IP Address
```text
192.168.56.102
```

---

## 2. Metasploitable2

### Role
Metasploitable2 was configured as the intentionally vulnerable victim machine for cybersecurity testing.

### Vulnerable Services
- FTP
- SSH
- HTTP

### IP Address
```text
192.168.56.101
```

---

## 3. Windows 10 VM

### Role
Windows 10 VM was used for:
- User simulation
- File sharing
- Browser testing
- Cross-platform communication testing

### IP Address
```text
192.168.56.103
```

---

# Network Configuration

## Network Type
- NAT Network / Host-Only Network

## Features
- Secure isolated environment
- VM-to-VM communication
- Internet access (NAT)
- Safe penetration testing environment

---

# Connectivity Testing

Connectivity between all virtual machines was verified using ping commands.

---

# Security Benefits of the Lab Setup

- Isolated testing environment
- Prevents exposure to the host network
- Safe vulnerability assessment practice
- Controlled penetration testing environment

---

# Outcome

Successfully designed and implemented a secure cybersecurity virtual lab environment with proper network communication between all virtual machines.

---

# Skills Learned

- Virtual network configuration
- NAT Network setup
- Host-Only networking
- Cybersecurity lab design
- VM communication testing
- Basic penetration testing environment setup

---

# Screenshot

<img width="1920" height="1876" alt="IMG_20260516_105044" src="https://github.com/user-attachments/assets/be2759f9-23e8-407d-aff2-4274a6a2ffef" />


