# Project 2 Kali Linux Desktop Environment Exploration

## Objective

Explore the Kali Linux desktop environment and identify important cybersecurity tools used in penetration testing and ethical hacking.

---

# 1. Kali Linux Desktop Environment

Kali Linux is a Debian-based Linux distribution specially designed for cybersecurity professionals, ethical hackers, and penetration testers. It contains hundreds of pre-installed security tools.

## Kali Linux Desktop

<img width="1031" height="534" alt="1" src="https://github.com/user-attachments/assets/38d5e4d1-2819-4b3f-8a51-29c6f5257093" />
<img width="889" height="500" alt="2" src="https://github.com/user-attachments/assets/292ffe19-7dce-4a9b-b011-4f2e45182e24" />
<img width="1205" height="810" alt="3" src="https://github.com/user-attachments/assets/56d6acef-2409-40e3-bc36-84be41ecd65c" />
<img width="889" height="500" alt="4" src="https://github.com/user-attachments/assets/5dd2d401-92e0-40f4-a1f8-cef70005e804" />
<img width="901" height="776" alt="5" src="https://github.com/user-attachments/assets/8bd0ffe4-8596-4f0a-a47a-0a443d497687" />






---

# 2. Navigating Through Application Menus

## Steps

1. Start the Kali Linux virtual machine.
2. Login with your username and password.
3. Click on the **Applications** menu located at the top-left corner.
4. Explore different tool categories available in Kali Linux.

## Main Categories in Kali Linux

* Information Gathering
* Vulnerability Analysis
* Web Application Analysis
* Password Attacks
* Wireless Attacks
* Exploitation Tools
* Sniffing & Spoofing
* Reverse Engineering

## Applications Menu
<img width="901" height="776" alt="5" src="https://github.com/user-attachments/assets/b8fe0c32-32d1-493f-9f4f-d9bc44c55ddd" />

<img width="1031" height="534" alt="1" src="https://github.com/user-attachments/assets/2d50264c-0117-4398-86c1-baf260d2d680" />



---

# 3. Information Gathering Tools

## Navigation

Applications → Information Gathering

## Purpose

Information Gathering tools are used during the reconnaissance phase of penetration testing to collect information about systems, domains, networks, and targets.

## Common Tools

| Tool         | Purpose                             |
| ------------ | ----------------------------------- |
| Nmap         | Network scanning and host discovery |
| Whois        | Domain information lookup           |
| theHarvester | Email and subdomain gathering       |
| Maltego      | OSINT and relationship mapping      |
| Netdiscover  | Network discovery                   |

## Information Gathering tools

<img width="1919" height="951" alt="6" src="https://github.com/user-attachments/assets/6cf11fb9-c299-4a6b-a16f-96d884676c17" />
<img width="1914" height="983" alt="7" src="https://github.com/user-attachments/assets/5b36f885-fe26-4f72-b2a5-f890321a0bf6" />
<img width="1912" height="983" alt="8" src="https://github.com/user-attachments/assets/5030bde5-3eb7-4901-a7c3-2d9cb56edcab" />
<img width="1437" height="1191" alt="9" src="https://github.com/user-attachments/assets/a9a0ea9b-a8cb-42a8-858e-7d89dac3e291" />


## Observation

These tools help security professionals gather target information before performing vulnerability assessment or penetration testing.

---

# 4. Vulnerability Analysis Tools

## Navigation

Applications → Vulnerability Analysis

## Purpose

Vulnerability Analysis tools are used to identify security weaknesses, outdated software, and vulnerabilities in systems and networks.

## Common Tools

| Tool                | Purpose                          |
| ------------------- | -------------------------------- |
| Nikto               | Web server vulnerability scanner |
| OpenVAS / Greenbone | Vulnerability assessment         |
| Legion              | Automated penetration testing    |
| Nmap NSE Scripts    | Vulnerability detection          |

## Vulnerability Analysis Menu

<img width="1747" height="1009" alt="10" src="https://github.com/user-attachments/assets/c85ce801-2bb9-4955-bdc9-27150e6e7c9d" />
<img width="924" height="941" alt="11" src="https://github.com/user-attachments/assets/0d30604c-5e58-4c77-b9a0-2491fba53459" />
<img width="743" height="402" alt="12" src="https://github.com/user-attachments/assets/d09e24ef-dc8f-4b31-954d-679dc7ed0c5f" />
<img width="654" height="824" alt="13" src="https://github.com/user-attachments/assets/a1ef51c6-bc07-49af-b6f3-737b20a8c2fb" />
<img width="1596" height="968" alt="14" src="https://github.com/user-attachments/assets/1bc55c25-3f10-494a-98fa-280121eabd62" />

## Observation

These tools help in detecting vulnerabilities that attackers might exploit.

---

# 5. Web Application Analysis Tools

## Navigation

Applications → Web Application Analysis

## Purpose

Web Application Analysis tools are used to test websites and web applications for security vulnerabilities.

## Common Tools

| Tool            | Purpose                          |
| --------------- | -------------------------------- |
| Burp Suite      | Web application security testing |
| OWASP ZAP       | Web vulnerability scanner        |
| SQLmap          | SQL injection testing            |
| Dirb / Gobuster | Directory brute forcing          |
| Wfuzz           | Web fuzzing tool                 |

## Burp Suite Tool

<img width="1369" height="672" alt="15" src="https://github.com/user-attachments/assets/8a35b2f3-ce25-4452-91a6-4d7c9a3d3dfe" />
<img width="1155" height="721" alt="16" src="https://github.com/user-attachments/assets/17541d1e-4f14-487a-b029-f58c9e194a98" />
<img width="1580" height="1208" alt="17" src="https://github.com/user-attachments/assets/3e4eb2b2-5145-4468-a1c8-2b482c50a248" />
<img width="800" height="345" alt="18" src="https://github.com/user-attachments/assets/cb72e69c-f9ca-452a-a038-dae48ba662a2" />






## Observation

These tools help identify vulnerabilities such as:

* SQL Injection
* Cross-Site Scripting (XSS)
* Authentication flaws
* Security misconfigurations
* Directory traversal

---

# Conclusion

In this task, the Kali Linux desktop environment was explored successfully. Different cybersecurity tool categories were identified and accessed through the Applications menu. Important tools related to Information Gathering, Vulnerability Analysis, and Web Application Analysis were explored and understood.

This activity helped in understanding the structure of Kali Linux and the role of various tools used in ethical hacking and penetration testing.

---

# Tools Explored

* Nmap
* Whois
* theHarvester
* Maltego
* Nikto
* OpenVAS
* Burp Suite
* OWASP ZAP
* SQLmap

---

# Author

Sarfaraj Ahamad
