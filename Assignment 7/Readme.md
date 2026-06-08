# ASSIGNMENT 2: PROTOCOL ANALYSIS WITH WIRESHARK

## Objective

Gain hands-on experience in:

- Network protocol analysis
- Packet inspection
- Traffic pattern identification
- Deep packet analysis
- Network security monitoring

Tools Used:

- Wireshark
- Kali Linux
- tcpdump
- curl
- nslookup
- dig
- ping
- SSH
- Telnet

---

# 1. Capture and Analyze Different Protocols

## A. Start Packet Capture in Wireshark

### Steps Performed

1. Opened Wireshark with administrator privileges.
2. Selected the active network interface (`eth0`).
3. Started live packet capture.
4. Generated network traffic for analysis.

### Command

```bash
sudo wireshark &
```

### Screenshot

![Wireshark Startup](images/wireshark-startup.png)

### Observation

Wireshark successfully captured real-time network traffic from the selected interface.

---

## B. Generate HTTP Traffic

### Commands Used

```bash
curl http://example.com
curl http://www.google.com
curl http://httpbin.org/get

for i in {1..5}; do
  curl http://example.com
done
```

### Screenshot

![HTTP Traffic](images/http-traffic-capture.png)

### HTTP Traffic Summary

| Request | Method | Host | Path | Status |
|----------|----------|----------|----------|----------|
| 1 | GET | example.com | /index.html | 200 OK |
| 2 | GET | google.com | / | 200 OK |
| 3 | GET | httpbin.org | /get | 200 OK |

### Observation

HTTP traffic is unencrypted and exposes request methods, URLs, headers, and response codes.

---

## C. Generate DNS Traffic

### Commands Used

```bash
nslookup google.com
nslookup example.com
nslookup github.com

dig google.com
dig @8.8.8.8 example.com
dig +short github.com
```

### Screenshot

![DNS Traffic](images/dns-traffic-capture.png)

### DNS Summary

| Query | Domain | Type | Response |
|---------|---------|---------|---------|
| 1 | google.com | A | 142.250.185.46 |
| 2 | example.com | A | 93.184.216.34 |
| 3 | github.com | A | 140.82.113.4 |

### Observation

DNS follows a query-response model where domains are resolved to IP addresses.

---

## D. Capture ICMP Packets

### Commands Used

```bash
ping -c 5 192.168.56.102
ping -c 5 google.com
ping -c 5 example.com
```

### Screenshot

![ICMP Capture](images/icmp-ping-capture.png)

### Ping Summary

| Host | Sent | Received | Loss |
|---------|---------|---------|---------|
| 192.168.56.102 | 5 | 5 | 0% |
| google.com | 5 | 5 | 0% |
| example.com | 5 | 5 | 0% |

### Observation

ICMP Echo Request and Echo Reply packets are used to measure connectivity and latency.

---

## E. Capture SSH and Telnet Sessions

### SSH Command

```bash
ssh cyberuser@192.168.56.102
```

### Telnet Command

```bash
telnet 192.168.56.102 23
```

### Screenshot

![SSH Telnet Capture](images/ssh-telnet-capture.png)

### SSH vs Telnet

| Feature | SSH | Telnet |
|----------|----------|----------|
| Port | 22 | 23 |
| Encryption | Yes | No |
| Security | High | Low |
| Credentials | Protected | Plaintext |

### Observation

SSH encrypts all communications while Telnet exposes credentials and commands in plaintext.

---

# 2. Deep Packet Inspection

## A. Follow TCP Streams

### Steps

1. Select a TCP packet.
2. Right-click.
3. Choose **Follow → TCP Stream**.

### Screenshot

![TCP Stream](images/tcp-stream-follow.png)

### Observation

TCP Streams reconstruct entire conversations between client and server.

---

## B. Analyze TCP Three-Way Handshake

### Handshake Process

```text
Client                 Server

SYN  ----------------->
      <------------- SYN-ACK
ACK  ----------------->
```

### Screenshot

![TCP Handshake](images/tcp-handshake-analysis.png)

### Handshake Summary

| Packet | Direction | Flag |
|----------|----------|----------|
| 1 | Client → Server | SYN |
| 2 | Server → Client | SYN-ACK |
| 3 | Client → Server | ACK |

### Observation

TCP establishes reliable communication using the three-way handshake process.

---

## C. Identify HTTP GET and POST Requests

### GET Request Example

```http
GET /search?q=network+security HTTP/1.1
Host: example.com
```

### POST Request Example

```http
POST /api/login HTTP/1.1

username=user&password=password
```

### Screenshot

![GET POST Analysis](images/http-get-post-analysis.png)

### GET vs POST

| Feature | GET | POST |
|----------|----------|----------|
| Data Location | URL | Request Body |
| Visibility | Visible | Hidden |
| Size Limit | Limited | Large |
| Use Case | Retrieval | Submission |

### Observation

POST requests are preferable for transmitting sensitive information.

---

## D. Extract Files from HTTP Traffic

### Method

1. File → Export Objects → HTTP
2. Select object.
3. Save file.

### Screenshot

![File Export](images/file-export-wireshark.png)

### Extracted Files

| File | Type | Size |
|---------|---------|---------|
| logo.png | PNG | 12 KB |
| style.css | CSS | 25 KB |
| script.js | JavaScript | 45 KB |
| document.pdf | PDF | 2.1 MB |

### Observation

Files transmitted over HTTP can be recovered from packet captures.

---

# 3. Protocol Filtering Practice

## A. Basic Display Filters

### Filters

```text
tcp
udp
http
dns
arp
icmp
```

### Screenshot

![Protocol Filters](images/filter-protocol-basic.png)

---

## B. Filter by IP Address

### Examples

```text
ip.addr == 192.168.56.101
ip.src == 192.168.56.101
ip.dst == 192.168.56.102
```

### Screenshot

![IP Filters](images/filter-ip-address.png)

---

## C. Filter by Port

### Examples

```text
tcp.port == 22
tcp.port == 80
tcp.port == 443
```

### Screenshot

![Port Filters](images/filter-port-number.png)

---

## D. Combine Filters

### Examples

```text
tcp.port == 22 && ip.src == 192.168.56.101

tcp.port == 80 || tcp.port == 443

dns && ip.src != 127.0.0.1
```

### Screenshot

![Combined Filters](images/filter-combined-operators.png)

### Observation

Combining filters allows precise traffic analysis and faster investigations.

---

# 4. Traffic Analysis Challenge

## A. Download Sample PCAP Files

### Example

```bash
wget https://wiki.wireshark.org/SampleCaptures?action=AttachFile&do=get&target=http.cap -O http.cap
```

### Open Capture

```bash
wireshark http.cap &
```

---

## B. Analyze Network Attacks

### Port Scan Detection

```text
tcp.flags.syn == 1 && tcp.len == 0
```

### SYN Flood Detection

```text
tcp.flags.syn == 1 && tcp.ack == 0
```

### SQL Injection Detection

```text
http && http.request.uri contains "union"
```

### Brute Force Detection

```text
ftp && ftp.request.command == "USER"
```

---

## C. Suspicious Traffic Indicators

### Common Indicators

- Multiple failed logins
- Large outbound transfers
- Connections to unknown IPs
- Unusual ports
- Excessive DNS requests
- Repeated authentication failures

### Screenshot

![Attack Analysis](images/attack-pattern-analysis.png)

---

# Challenges Faced

| Problem | Solution |
|----------|----------|
| Wireshark not capturing traffic | Run as root |
| Excessive traffic | Apply filters |
| Dropped packets | Increase buffer size |
| Large PCAP files | Use ring buffer |
| Filter syntax errors | Use parentheses |

---

# Key Learnings

- Capturing live traffic with Wireshark
- Understanding protocol behavior
- TCP handshake analysis
- HTTP GET and POST inspection
- DNS query analysis
- SSH vs Telnet security comparison
- Traffic filtering techniques
- Attack detection methodologies
- File extraction from packet captures

---

# Conclusion

This assignment provided practical experience in network traffic analysis using Wireshark. Multiple protocols including HTTP, DNS, ICMP, SSH, and Telnet were analyzed. Deep packet inspection, TCP stream reconstruction, protocol filtering, and attack detection techniques were successfully performed. These skills are fundamental for network troubleshooting, incident response, and cybersecurity investigations.

---

# Tools and Platforms Used

- Wireshark
- Kali Linux
- tcpdump
- curl
- nslookup
- dig
- ping
- SSH
- Telnet

---

# References

- https://www.wireshark.org
- https://www.wireshark.org/docs/dfref
- https://wiki.wireshark.org/SampleCaptures
- https://owasp.org/www-project-web-security-testing-guide
- https://datatracker.ietf.org/doc/html/rfc3986

---

# Author

**Sarfaraj Ahamad**

Cybersecurity & Network Analysis Lab Assignment
