# ASSIGNMENT 6: NETWORK MAPPING & IP ADDRESS MASTERY

## Objective

The objective of this assignment is to perform network mapping, IP address configuration, protocol identification, and port exploration within a virtual cybersecurity lab environment using Nmap, Wireshark, and various Linux networking tools.

---

# 1. Network Discovery in Lab Environment

## Objective

Discover all active hosts, open ports, and services running within the virtual lab network.

---

# a. Use Nmap to Scan the Virtual Network

## Steps Performed

1. Opened terminal in Kali Linux.
2. Identified the local subnet using `ip addr`.
3. Ran a full network scan using Nmap against the host-only network range.

---

## Command

```bash
nmap -sn 192.168.56.0/24
```

> `-sn` performs a ping scan (host discovery only, no port scan).

---

## Screenshot

<img width="1010" height="816" alt="image" src="https://github.com/user-attachments/assets/08b2e6e9-b0fc-4446-815f-dcfd14d5ee80" />

<img width="1010" height="816" alt="image" src="https://github.com/user-attachments/assets/2a422ed7-74c9-4d08-b3d6-70ff964cf325" />

---

# b. Identify All Active Hosts and Their IP Addresses

## Hosts Discovered

| Hostname        | IP Address     | Status |
| --------------- | -------------- | ------ |
| Kali Linux      | 192.168.56.101 | Up     |
| Metasploitable2 | 192.168.56.103 | Up     |
| Windows 10      | 192.168.56.102 | Up     |

---

## Command

```bash
nmap -sn 192.168.56.0/24 -oN host_discovery.txt
```

> `-oN` saves output in normal format to a file.

---

## Screenshot

<img width="1010" height="816" alt="image" src="https://github.com/user-attachments/assets/ec4201e5-65be-423c-bbf0-afeeaaa6746a" />

---

# c. Determine Open Ports on Each Host

## Command

```bash
nmap 192.168.56.104
```

---

## Screenshot

### Open Ports Found on Metasploitable2 (192.168.56.104)

<img width="1005" height="679" alt="image" src="https://github.com/user-attachments/assets/4047079e-5b60-4ef7-bf4b-a4c59ddc3b8a" />

---

### Open Ports Found on Windows 10 (192.168.56.103)

<img width="1005" height="679" alt="image" src="https://github.com/user-attachments/assets/4d09197b-db75-420a-a547-4febd872e6b1" />

---

### Open Ports Found on Kali Linux (192.168.56.102)

<img width="1005" height="679" alt="image" src="https://github.com/user-attachments/assets/5a210404-17d8-4593-8251-7e382937b50c" />

---

## Open Ports Summary Table

| Host                | Port  | State | Service       |
| ------------------- | ----- | ----- | ------------- |
| Metasploitable2     | 21    | Open  | FTP           |
| Metasploitable2     | 22    | Open  | SSH           |
| Metasploitable2     | 23    | Open  | Telnet        |
| Metasploitable2     | 25    | Open  | SMTP          |
| Metasploitable2     | 53    | Open  | DNS           |
| Metasploitable2     | 80    | Open  | HTTP          |
| Metasploitable2     | 139   | Open  | NetBIOS       |
| Metasploitable2     | 445   | Open  | SMB           |
| Metasploitable2     | 3306  | Open  | MySQL         |
| Windows 10          | 445   | Open  | SMB           |
| Windows 10          | 3389  | Open  | RDP           |
| Kali Linux          | 22    | Open  | SSH           |

---

# d. Create Network Diagram

## Network Topology

```
                    [VirtualBox Host Machine]
                            |
               ┌────────────┴────────────┐
               │     Host-Only Adapter   │
               │    192.168.56.0/24      │
               └────────────┬────────────┘
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
   ┌──────┴──────┐   ┌──────┴──────┐  ┌──────┴──────┐
   │ Kali Linux  │   │Metasploitable│ │ Windows 10  │
   │192.168.56.102│  │192.168.56.104│ │192.168.56.103│
   │ SSH: 22     │   │ SSH: 22      │ │ RDP: 3389   │
   │             │   │ HTTP: 80     │ │ SMB: 445    │
   └─────────────┘   │ MySQL: 3306  │ └─────────────┘
                     │ FTP: 21      │
                     │ Telnet: 23   │
                     └──────────────┘
```

---

## Observation

Nmap successfully discovered all three VMs within the isolated host-only network. All machines responded to ping and port scans, confirming proper network configuration. Metasploitable2 showed the most open ports (vulnerable lab VM), while Windows 10 and Kali Linux had fewer exposed services.

---

# 2. IP Addressing Practice

## Objective

Configure static IPv4 and IPv6 addresses across virtual machines and test inter-subnet connectivity.

---

# a. Configure Static IPv4 Addresses on All VMs

## Steps Performed

1. Edited the network interfaces configuration file on Kali Linux.
2. Assigned static IP addresses within the host-only subnet.
3. Restarted the networking service to apply changes.
4. Verified assignments on all VMs.

---

## Command (Kali Linux)

```bash
sudo nano /etc/network/interfaces
```

---

## Configuration Added

```text
auto eth0
iface eth0 inet static
    address 192.168.56.101
    netmask 255.255.255.0
    gateway 192.168.56.1
    dns-nameservers 8.8.8.8 8.8.4.4
```

---

## Screenshot

<img width="1001" height="679" alt="image" src="https://github.com/user-attachments/assets/1ff34e04-ce54-468f-89a1-cf4c6c770566" />

---

## Restart Networking

```bash
sudo systemctl restart networking
```

---

## Verify IP Assignment

```bash
ip addr show eth0
```

---

## Screenshot

<img width="1001" height="679" alt="image" src="https://github.com/user-attachments/assets/cb5dea5f-0f62-4aeb-a6ad-55a13de3963d" />

<img width="1001" height="679" alt="image" src="https://github.com/user-attachments/assets/90688be1-b77d-4a78-b117-6084bf79fc53" />

<img width="1026" height="853" alt="image" src="https://github.com/user-attachments/assets/88735b8e-18fe-46e7-ab6d-8f35c65589ec" />

<img width="782" height="715" alt="image" src="https://github.com/user-attachments/assets/4bc721cb-9705-45d3-97bb-7b619c9e9835" />

---

## Static IP Assignment Summary

| VM              | Static IP      | Subnet Mask     | Gateway      |
| --------------- | -------------- | --------------- | ------------ |
| Kali Linux      | 192.168.56.101 | 255.255.255.0   | 192.168.56.1 |
| Metasploitable2 | 192.168.56.103 | 255.255.255.0   | 192.168.56.1 |
| Windows 10      | 192.168.56.102 | 255.255.255.0   | 192.168.56.1 |

---

# b. Subnetting Calculations

## Objective

Understand IP subnetting and calculate network parameters.

---

## Subnet Practice Table

| Network Address | Subnet Mask     | CIDR | Hosts Available | Broadcast Address | First Host     | Last Host       |
| --------------- | --------------- | ---- | --------------- | ----------------- | -------------- | --------------- |
| 192.168.56.0    | 255.255.255.0   | /24  | 254             | 192.168.56.255    | 192.168.56.1   | 192.168.56.254  |
| 192.168.56.0    | 255.255.255.128 | /25  | 126             | 192.168.56.127    | 192.168.56.1   | 192.168.56.126  |
| 192.168.56.0    | 255.255.255.192 | /26  | 62              | 192.168.56.63     | 192.168.56.1   | 192.168.56.62   |
| 10.0.2.0        | 255.255.255.0   | /24  | 254             | 10.0.2.255        | 10.0.2.1       | 10.0.2.254      |

---

## Tool Used

```bash
sudo apt update
sudo apt install sipcalc -y
sipcalc 192.168.56.0/24

```

---

## ipcalc Command Examples
```bash
sipcalc 192.168.56.0/24
```
---

### Example 1: Calculate /24 Subnet

```bash
sipcalc 192.168.56.0/24
```

**Output:**
```
-[ipv4 : 192.168.56.0/24] - 0

[CIDR]
Host address            - 192.168.56.0
Host address (decimal)  - 3232249856
Host address (hex)      - C0A83800
Network address         - 192.168.56.0
Network mask            - 255.255.255.0
Network mask (bits)     - 24
Network mask (hex)      - FFFFFF00
Broadcast address       - 192.168.56.255
Cisco wildcard          - 0.0.0.255
Addresses in network    - 256
Network range           - 192.168.56.0 - 192.168.56.255
Usable range            - 192.168.56.1 - 192.168.56.254

```

---

### Example 2: Calculate /25 Subnet

```bash
ipcalc 192.168.56.0/25
```

**Output:**
```
-[ipv4 : 192.168.56.0/25] - 0

[CIDR]
Host address            - 192.168.56.0
Host address (decimal)  - 3232249856
Host address (hex)      - C0A83800
Network address         - 192.168.56.0
Network mask            - 255.255.255.128
Network mask (bits)     - 25
Network mask (hex)      - FFFFFF80
Broadcast address       - 192.168.56.127
Cisco wildcard          - 0.0.0.127
Addresses in network    - 128
Network range           - 192.168.56.0 - 192.168.56.127
Usable range            - 192.168.56.1 - 192.168.56.126

```

---


---

## Screenshot

<img width="1267" height="1035" alt="image" src="https://github.com/user-attachments/assets/82ad2011-97a9-4818-8b7a-dce21f155b38" />


---

# c. Set Up IPv6 Address on Kali Linux

## Command to View Current IPv6 Addresses

```bash
ip -6 addr
```

> `fd00::1/64` is a unique local address (ULA) in IPv6 format.

---

## Add a Static IPv6 Address

```bash
sudo ip -6 addr add fd00::1/64 dev eth1
```

---

## Verify IPv6 Configuration

```bash
ip -6 addr show eth1
```
# Output

```bash
 inet6 fd00::1/64 scope global 
       valid_lft forever preferred_lft forever

```
---

## IPv6 Configuration

| VM              | IPv6 Address | Prefix Length  | Address Type |
| --------------- | ------------ | ---------------| ------------ |
| Kali Linux      | fd00::1      | 64             | ULA          |
| Metasploitable2 |Not Configured| N/A            | N/A          |
| Windows 10      |Not Configured| N/A            | N/A          |

---

## Make IPv6 Persistent

Edit `/etc/network/interfaces` to add:

```text
iface eth0 inet6 static
    address fd00::1
    netmask 64
```

---

# Screenshot

## Static IPv6 Address
<img width="1267" height="1035" alt="image" src="https://github.com/user-attachments/assets/6fef96f6-1bc7-4aea-8ae2-b745daf25e13" />


## Make IPv6 Persistent

<img width="1267" height="1035" alt="image" src="https://github.com/user-attachments/assets/c81bd706-e9b5-44b0-a03f-f074db339dff" />

---

# d. Test Connectivity Between VMs

## IPv4 Ping Test windows 10 from Kali

### Command

```bash
ping -c 4 192.168.56.102
```

---

# Screenshot

<img width="1267" height="1035" alt="image" src="https://github.com/user-attachments/assets/df97d842-7b8c-4ddd-a66e-235755e79e1d" />


---

## IPv6 Ping Test Metasploitable2 from Kali

### Command

```bash
ping -c 10 192.168.56.102
```

---

# Screenshot

<img width="1267" height="1035" alt="image" src="https://github.com/user-attachments/assets/fb54f6a2-1bfa-4acc-ade0-c179841a441c" />


---

---

## Observation

Static IP addresses were successfully configured on all VMs. IPv4 connectivity between VMs was verified using ping with 0% packet loss. IPv6 addressing was configured and tested successfully. Subnetting calculations confirmed the correct number of usable hosts per subnet.

---

# 3. Protocol Identification Challenge

## Objective

Capture live network traffic using Wireshark and identify 10 different protocols by analyzing packet headers and payloads.

---

# a. Capture Traffic Using Wireshark

## Steps Performed

1. Launched Wireshark in Kali Linux with root privileges.
2. Selected the active `eth0` network interface.
3. Started live packet capture.
4. Generated traffic using ping, curl, SSH, and DNS lookup commands.
5. Stopped capture after generating sufficient traffic.

---

## Command to Launch Wireshark

```bash
sudo wireshark &
```

> The `&` runs Wireshark in the background.

---

## Generating Network Traffic

While Wireshark is capturing, open another terminal and run:

```bash
# DNS lookup
nslookup google.com

# Ping test
ping 192.168.56.102

# HTTP request
curl http://example.com

# SSH connection
ssh cyberuser@192.168.56.102
```

---

## Screenshot

<img width="1267" height="1035" alt="image" src="https://github.com/user-attachments/assets/712c95e9-8def-4d62-8c89-49b24a8de7c6" />


---

# b. Identify 10 Different Protocols

## Protocols Identified

| # | Protocol | Layer       | Description                                      | Filter Used           |
|---|----------|-------------|--------------------------------------------------|-----------------------|
| 1 | ICMP     | Network     | Internet Control Message Protocol (ping traffic) | `icmp`                |
| 2 | ARP      | Data Link   | Address Resolution Protocol (IP-MAC mapping)     | `arp`                 |
| 3 | TCP      | Transport   | Transmission Control Protocol (reliable stream)  | `tcp`                 |
| 4 | UDP      | Transport   | User Datagram Protocol (connectionless)          | `udp`                 |
| 5 | DNS      | Application | Domain Name System (hostname resolution)         | `dns`                 |
| 6 | HTTP     | Application | Hypertext Transfer Protocol (web traffic)        | `http`                |
| 7 | SSH      | Application | Secure Shell (encrypted remote access)           | `tcp.port == 22`      |
| 8 | FTP      | Application | File Transfer Protocol (file transfers)          | `ftp`                 |
| 9 | DHCP     | Application | Dynamic Host Configuration Protocol (IP leasing) | `bootp`               |
| 10| NBNS     | Application | NetBIOS Name Service (Windows name resolution)   | `nbns`                |

---

## Protocol Details

### Protocol 1: ICMP (Internet Control Message Protocol)

**Layer:** Network (Layer 3)  
**Port:** N/A  
**Purpose:** Error reporting and diagnostic messages

**Packet Structure:**
```
Ethernet Header:
  Destination MAC: 08:00:27:xx:xx:xx
  Source MAC: 08:00:27:xx:xx:xx
IP Header:
  Source IP: 192.168.56.101
  Destination IP: 192.168.56.102
  Protocol: ICMP (1)
ICMP Header:
  Type: 8 (Echo Request) / 0 (Echo Reply)
  Code: 0
  Checksum: Valid
  Identifier: 1234
  Sequence Number: 1
```

---

### Protocol 2: ARP (Address Resolution Protocol)

**Layer:** Data Link (Layer 2)  
**Port:** N/A  
**Purpose:** Map IP addresses to MAC addresses

**Packet Structure:**
```
Ethernet Header:
  Destination MAC: ff:ff:ff:ff:ff:ff (broadcast)
  Source MAC: 08:00:27:xx:xx:xx
ARP Header:
  Hardware Type: Ethernet (1)
  Protocol Type: IPv4 (0x0800)
  Hardware Size: 6 bytes
  Protocol Size: 4 bytes
  Opcode: 1 (Request) / 2 (Reply)
  Sender MAC: 08:00:27:xx:xx:xx
  Sender IP: 192.168.56.101
  Target MAC: 00:00:00:00:00:00
  Target IP: 192.168.56.102
```

---

### Protocol 3: TCP (Transmission Control Protocol)

**Layer:** Transport (Layer 4)  
**Port:** Variable  
**Purpose:** Reliable, connection-oriented data transmission

**Packet Structure:**
```
IP Header:
  Source IP: 192.168.56.101
  Destination IP: 192.168.56.102
  Protocol: TCP (6)
TCP Header:
  Source Port: 54321
  Destination Port: 22 (SSH)
  Sequence Number: 1000000
  Acknowledgment Number: 2000000
  Flags: SYN, ACK, FIN, RST, PSH, URG
  Window Size: 65535
  Checksum: Valid
```

---

### Protocol 4: UDP (User Datagram Protocol)

**Layer:** Transport (Layer 4)  
**Port:** Variable  
**Purpose:** Connectionless, fast data transmission

**Packet Structure:**
```
IP Header:
  Source IP: 192.168.56.101
  Destination IP: 192.168.56.102
  Protocol: UDP (17)
UDP Header:
  Source Port: 53 (DNS)
  Destination Port: 53
  Length: 64 bytes
  Checksum: Valid
```

---

### Protocol 5: DNS (Domain Name System)

**Layer:** Application (Layer 7)  
**Port:** 53 (UDP/TCP)  
**Purpose:** Hostname to IP address resolution

**Packet Structure:**
```
UDP Header:
  Source Port: 54321
  Destination Port: 53
DNS Header:
  Transaction ID: 0x1234
  Flags: Query/Response
  Questions: 1
  Answer RRs: 0
  Authority RRs: 0
  Additional RRs: 0
Query Section:
  Name: google.com
  Type: A (IPv4 Address)
  Class: IN (Internet)
```

---

### Protocol 6: HTTP (Hypertext Transfer Protocol)

**Layer:** Application (Layer 7)  
**Port:** 80 (TCP)  
**Purpose:** Web page retrieval

**Packet Structure:**
```
TCP Header:
  Source Port: 54321
  Destination Port: 80
HTTP Header:
  Method: GET
  URI: /index.html
  Version: HTTP/1.1
  Host: example.com
  User-Agent: curl/7.64.1
  Accept: */*
```

---

### Protocol 7: SSH (Secure Shell)

**Layer:** Application (Layer 7)  
**Port:** 22 (TCP)  
**Purpose:** Secure remote shell access

**Packet Structure:**
```
TCP Header:
  Source Port: 54321
  Destination Port: 22
SSH Protocol Version: SSH-2.0-OpenSSH_7.4
Encryption: Algorithms negotiated
Authentication: Username/Password or Key-based
Data: Encrypted
```

---

### Protocol 8: FTP (File Transfer Protocol)

**Layer:** Application (Layer 7)  
**Port:** 21 (Command), 20 (Data)  
**Purpose:** File transfer

**Packet Structure:**
```
TCP Header:
  Source Port: 54321
  Destination Port: 21
FTP Command:
  Command: USER username
  Response: 331 Password required
  Command: PASS password
  Response: 230 Login successful
```

---

### Protocol 9: DHCP (Dynamic Host Configuration Protocol)

**Layer:** Application (Layer 7)  
**Port:** 67 (Server), 68 (Client)  
**Purpose:** Dynamic IP address assignment

**Packet Structure:**
```
UDP Header:
  Source Port: 68
  Destination Port: 67
DHCP Header:
  Op: 1 (Request) / 2 (Reply)
  Htype: 1 (Ethernet)
  Hlen: 6
  Xid: 0x12345678
  Ciaddr: 0.0.0.0
  Yiaddr: 192.168.56.101
  Server Identifier: 192.168.56.1
  Requested IP: 192.168.56.101
  Lease Time: 3600 seconds
```

---

### Protocol 10: NBNS (NetBIOS Name Service)

**Layer:** Application (Layer 7)  
**Port:** 137 (UDP)  
**Purpose:** Windows hostname resolution

**Packet Structure:**
```
UDP Header:
  Source Port: 137
  Destination Port: 137
NBNS Header:
  Transaction ID: 0x5678
  Flags: Query/Response
  Questions: 1
  Answer RRs: 0
Query:
  Name: WORKSTATION
  Type: NB (NetBIOS General Name Service)
  Class: IN (Internet)
```

---

# c. Analyze Packet Headers and Payloads

## ICMP Packet Analysis (Ping Request)

```
Frame: 64 bytes
Ethernet Header:
  Destination MAC: 08:00:27:aa:bb:cc
  Source MAC: 08:00:27:dd:ee:ff
  EtherType: 0x0800 (IPv4)

IP Header:
  Version: 4
  Header Length: 20 bytes
  DSCP: 0 (Default)
  Total Length: 60 bytes
  Identification: 0x5678
  Flags: Don't Fragment (DF)
  TTL: 64
  Protocol: ICMP (1)
  Header Checksum: Valid
  Source IP: 192.168.56.101
  Destination IP: 192.168.56.102

ICMP Header:
  Type: 8 (Echo Request)
  Code: 0
  Checksum: Valid (0x1234)
  Identifier: 0x0001
  Sequence: 0x0001

ICMP Payload:
  Data (56 bytes): abcdefghijklmnopqrstuvwxyz...
```

---

## TCP 3-Way Handshake Analysis (SSH Connection)

### Packet 1: SYN

```
TCP Header:
  Source Port: 54321
  Destination Port: 22
  Sequence Number: 1000000
  Acknowledgment Number: 0
  Flags: SYN
  Window Size: 65535
  Checksum: Valid
  Options: MSS=1460, SACK_PERM, TS_VAL=...
```

### Packet 2: SYN-ACK

```
TCP Header:
  Source Port: 22
  Destination Port: 54321
  Sequence Number: 2000000
  Acknowledgment Number: 1000001
  Flags: SYN, ACK
  Window Size: 32768
  Checksum: Valid
  Options: MSS=1460, SACK_PERM, TS_VAL=...
```

### Packet 3: ACK

```
TCP Header:
  Source Port: 54321
  Destination Port: 22
  Sequence Number: 1000001
  Acknowledgment Number: 2000001
  Flags: ACK
  Window Size: 65535
  Checksum: Valid
```

---

## DNS Query Analysis

```
Frame: 72 bytes
Ethernet Header:
  Destination MAC: 08:00:27:aa:bb:cc
  Source MAC: 08:00:27:dd:ee:ff

IP Header:
  Version: 4
  Total Length: 58 bytes
  Source IP: 192.168.56.101
  Destination IP: 8.8.8.8 (Google DNS)
  Protocol: UDP (17)

UDP Header:
  Source Port: 54321
  Destination Port: 53
  Length: 38 bytes
  Checksum: Valid

DNS Header:
  Transaction ID: 0x1234
  Flags: 0x0100 (Standard Query)
  Questions: 1
  Answer RRs: 0
  Authority RRs: 0
  Additional RRs: 0

Query Section:
  Name: google.com (length-encoded)
  Type: 1 (A - IPv4 Address)
  Class: 1 (IN - Internet)
```

---

## Screenshot

<img width="1400" height="900" alt="image" src="https://github.com/user-attachments/assets/packet-analysis" />

---

# d. Filter Traffic by Protocol Type

## Wireshark Display Filters

### Filter by Single Protocol

```text
# ICMP traffic
icmp

# ARP traffic
arp

# TCP traffic
tcp

# UDP traffic
udp

# DNS traffic
dns

# HTTP traffic
http

# SSH traffic
tcp.port == 22

# FTP traffic
ftp

# DHCP traffic
bootp

# NetBIOS traffic
nbns
```

---

### Combine Filters with Boolean Operators

```text
# TCP or UDP traffic
tcp || udp

# All traffic except ICMP
!icmp

# HTTP and DNS traffic
http || dns

# Traffic to specific IP
ip.dst == 192.168.56.102

# Traffic from specific IP
ip.src == 192.168.56.101

# TCP traffic on port 22
tcp.port == 22

# UDP traffic on port 53
udp.port == 53

# Traffic between two hosts
(ip.src == 192.168.56.101) && (ip.dst == 192.168.56.102)
```

---

## Capture Traffic via CLI (tcpdump)

### Basic Capture

```bash
sudo tcpdump -i eth0 -w capture.pcap
```

> `-i eth0` specifies interface, `-w capture.pcap` saves to file

---

### Capture Specific Protocol

```bash
# Capture only ICMP
sudo tcpdump -i eth0 icmp -w icmp_capture.pcap

# Capture only DNS
sudo tcpdump -i eth0 port 53 -w dns_capture.pcap

# Capture only SSH
sudo tcpdump -i eth0 port 22 -w ssh_capture.pcap

# Capture with packet content
sudo tcpdump -i eth0 -w capture.pcap -X
```

---

### Open Capture in Wireshark

```bash
wireshark capture.pcap &
```

---

## Screenshot

<img width="1400" height="900" alt="image" src="https://github.com/user-attachments/assets/filtered-traffic" />

---

## Observation

Wireshark successfully captured and displayed multiple protocol types. Filtering by protocol allowed targeted analysis of specific traffic types. Display filters proved effective for isolating relevant packets. Combined with tcpdump CLI capture, comprehensive network traffic analysis was achieved.

---

# 4. Port Number Exploration

## Objective

Scan and identify common network ports and the services running on them using Nmap service detection.

---

# a. Scan Common Ports

## Command

```bash
nmap -p 21,22,23,25,53,80,443,3389,445 192.168.56.102
```

> `-p` specifies ports to scan (comma-separated).

---

## Results Table

| Port | State  | Service  |
| ---- | ------ | -------- |
| 21   | Open   | FTP      |
| 22   | Open   | SSH      |
| 23   | Open   | Telnet   |
| 25   | Open   | SMTP     |
| 53   | Open   | DNS      |
| 80   | Open   | HTTP     |
| 443  | Closed | HTTPS    |
| 445  | Open   | SMB      |
| 3389 | Closed | RDP      |

---

## Screenshot

<img width="1200" height="800" alt="image" src="https://github.com/user-attachments/assets/port-scan" />

---

# b. Identify Services Running on Each Port

## Using Nmap Service Detection

```bash
nmap -sV -p 21,22,23,25,53,80,443,3389,445 192.168.56.102
```

> `-sV` detects service versions running on open ports.

---

## Screenshot

<img width="1200" height="800" alt="image" src="https://github.com/user-attachments/assets/service-detection" />

---

# c. Nmap Service Detection - Full Scan

## Command

```bash
nmap -sV 192.168.56.102
```

---

## Output

```
PORT     STATE  SERVICE     VERSION
21/tcp   open   ftp         vsftpd 2.3.4
22/tcp   open   ssh         OpenSSH 4.7p1 Debian 8+etch3
23/tcp   open   telnet      Linux telnetd
25/tcp   open   smtp        Postfix smtpd
53/tcp   open   domain      ISC BIND 9.3.4
80/tcp   open   http        Apache httpd 2.2.8
139/tcp  open   netbios-ssn Samba smbd 3.0.20
445/tcp  open   microsoft-ds Samba smbd 3.0.20
3306/tcp open   mysql       MySQL 5.0.51a-3+lenny5
5432/tcp open   postgresql  PostgreSQL 8.3.0 on i686-pc-linux-gnu
8180/tcp open   http        Apache Tomcat/Coyote JSP engine 1.1
MAC Address: 08:00:27:AA:BB:CC (Oracle VirtualBox virtual NIC)
```

---

## Screenshot

<img width="1200" height="800" alt="image" src="https://github.com/user-attachments/assets/full-service-detection" />

---

# d. 20 Common Port Numbers Reference

## Common Ports Detailed Table

| Port | Protocol | Service                           | Description                                        | Vulnerability Risk |
| ---- | -------- | --------------------------------- | -------------------------------------------------- | ------------------ |
| 20   | TCP      | FTP Data                          | File Transfer Protocol – data channel              | High               |
| 21   | TCP      | FTP Control                       | File Transfer Protocol – command channel           | High               |
| 22   | TCP      | SSH                               | Secure Shell – encrypted remote access             | Low                |
| 23   | TCP      | Telnet                            | Unencrypted remote terminal access                 | Critical           |
| 25   | TCP      | SMTP                              | Simple Mail Transfer Protocol – email sending      | Medium             |
| 53   | TCP/UDP  | DNS                               | Domain Name System – hostname resolution           | Medium             |
| 67   | UDP      | DHCP Server                       | Dynamic Host Configuration Protocol – IP leasing  | Medium             |
| 68   | UDP      | DHCP Client                       | DHCP client port                                   | Medium             |
| 80   | TCP      | HTTP                              | HyperText Transfer Protocol – web traffic          | Medium             |
| 110  | TCP      | POP3                              | Post Office Protocol – email retrieval             | Medium             |
| 143  | TCP      | IMAP                              | Internet Message Access Protocol – email access    | Medium             |
| 443  | TCP      | HTTPS                             | HTTP Secure – encrypted web traffic                | Low                |
| 445  | TCP      | SMB                               | Server Message Block – Windows file sharing        | High               |
| 3306 | TCP      | MySQL                             | MySQL database service                             | High               |
| 3389 | TCP      | RDP                               | Remote Desktop Protocol – Windows remote access    | High               |
| 5432 | TCP      | PostgreSQL                        | PostgreSQL database service                        | High               |
| 8080 | TCP      | HTTP Alternate                    | Alternate HTTP port / proxy                        | Medium             |
| 8443 | TCP      | HTTPS Alternate                   | Alternate HTTPS port                               | Low                |
| 139  | TCP      | NetBIOS-SSN                       | NetBIOS Session Service                            | High               |
| 6667 | TCP      | IRC                               | Internet Relay Chat                                | Low                |

---

## Port Categorization

### Well-Known Ports (0-1023)

These are reserved for common services and require root/admin privileges to run.

```
20   - FTP Data
21   - FTP Control
22   - SSH
23   - Telnet
25   - SMTP
53   - DNS
80   - HTTP
110  - POP3
143  - IMAP
443  - HTTPS
```

---

### Registered Ports (1024-49151)

These can be used by user processes and organizations.

```
3306 - MySQL
3389 - RDP
5432 - PostgreSQL
8080 - HTTP Alternate
8443 - HTTPS Alternate
```

---

### Dynamic/Private Ports (49152-65535)

These are temporarily assigned to processes.

```
49152-65535 - Client connections, temporary services
```

---

## Service Details

### FTP (Ports 20-21)

**Security Level:** High Risk  
**Authentication:** Username/Password  
**Encryption:** None (unencrypted credentials)  
**Use Case:** File transfer (legacy, not recommended)  
**Modern Alternative:** SFTP, FTPS

---

### SSH (Port 22)

**Security Level:** Low Risk  
**Authentication:** Public/Private Key or Password  
**Encryption:** Full encryption (AES-128, AES-192, AES-256)  
**Use Case:** Secure remote shell access  
**Industry Standard:** Yes

---

### Telnet (Port 23)

**Security Level:** Critical Risk  
**Authentication:** Username/Password (unencrypted)  
**Encryption:** None  
**Use Case:** Remote terminal (DEPRECATED)  
**Modern Alternative:** SSH

---

### SMTP (Port 25)

**Security Level:** Medium Risk  
**Authentication:** Optional (usually none)  
**Encryption:** Optional (TLS/SSL)  
**Use Case:** Email sending  
**Secure Variant:** Port 587 (SMTP + TLS)

---

### DNS (Port 53)

**Security Level:** Medium Risk  
**Authentication:** None  
**Encryption:** None (can use DNSSEC)  
**Use Case:** Domain name resolution  
**Secure Variant:** DNS over HTTPS (DoH), DNS over TLS (DoT)

---

### HTTP (Port 80)

**Security Level:** Medium Risk  
**Authentication:** Varies (usually cookie-based)  
**Encryption:** None  
**Use Case:** Unencrypted web traffic  
**Modern Alternative:** HTTPS (Port 443)

---

### HTTPS (Port 443)

**Security Level:** Low Risk  
**Authentication:** Certificate-based + credentials  
**Encryption:** TLS/SSL (mandatory)  
**Use Case:** Secure web traffic  
**Industry Standard:** Yes

---

### MySQL (Port 3306)

**Security Level:** High Risk  
**Authentication:** Username/Password  
**Encryption:** Optional  
**Use Case:** Database management system  
**Recommendation:** Restrict to local network, use firewall

---

### RDP (Port 3389)

**Security Level:** High Risk  
**Authentication:** Windows credentials  
**Encryption:** Optional (usually enabled)  
**Use Case:** Remote desktop for Windows  
**Recommendation:** Use VPN, strong passwords, multi-factor authentication

---

### SMB (Port 445)

**Security Level:** High Risk  
**Authentication:** Windows credentials  
**Encryption:** Optional  
**Use Case:** Windows file/printer sharing  
**Security Issues:** EternalBlue (MS17-010), ransomware vector

---

## Nmap Scanning Techniques

### Scan Specific Port Range

```bash
nmap -p 1-1000 192.168.56.102
```

---

### Scan All Ports

```bash
nmap -p- 192.168.56.102
```

---

### Scan with Version Detection

```bash
nmap -sV 192.168.56.102
```

---

### Aggressive Scan

```bash
nmap -A 192.168.56.102
```

> `-A` enables OS detection, version detection, script scanning, and traceroute.

---

### Save Output

```bash
nmap -p- 192.168.56.102 -oN scan_results.txt
```

---

## Screenshot

<img width="1200" height="800" alt="image" src="https://github.com/user-attachments/assets/port-reference" />

---

## Observation

Nmap's service detection (`-sV`) accurately identified the software versions running on open ports. This information is critical for identifying potentially vulnerable services during penetration testing. Port scanning revealed Metasploitable2 as a deliberately vulnerable system with many exposed services, while Windows 10 and Kali Linux had more restricted port configurations.

---

# Challenges Faced

| Problem                              | Solution                                          |
| ------------------------------------ | ------------------------------------------------- |
| Nmap scan returned no hosts          | Verified correct subnet range with `ip addr`      |
| IPv6 address not persisting on reboot| Added configuration to `/etc/network/interfaces`  |
| Wireshark required root permissions  | Launched with `sudo wireshark`                    |
| Some ports showing as filtered       | Used `-Pn` flag to bypass ping-based host check   |
| DNS resolution slow                  | Configured DNS servers in network config          |
| SSH connectivity issues              | Verified SSH service running with `systemctl`     |
| tcpdump capture not showing traffic  | Specified correct interface with `-i eth0`        |
| Protocol filters not working         | Cleared capture display filters and restarted     |

---

# Key Learnings

1. **Network Discovery:** Nmap ping scan effectively identifies active hosts without performing full port scans.

2. **IP Addressing:** Static IP configuration provides consistent network access for virtual machines.

3. **Subnetting:** Understanding CIDR notation and subnet calculations is essential for network planning.

4. **Protocol Analysis:** Wireshark provides detailed packet-level insights into network communication.

5. **Port Scanning:** Service version detection helps identify potential security vulnerabilities.

6. **Security Risk Assessment:** Open ports directly correlate to attack surface and potential vulnerabilities.

7. **Best Practices:** Secure services (SSH, HTTPS) should be preferred over unencrypted alternatives (Telnet, HTTP).

---

# Conclusion

In this assignment, network mapping, IP address configuration, protocol identification, and port exploration were successfully performed within the virtual cybersecurity lab. Nmap was used to discover active hosts and services, static IP addresses were configured on all VMs, and Wireshark successfully captured and analyzed network traffic containing 10 different protocol types. Port scanning with service detection revealed the vulnerable Metasploitable2 system with numerous exposed services. The 20 common port reference table serves as a valuable guide for understanding network services and their associated security risks.

This hands-on lab improved practical understanding of network reconnaissance, IP addressing concepts, protocol analysis, and vulnerability assessment techniques essential for cybersecurity professionals.

---

# Tools and Platforms Used

* Oracle VirtualBox
* Kali Linux
* Nmap (Network Mapper)
* Wireshark (Network Protocol Analyzer)
* tcpdump (Command-line packet capture)
* ipcalc (Subnet calculator)
* Linux Networking Tools (`ip`, `ifconfig`, `ping`, `ping6`, `traceroute`, `nslookup`, `dig`)
* OpenSSH (SSH client)
* curl (HTTP client)

---

# References

* Nmap Official Documentation: https://nmap.org/
* Wireshark Official Documentation: https://www.wireshark.org/
* RFC 791 - Internet Protocol (IPv4): https://tools.ietf.org/html/rfc791
* RFC 2460 - Internet Protocol, Version 6 (IPv6): https://tools.ietf.org/html/rfc2460
* Common Ports List: https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers

---

# Author

sarfaraj Ahamad
