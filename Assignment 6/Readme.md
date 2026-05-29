# Assignment 6: Network Mapping & IP Address Mastery

## Objective

The objective of this assignment is to gain hands-on experience with network discovery, IP addressing, subnetting, protocol analysis, and port scanning using Kali Linux, Wireshark, Nmap, Metasploitable2, and Windows 10 virtual machines.

---

# 1. Network Discovery Using Nmap

## Objective

Discover active hosts within the virtual lab network and identify running services.

### Step 1: Identify Local IP Address

#### Command

```bash
ip a
```

### Screenshot

<img width="1010" height="816" alt="image" src="https://github.com/user-attachments/assets/c0e2a89a-c826-4bda-a751-c063d3cbbf1f" />



---

### Step 2: Discover Active Hosts

#### Command

```bash
nmap -sn 10.0.2.3/24
```

#### Result

| Host            | IP Address |
| --------------- | ---------- |
| Kali Linux      | 10.0.2.3   |
| Metasploitable2 | 10.0.2.4   |
| Windows 10      | 10.0.2.15  |

### Screenshot

<img width="1010" height="816" alt="image" src="https://github.com/user-attachments/assets/cf3a2a39-fa31-4721-bcfa-ea710a0f023d" />


---

### Step 3: Scan Open Ports

#### Command

```bash
nmap 10.0.2.16
nmap 10.0.2.17
```

### Open Ports Found

#### Metasploitable2

| Port | Service      |
|------|-------------|
| 21   | FTP         |
| 22   | SSH         |
| 23   | Telnet      |
| 25   | SMTP        |
| 53   | Domain (DNS)|
| 80   | HTTP        |
| 111  | RPCBind     |
| 139  | NetBIOS-SSN |
| 445  | SMB         |
| 512  | Exec        |
| 513  | Login       |
| 514  | Shell       |
| 1524 | Ingreslock  |
| 2049 | NFS         |
| 2121 | CCProxy-FTP |
| 3306 | MySQL       |
| 3632 | DistCCD     |
| 5432 | PostgreSQL  |
| 5900 | VNC         |
| 6000 | X11         |
| 6667 | IRC         |
| 8009 | AJP13       |

#### Windows 10

| Port | Service |
| ---- | ------- |
| 135  | RPC     |
| 139  | NetBIOS |
| 445  | SMB     |
| 3389 | RDP     |

### Screenshot

> Insert screenshot showing Nmap port scan results.

---

### Step 4: Service Detection Scan

#### Command

```bash
nmap -sV 10.0.2.16
```

### Screenshot

> Insert screenshot showing service versions detected by Nmap.

---

# 2. Network Topology Diagram

## Network Diagram

```text
                    +-------------------+
                    |    Host Machine   |
                    |     Windows 10    |
                    +---------+---------+
                              |
                    =====================
                          NAT Network
                    =====================
                     /         |         \
                    /          |          \
                   /           |           \
        +---------------+ +---------------+ +---------------+
        | Kali Linux    | |Metasploitable2| | Windows 10 VM |
        | 10.0.2.15     | | 10.0.2.16     | | 10.0.2.17     |
        +---------------+ +---------------+ +---------------+
```

### Screenshot

> Insert screenshot of VirtualBox network configuration showing all VMs connected to the same NAT Network.

---

# 3. IP Address Configuration

## Static IPv4 Address Configuration

### Kali Linux

#### Edit Network Configuration

```bash
sudo nano /etc/network/interfaces
```

#### Example Configuration

```bash
auto eth0
iface eth0 inet static
address 192.168.10.10
netmask 255.255.255.0
gateway 192.168.10.1
```

### Screenshot

> Insert screenshot showing static IP configuration on Kali Linux.

---

### Windows 10 Static IP

1. Open Network Settings
2. Change Adapter Options
3. Open IPv4 Properties
4. Assign Static IP Address

#### Example

```text
IP Address : 192.168.20.10
Subnet Mask: 255.255.255.0
Gateway    : 192.168.20.1
```

### Screenshot

> Insert screenshot showing Windows IPv4 configuration screen.

---

# 4. Subnetting Practice

## Example 1

### Network

```text
192.168.1.0/24
```

### Calculation

| Item              | Value         |
| ----------------- | ------------- |
| Network Address   | 192.168.1.0   |
| First Host        | 192.168.1.1   |
| Last Host         | 192.168.1.254 |
| Broadcast Address | 192.168.1.255 |
| Total Hosts       | 254           |

---

## Example 2

### Network

```text
192.168.1.0/26
```

### Calculation

| Item              | Value        |
| ----------------- | ------------ |
| Network Address   | 192.168.1.0  |
| First Host        | 192.168.1.1  |
| Last Host         | 192.168.1.62 |
| Broadcast Address | 192.168.1.63 |
| Total Hosts       | 62           |

### Screenshot

> Insert screenshot from subnet calculator showing subnet calculations.

---

# 5. IPv6 Configuration

## Configure IPv6 Address

### Command

```bash
sudo ip -6 addr add 2001:db8::10/64 dev eth0
```

### Verify Configuration

```bash
ip -6 addr
```

### Screenshot

> Insert screenshot showing IPv6 address assigned to Kali Linux.

---

# 6. Connectivity Testing Between Subnets

## Ping Test

### Command

```bash
ping 192.168.20.10
```

### IPv6 Ping

```bash
ping6 2001:db8::10
```

### Screenshot

> Insert screenshot showing successful IPv4 and IPv6 ping replies.

---

# 7. Protocol Identification Using Wireshark

## Start Packet Capture

1. Open Wireshark
2. Select Active Interface
3. Start Capture
4. Generate Network Traffic

### Screenshot

> Insert screenshot showing Wireshark capture interface.

---

## Identified Protocols

| No | Protocol | Purpose                |
| -- | -------- | ---------------------- |
| 1  | ARP      | Address Resolution     |
| 2  | ICMP     | Ping                   |
| 3  | TCP      | Reliable Communication |
| 4  | UDP      | Fast Communication     |
| 5  | DNS      | Name Resolution        |
| 6  | HTTP     | Web Traffic            |
| 7  | HTTPS    | Secure Web Traffic     |
| 8  | DHCP     | IP Assignment          |
| 9  | SMB      | File Sharing           |
| 10 | SSH      | Secure Remote Access   |

### Screenshot

> Insert screenshot showing Wireshark protocol list.

---

## Protocol Filters Used

### ARP

```text
arp
```

### ICMP

```text
icmp
```

### TCP

```text
tcp
```

### UDP

```text
udp
```

### DNS

```text
dns
```

### HTTP

```text
http
```

### Screenshot

> Insert screenshot showing Wireshark display filters in action.

---

# 8. Packet Analysis

## Examined Fields

### Ethernet Header

* Source MAC Address
* Destination MAC Address

### IP Header

* Source IP Address
* Destination IP Address
* TTL

### TCP Header

* Source Port
* Destination Port
* Flags

### Screenshot

> Insert screenshot showing packet details pane in Wireshark.

---

# 9. Port Number Exploration

## Common Port Scan

### Command

```bash
nmap -p 21,22,23,25,53,80,443,3389,445 10.0.2.16
```

### Screenshot

> Insert screenshot showing targeted port scan results.

---

## Service Detection

### Command

```bash
nmap -sV 10.0.2.16
```

### Screenshot

> Insert screenshot showing service versions.

---

# 10. Twenty Common Port Numbers

| Port | Service         |
| ---- | --------------- |
| 20   | FTP Data        |
| 21   | FTP             |
| 22   | SSH             |
| 23   | Telnet          |
| 25   | SMTP            |
| 53   | DNS             |
| 67   | DHCP            |
| 68   | DHCP Client     |
| 69   | TFTP            |
| 80   | HTTP            |
| 110  | POP3            |
| 123  | NTP             |
| 135  | RPC             |
| 137  | NetBIOS         |
| 139  | NetBIOS Session |
| 143  | IMAP            |
| 161  | SNMP            |
| 389  | LDAP            |
| 443  | HTTPS           |
| 445  | SMB             |

---

# Tools Used

* Kali Linux
* Nmap
* Wireshark
* VirtualBox
* Windows 10
* Metasploitable2

---

# Challenges Faced

| Problem                         | Solution                           |
| ------------------------------- | ---------------------------------- |
| Host discovery not working      | Verified NAT Network configuration |
| VM connectivity issues          | Checked IP configuration           |
| Wireshark not capturing packets | Selected correct network interface |
| Service detection slow          | Used targeted Nmap scans           |

---

# Conclusion

This assignment provided practical experience in network discovery, IP addressing, subnetting, protocol analysis, and port scanning. Nmap was used to identify hosts, open ports, and services, while Wireshark was used to capture and analyze network traffic. Static IPv4, IPv6, and subnetting concepts were successfully implemented and tested within the virtual lab environment.

---

# Author

**Sarfaraj Ahamad**

