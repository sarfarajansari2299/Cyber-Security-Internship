# ASSIGNMENT 1: NETWORK MAPPING & IP ADDRESS MASTERY

## Objective

The objective of this assignment is to perform network mapping, IP address configuration, protocol identification, and port exploration within a virtual cybersecurity lab environment using Nmap, Wireshark, and Linux networking tools.

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
| Kali Linux      | 192.168.56.102 | Up     |
| Metasploitable2 | 192.168.56.104 | Up     |
| Windows 10      | 192.168.56.103 | Up     |

---

## Command

```bash
nmap -sn 192.168.56.0/24 -oN host_discovery.txt
```

---

## Screenshot

<img width="1010" height="816" alt="image" src="https://github.com/user-attachments/assets/ec4201e5-65be-423c-bbf0-afeeaaa6746a" />


---

# c. Determine Open Ports on Each Host

## Command

```bash
nmap 192.168.56.104
```


## Screenshot

```
```
## Open Ports Found on Metasploitable2 (192.168.56.104)

<img width="1005" height="679" alt="image" src="https://github.com/user-attachments/assets/4047079e-5b60-4ef7-bf4b-a4c59ddc3b8a" />



## Open Ports Found on Windows 10 (192.168.56.103)

<img width="1005" height="679" alt="image" src="https://github.com/user-attachments/assets/4d09197b-db75-420a-a547-4febd872e6b1" />



## Open Ports Found on kali (192.168.56.102)

<img width="1005" height="679" alt="image" src="https://github.com/user-attachments/assets/5a210404-17d8-4593-8251-7e382937b50c" />


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
   └─────────────┘   └─────────────┘  └─────────────┘
```

---

## Observation

Nmap successfully discovered all three VMs within the isolated host-only network. All machines responded to ping and port scans, confirming proper network configuration.

---

# 2. IP Addressing Practice

## Objective

Configure static IPv4 and IPv6 addresses across virtual machines and test inter-subnet connectivity.

---

# a. Configure Static IPv4 Addresses on All VMs

## Steps Performed

1. Edited the network interfaces configuration file on Kali Linux.
2. Assigned a static IP address within the host-only subnet.
3. Restarted the networking service to apply changes.

---

## Command (Kali Linux)

```bash
sudo nano /etc/network/interfaces
```

## Configuration Added

```text
auto eth0
iface eth0 inet static
    address 192.168.56.101
    netmask 255.255.255.0
    gateway 192.168.56.1
```
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


---

# b. Subnetting Calculations

## Subnet Practice Table

| Network Address | Subnet Mask     | CIDR | Hosts Available | Broadcast Address |
| --------------- | --------------- | ---- | --------------- | ----------------- |
| 192.168.56.0    | 255.255.255.0   | /24  | 254             | 192.168.56.255    |
| 192.168.56.0    | 255.255.255.128 | /25  | 126             | 192.168.56.127    |
| 192.168.56.0    | 255.255.255.192 | /26  | 62              | 192.168.56.63     |
| 10.0.2.0        | 255.255.255.0   | /24  | 254             | 10.0.2.255        |

---

## Tool Used

```bash
ipcalc 192.168.56.0/24
```

---

## Screenshot

<!-- Add screenshot of ipcalc output here -->

---

# c. Set Up IPv6 Address on Kali Linux

## Command

```bash
sudo ip -6 addr add fd00::1/64 dev eth0
```

---

## Verify IPv6 Assignment

```bash
ip -6 addr show eth0
```

---

## Screenshot

<!-- Add screenshot of IPv6 address assignment here -->

---

# d. Test Connectivity Between VMs

## IPv4 Ping Test

```bash
ping 192.168.56.102
```

## IPv6 Ping Test

```bash
ping6 fd00::2
```

---

## Screenshot

<!-- Add screenshot of ping test results here -->

---

## Observation

Static IP addresses were successfully configured on all VMs. Subnetting calculations confirmed the correct number of usable hosts per subnet. IPv6 addressing was configured and verified on Kali Linux.

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

---

## Command to Launch Wireshark (CLI)

```bash
sudo wireshark &
```

---

## Screenshot

<!-- Add screenshot of Wireshark capture session here -->

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

## Screenshot

<!-- Add screenshot of Wireshark showing identified protocols here -->

---

# c. Analyze Packet Headers and Payloads

## ICMP Packet Analysis

```
Frame: 64 bytes
Ethernet Header:
  Source MAC: 08:00:27:xx:xx:xx
  Destination MAC: 08:00:27:xx:xx:xx
IP Header:
  Source IP: 192.168.56.101
  Destination IP: 192.168.56.102
  TTL: 64
  Protocol: ICMP (1)
ICMP Header:
  Type: 8 (Echo Request)
  Code: 0
  Checksum: Valid
```

---

## Screenshot

<!-- Add screenshot of packet header analysis in Wireshark here -->

---

# d. Filter Traffic by Protocol Type

## Wireshark Display Filters Used

```text
icmp
arp
tcp
udp
dns
http
tcp.port == 22
ftp
bootp
nbns
```

---

## Command to Capture Traffic via CLI (tcpdump)

```bash
sudo tcpdump -i eth0 -w capture.pcap
```

---

## Open Capture in Wireshark

```bash
wireshark capture.pcap
```

---

## Screenshot

<!-- Add screenshot of filtered Wireshark output here -->

---

## Observation

Wireshark successfully captured and displayed multiple protocol types. Filtering by protocol allowed targeted analysis of specific traffic types within the virtual lab network.

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

---

## Results

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

<!-- Add screenshot of port scan output here -->

---

# b. Identify Services Running on Each Port

## Using Nmap Service Detection

```bash
nmap -sV -p 21,22,23,25,53,80,443,3389,445 192.168.56.102
```

---

## Screenshot

<!-- Add screenshot of service version detection here -->

---

# c. Nmap Service Detection

## Command

```bash
nmap -sV 192.168.56.102
```

---

## Sample Output

```text
PORT     STATE  SERVICE     VERSION
21/tcp   open   ftp         vsftpd 2.3.4
22/tcp   open   ssh         OpenSSH 4.7p1
23/tcp   open   telnet      Linux telnetd
25/tcp   open   smtp        Postfix smtpd
80/tcp   open   http        Apache httpd 2.2.8
3306/tcp open   mysql       MySQL 5.0.51a
5432/tcp open   postgresql  PostgreSQL 8.3
8180/tcp open   http        Apache Tomcat/Coyote
```

---

## Screenshot

<!-- Add screenshot of nmap -sV output here -->

---

# d. 20 Common Port Numbers Reference

| Port | Protocol | Service                           | Description                                        |
| ---- | -------- | --------------------------------- | -------------------------------------------------- |
| 20   | TCP      | FTP Data                          | File Transfer Protocol – data channel              |
| 21   | TCP      | FTP Control                       | File Transfer Protocol – command channel           |
| 22   | TCP      | SSH                               | Secure Shell – encrypted remote access             |
| 23   | TCP      | Telnet                            | Unencrypted remote terminal access                 |
| 25   | TCP      | SMTP                              | Simple Mail Transfer Protocol – email sending      |
| 53   | TCP/UDP  | DNS                               | Domain Name System – hostname resolution           |
| 67   | UDP      | DHCP Server                       | Dynamic Host Configuration Protocol – IP leasing  |
| 68   | UDP      | DHCP Client                       | DHCP client port                                   |
| 80   | TCP      | HTTP                              | HyperText Transfer Protocol – web traffic          |
| 110  | TCP      | POP3                              | Post Office Protocol – email retrieval             |
| 143  | TCP      | IMAP                              | Internet Message Access Protocol – email access    |
| 443  | TCP      | HTTPS                             | HTTP Secure – encrypted web traffic                |
| 445  | TCP      | SMB                               | Server Message Block – Windows file sharing        |
| 3306 | TCP      | MySQL                             | MySQL database service                             |
| 3389 | TCP      | RDP                               | Remote Desktop Protocol – Windows remote access    |
| 5432 | TCP      | PostgreSQL                        | PostgreSQL database service                        |
| 8080 | TCP      | HTTP Alternate                    | Alternate HTTP port / proxy                        |
| 8443 | TCP      | HTTPS Alternate                   | Alternate HTTPS port                               |
| 139  | TCP      | NetBIOS-SSN                       | NetBIOS Session Service                            |
| 6667 | TCP      | IRC                               | Internet Relay Chat                                |

---

## Screenshot

<!-- Add screenshot of nmap port number documentation here -->

---

## Observation

Nmap's service detection (`-sV`) accurately identified the software versions running on open ports. This information is critical for identifying potentially vulnerable services during penetration testing.

---

# Challenges Faced

| Problem                              | Solution                                          |
| ------------------------------------ | ------------------------------------------------- |
| Nmap scan returned no hosts          | Verified correct subnet range with `ip addr`      |
| IPv6 address not persisting on reboot| Added configuration to `/etc/network/interfaces`  |
| Wireshark required root permissions  | Launched with `sudo wireshark`                    |
| Some ports showing as filtered       | Used `-Pn` flag to bypass ping-based host check   |

---

# Conclusion

In this assignment, network mapping, IP address configuration, protocol identification, and port exploration were successfully performed within the virtual cybersecurity lab. Nmap was used to discover hosts and identify open services, Wireshark captured and analyzed 10 different network protocols, static IPv4 and IPv6 addresses were configured, and 20 common port numbers were documented. These skills form a fundamental foundation for cybersecurity and penetration testing work.

---

# Tools and Platforms Used

* Oracle VirtualBox
* Kali Linux
* Nmap
* Wireshark
* tcpdump
* ipcalc
* Linux Networking Tools (`ip`, `ifconfig`, `ping`, `ping6`)

---

# Author

sarfaraj Ahamad
