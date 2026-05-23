# ASSIGNMENT 5: SECURE LAB CONFIGURATION CHALLENGE

## Objective

The objective of this assignment is to configure a secure and isolated cybersecurity lab environment using VirtualBox and Kali Linux. This assignment focuses on network isolation, VM security practices, user management, SSH configuration, and network traffic monitoring.

---

# 1. Configure Isolated Network Environment

## Objective

Create a secure isolated network environment for penetration testing practice without affecting the home network.

---

# a. Create Custom NAT Network in VirtualBox

## Steps Performed

1. Opened VirtualBox.
2. Navigated to:
   `File → Tools → Network Manager`
3. Created a new NAT Network.
4. Enabled DHCP.
5. Assigned all VMs to the same NAT Network.

---

## NAT Network Configuration

| Setting      | Value        |
| ------------ | ------------ |
| Network Name | CyberLab-NAT |
| Network CIDR | 10.0.2.0/24  |
| DHCP Enabled | Yes          |

---

## Command Verification

```bash id="m7yoe2"
ip addr
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/c82f8cf6-11e0-4550-b6e8-da75080e1378" />


---

# b. Configure Host-Only Network

## Steps Performed

1. Opened VirtualBox Network Manager.
2. Created Host-Only Adapter.
3. Assigned VMs to Host-Only Adapter.
4. Verified isolated communication between VMs.

---

## Host-Only Adapter Configuration

| VM              | IP Address     |
| --------------- | -------------- |
| Kali Linux      | 192.168.56.101 |
| Metasploitable2 | 192.168.56.102 |
| Windows 10      | 192.168.56.103 |

---

## Screenshot

<img width="975" height="647" alt="image" src="https://github.com/user-attachments/assets/ead3aa1d-c43d-4459-a004-90d69c72556e" />

<img width="975" height="647" alt="image" src="https://github.com/user-attachments/assets/f5ab4a53-eef6-4f71-ba77-295d0167d7d5" />

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/f9300a74-4f28-4ac5-813e-8120b3019281" />


---

# c. Restrict Access to Home Network

## Configuration Performed

* Disabled Bridged Adapter.
* Enabled only NAT Network and Host-Only Adapter.
* Verified that VMs could not directly access home devices.

---

## Screenshot

<img width="975" height="647" alt="image" src="https://github.com/user-attachments/assets/b20a29ff-68fd-48ae-8fc7-bc8a14ac8a96" />

<img width="975" height="647" alt="image" src="https://github.com/user-attachments/assets/1e7fef92-6b8c-4f4a-8e66-10abba3f4bfb" />



---

# d. Test Network Isolation

## Ping Test

### Command

```bash id="9ujfxl"
ping 192.168.56.102
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/d8248d75-67b9-46b2-9716-d1e64fd411be" />


---

## Traceroute Test

### Command

```bash id="if4m3l"
traceroute 192.168.56.102
```

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/f1340ca5-632b-441d-a9c7-3701aabebf90" />


---

## Observation

The isolated network environment allowed VM-to-VM communication while preventing direct interaction with the host home network.

---

# 2. Implement Lab Safety Measures

## Objective

Apply security best practices to protect the host system and maintain safe penetration testing conditions.

---

# a. Disable Shared Folders

## Steps Performed

1. Opened VM Settings.
2. Navigated to:
   `Settings → Shared Folders`
3. Removed all shared folders.

---

## Screenshot

<img width="975" height="647" alt="image" src="https://github.com/user-attachments/assets/5f737fb0-6d48-4a13-bf44-12824e8668b3" />


---

# b. Disable Clipboard Sharing

## Steps Performed

1. Opened VM Settings.
2. Navigated to:
   `Settings → General → Advanced`
3. Set Shared Clipboard to:
   `Disabled`

---

## Screenshot

<img width="975" height="647" alt="image" src="https://github.com/user-attachments/assets/40e6830c-5a1c-49ee-9461-b7325870ee17" />


---

# c. Create VM Snapshots

## Steps Performed

1. Shut down virtual machines.
2. Opened Snapshot Manager.
3. Created clean snapshots before testing.

---

## Snapshot Names

* Kali Clean Snapshot
* Windows10 Clean Snapshot
* Metasploitable2 Clean Snapshot

---

## Screenshot

<img width="960" height="1020" alt="image" src="https://github.com/user-attachments/assets/e88b752c-d343-4619-a4f1-003da8d0d032" />
<img width="960" height="1020" alt="image" src="https://github.com/user-attachments/assets/c73d0037-681f-414a-80ad-ef668c0f838d" />
<img width="960" height="1020" alt="image" src="https://github.com/user-attachments/assets/8185badf-6996-4d00-825e-c5dc8ee15cb4" />


---

# d. Restore VM Snapshot

## Steps Performed

1. Opened Snapshot Manager.
2. Selected clean snapshot.
3. Clicked Restore Snapshot.

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/4cd263d9-8a33-4b2f-a3ae-eb19a85e0196" />


---

## Observation

Snapshots provide a quick recovery method to restore VMs to a safe state after testing activities.

---

# 3. User and Permission Configuration

## Objective

Configure secure user accounts and remote access in Kali Linux.

---

# a. Create Non-Root User

## Command

```bash id="y7zbxm"
sudo adduser cyberuser
```

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/008d415f-cbfc-4eb4-a44d-0e35e348020a" />


---

# b. Configure Sudo Privileges

## Command

```bash id="nq54ma"
sudo usermod -aG sudo cyberuser
```

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/97904887-9ae1-4a82-b17a-ffed7d994772" />


---

# c. Switch Users Using su

## Command

```bash id="2b3pzx"
su cyberuser
```

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/3890ff75-e5af-48e9-b8ec-58b0242f79a4" />


---

# d. Configure SSH Access Between VMs

## Install OpenSSH Server

### Command

```bash id="mjjcax"
sudo apt install openssh-server
```
## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/5fe2080d-3bd1-4c30-9cf5-6e1e43d5772e" />

---

## Start SSH Service

### Command

```bash id="jpz4a8"
sudo systemctl start ssh
sudo systemctl enable ssh
```
## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/2f191742-6d48-47a0-8555-e21b09bf7a03" />

---

## Connect Using SSH

### Command

```bash id="4p8z8f"
ssh cyberuser@192.168.56.102
```

---

# Issue Faced

While testing SSH connectivity using:

```bash id="z7k4qx"
ssh cyberuser@192.168.56.102
```

the following error occurred:

```text id="p8v2dc"
ssh: connect to host 192.168.56.102 port 22: connection refused
```

---

# Cause of the Issue

Initially, the SSH service was not properly configured for the user account being used for authentication.

Although the OpenSSH service was running, the problem was related to:

* Incorrect or unset password for the `cyberuser`
* Authentication failure during SSH login

As a result, SSH access could not be completed successfully.

---

# Troubleshooting Performed

## 1. Verified SSH Service Status

The following command was executed:

```bash id="r3m7qo"
service ssh status
```

Result:

```text id="d5x9yn"
Active: active (running)
```

This confirmed that the SSH server was working properly.

---

## 2. Verified User Configuration

The `cyberuser` account was checked and it was determined that the password needed to be reset.

---

# Solution Implemented

The password for the user was changed using:

```bash id="u6k1fp"
sudo passwd cyberuser
```

A new password was configured successfully.

---

# Successful SSH Connection

After changing the password, SSH login worked successfully using:

```bash id="m2v8ra"
ssh cyberuser@192.168.56.102
```

The system then authenticated correctly and established a secure SSH session.

---

# Final Result

SSH connectivity between the virtual machines was successfully established after correcting the user authentication issue by resetting the password for the `cyberuser` account.

---

# Observation

The issue was caused by incorrect user authentication credentials. After resetting the user password and verifying that the SSH service was active, secure remote access through SSH was successfully achieved.

---
## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/a1c5694a-ce4c-4a83-9efa-12f8430b5b31" />


---
## Observation

SSH allows secure remote access and management between virtual machines within the isolated lab environment.

---

# 4. Network Monitoring Setup

## Objective

Monitor and analyze network traffic between virtual machines.

---

# a. Capture Traffic Using Wireshark

## Steps Performed

1. Opened Wireshark in Kali Linux.
2. Selected active network adapter.
3. Started packet capture.
4. Generated traffic using ping command.

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/fb41c16b-0544-48ae-a583-1779b09d3f91" />

---

# b. Monitor Network Interfaces

## Using ifconfig

### Command

```bash id="mjlwm0"
ifconfig
```
## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/542fed88-6171-4301-8383-9b11d15e6e4a" />

---

## Using ip addr

### Command

```bash id="2nl3cz"
ip addr
```
---

## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/8dac0427-5dde-428e-aefe-789f795eec27" />


---

# c. Test Connectivity Using netstat

## Command

```bash id="7d2xqo"
netstat -tulnp
```

---

## Screenshot

<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/171941c1-440d-458a-9d49-e91c5b059f5d" />


---

# d. Test Connectivity Using ss

## Command

```bash id="6jhvxa"
ss -tulnp
```

---

## Screenshot
<img width="957" height="1017" alt="image" src="https://github.com/user-attachments/assets/12d158eb-6640-4589-bced-6611eb6802d7" />


---

## Observation

Wireshark and Linux network monitoring commands help analyze network traffic, open ports, and active network services.

---

# Challenges Faced

| Problem                             | Solution                      |
| ----------------------------------- | ----------------------------- |
| VMs accessing internet unexpectedly | Disabled Bridged Adapter      |
| SSH connection failed initially     | Started SSH service manually  |
| Host-only network not working       | Reconfigured adapter settings |
| Wireshark permission issues         | Used sudo privileges          |

---

# Conclusion

In this assignment, a secure and isolated virtual cybersecurity lab was successfully configured using VirtualBox and Kali Linux. Network isolation, user management, SSH access, snapshot recovery, and network monitoring were implemented successfully. These configurations help create a safe environment for cybersecurity testing and penetration testing practice.

---

# Tools and Platforms Used

* Oracle VirtualBox
* Kali Linux
* Wireshark
* OpenSSH Server
* Linux Networking Tools

---

# Author

sarfaraj Ahamad

