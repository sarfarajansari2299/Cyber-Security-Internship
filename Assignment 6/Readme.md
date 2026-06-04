# ASSIGNMENT 6: NETWORK MAPPING & IP ADDRESS MASTERY

## Objective

The objective of this assignment is to gain practical experience in network discovery, IP addressing, subnetting, protocol identification, port scanning, and network traffic analysis using cybersecurity tools such as Nmap and Wireshark.

---

# 1. Network Discovery in Lab Environment

## Objective

Learn how to discover devices connected to a network, identify active hosts, determine open ports, and document the network topology.

---

## a. Use Nmap to Scan Your Virtual Network

### Command

```bash
nmap -sn 192.168.56.0/24
```

## Screenshot

<img width="947" height="1017" alt="image" src="https://github.com/user-attachments/assets/7c1bfd5d-3538-45b3-b042-960ae02331c0" />

---

## Active Hosts Identified

| IP Address      | Host Status |
| -------------   | ----------- |
| 192.168.56.101  | Active      |
| 192.168.56.102  | Active      |
| 192.168.56.103  | Active      |
| 192.168.56.100  | Active      |

---

## Observation

Nmap successfully identified all active devices connected to the virtual network subnet.

---

## b. Identify Active Hosts and Their IP Addresses

```Bash
nmap -sn 192.168.56.0/24

```
---
Screenshot
<img width="957" height="1017" alt="image" src="YOUR_SCREENSHOT_HERE" />
Active Host Discovery Results
Host Name	IP Address	Status
Virtual Router	192.168.56.1	Active
Kali Linux	192.168.56.10	Active
Ubuntu VM	192.168.56.20	Active
Windows VM	192.168.56.30	Active

---

## Observation

Host discovery tools provide visibility into all reachable systems within the subnet.

---

## c. Determine Open Ports on Each Host

### Scan Ubuntu VM

```bash
nmap 192.168.56.20
```

### Scan Windows VM

```bash
nmap 192.168.56.30
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/open-port-scan" />

---

## Ubuntu VM Results

| Port | Service |
| ---- | ------- |
| 22   | SSH     |
| 80   | HTTP    |

---

## Windows VM Results

| Port | Service |
| ---- | ------- |
| 135  | RPC     |
| 445  | SMB     |
| 3389 | RDP     |

---

## Observation

Open ports reveal services exposed by a host and help identify potential attack surfaces.

---

## d. Create Network Diagram

### Network Topology

```text
                         Internet
                             |
                       Virtual Router
                      192.168.56.1
                             |
 --------------------------------------------------
 |                     |                         |
 |                     |                         |
Kali Linux         Ubuntu VM               Windows VM
192.168.56.10      192.168.56.20          192.168.56.30
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/network-topology-diagram" />

---

## Observation

The network topology provides a visual representation of all devices discovered during scanning.

---

# 2. IP Addressing Practice

## Objective

Learn IPv4 addressing, subnetting, IPv6 configuration, and connectivity testing.

---

## a. Configure Static IPv4 Addresses on All VMs

### Kali Linux Configuration

```bash
ip addr show
```

### Ubuntu Configuration

```bash
ip addr show
```

### Windows Configuration

```cmd
ipconfig
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/static-ip-config" />

---

## Static IP Configuration Table

| Device     | IP Address    | Subnet Mask   | Gateway      |
| ---------- | ------------- | ------------- | ------------ |
| Kali Linux | 192.168.56.10 | 255.255.255.0 | 192.168.56.1 |
| Ubuntu VM  | 192.168.56.20 | 255.255.255.0 | 192.168.56.1 |
| Windows VM | 192.168.56.30 | 255.255.255.0 | 192.168.56.1 |

---

## Observation

Static IP addresses ensure consistent communication between virtual machines.

---

## b. Practice Subnetting Calculations

### Example Network

```text
192.168.56.0/24
```

### Subnet Calculation Results

| CIDR | Subnet Mask     | Hosts Available |
| ---- | --------------- | --------------- |
| /24  | 255.255.255.0   | 254             |
| /25  | 255.255.255.128 | 126             |
| /26  | 255.255.255.192 | 62              |
| /27  | 255.255.255.224 | 30              |
| /28  | 255.255.255.240 | 14              |

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/subnet-calculator" />

---

## Observation

Subnetting divides large networks into smaller manageable segments and improves network organization.

---

## c. Configure IPv6 Address

### Command

```bash
sudo ip -6 addr add 2001:db8::20/64 dev eth0
```

### Verify IPv6 Address

```bash
ip -6 addr
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/ipv6-configuration" />

---

## IPv6 Address

```text
2001:db8::20/64
```

---

## Observation

IPv6 provides a significantly larger address space compared to IPv4.

---

## d. Test Connectivity Between Systems

### Ping Ubuntu

```bash
ping 192.168.56.20
```

### Ping Windows

```bash
ping 192.168.56.30
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/connectivity-test" />

---

## Connectivity Results

| Source | Destination | Status  |
| ------ | ----------- | ------- |
| Kali   | Ubuntu      | Success |
| Kali   | Windows     | Success |
| Ubuntu | Windows     | Success |

---

## Observation

Successful ping responses confirmed proper IP addressing and routing configuration.

---

# 3. Protocol Identification Challenge

## Objective

Use Wireshark to capture and analyze network protocols.

---

## a. Capture Network Traffic Using Wireshark

### Procedure

1. Open Wireshark.
2. Select active network adapter.
3. Start packet capture.
4. Generate network traffic using ping and web browsing.

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/wireshark-capture" />

---

## Observation

Wireshark captures all packets transmitted across the selected network interface.

---

## b. Identify 10 Different Protocols

| Protocol | Purpose                  |
| -------- | ------------------------ |
| TCP      | Reliable Transport       |
| UDP      | Connectionless Transport |
| ICMP     | Network Diagnostics      |
| ARP      | Address Resolution       |
| DNS      | Domain Name Resolution   |
| HTTP     | Web Traffic              |
| HTTPS    | Secure Web Traffic       |
| DHCP     | Dynamic IP Assignment    |
| SMB      | File Sharing             |
| SSH      | Secure Remote Access     |

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/protocol-identification" />

---

## Observation

Multiple protocols operate simultaneously to support communication across the network.

---

## c. Analyze Packet Headers and Payloads

### TCP Packet Analysis

| Header Field     | Value   |
| ---------------- | ------- |
| Source Port      | 443     |
| Destination Port | 50432   |
| Sequence Number  | Present |
| Acknowledgement  | Present |

---

### ICMP Packet Analysis

| Header Field | Value |
| ------------ | ----- |
| Type         | 8     |
| Code         | 0     |
| Checksum     | Valid |

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/packet-analysis" />

---

## Observation

Packet headers contain routing information while payloads contain transmitted data.

---

## d. Filter Traffic by Protocol

### DNS Filter

```text
dns
```

### TCP Filter

```text
tcp
```

### HTTP Filter

```text
http
```

### ICMP Filter

```text
icmp
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/protocol-filtering" />

---

## Observation

Protocol filtering simplifies traffic analysis and troubleshooting.

---

# 4. Port Number Exploration

## Objective

Understand common ports, associated services, and service detection techniques.

---

## a. Scan Common Ports

### Command

```bash
nmap -p 21,22,23,25,53,80,443,3389,445 192.168.56.20
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/common-port-scan" />

---

## Port Scan Results

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

---

## Observation

Port scanning identifies accessible services and assists in security assessments.

---

## b. Identify Services Running on Each Port

| Port | Service Description           |
| ---- | ----------------------------- |
| 21   | File Transfer Protocol        |
| 22   | Secure Shell                  |
| 23   | Telnet                        |
| 25   | Simple Mail Transfer Protocol |
| 53   | Domain Name System            |
| 80   | Hypertext Transfer Protocol   |
| 443  | Secure HTTP                   |
| 3389 | Remote Desktop Protocol       |
| 445  | Server Message Block          |

---

## Observation

Each port is associated with a specific network service used by applications.

---

## c. Nmap Service Detection

### Command

```bash
nmap -sV 192.168.56.20
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/service-detection" />

---

## Sample Results

| Port | Service | Version     |
| ---- | ------- | ----------- |
| 22   | SSH     | OpenSSH 8.9 |
| 80   | HTTP    | Apache 2.4  |
| 443  | HTTPS   | Apache SSL  |

---

## Observation

Service detection helps identify software versions running on target systems.

---

## d. Research and Document 20 Common Ports

| Port | Protocol | Service     |
| ---- | -------- | ----------- |
| 20   | TCP      | FTP Data    |
| 21   | TCP      | FTP         |
| 22   | TCP      | SSH         |
| 23   | TCP      | Telnet      |
| 25   | TCP      | SMTP        |
| 53   | TCP/UDP  | DNS         |
| 67   | UDP      | DHCP Server |
| 68   | UDP      | DHCP Client |
| 69   | UDP      | TFTP        |
| 80   | TCP      | HTTP        |
| 110  | TCP      | POP3        |
| 123  | UDP      | NTP         |
| 135  | TCP      | RPC         |
| 139  | TCP      | NetBIOS     |
| 143  | TCP      | IMAP        |
| 161  | UDP      | SNMP        |
| 389  | TCP      | LDAP        |
| 443  | TCP      | HTTPS       |
| 445  | TCP      | SMB         |
| 3389 | TCP      | RDP         |

---

# Challenges Faced

| Problem                             | Solution                              |
| ----------------------------------- | ------------------------------------- |
| Hosts not appearing in Nmap scan    | Verified network adapter settings     |
| Firewall blocking ping requests     | Temporarily allowed ICMP traffic      |
| Wireshark showing excessive traffic | Applied protocol filters              |
| IPv6 configuration errors           | Verified interface configuration      |
| Port scan results inconsistent      | Re-ran scans with elevated privileges |

---

# Conclusion

In this assignment, network discovery, IP addressing, subnetting, protocol analysis, and port scanning techniques were successfully performed. Nmap was used to identify active hosts and open ports, while Wireshark was used to capture and analyze network traffic. Static IPv4 and IPv6 configurations were implemented, subnet calculations were practiced, and common network services were documented. This assignment strengthened practical networking and cybersecurity skills required for security assessments and network administration.

---

# Tools and Platforms Used

* Kali Linux
* Ubuntu Linux
* Windows 10 VM
* VirtualBox
* Nmap
* Wireshark
* Command Prompt
* Terminal
* Online Subnet Calculator

---

# Author

sarfaraj Ahamad

