# Testing Connectivity Between Virtual Machines Using Ping Commands

## Objective
The objective of this task was to verify successful network communication between all virtual machines configured in the cybersecurity lab environment.

---

# Virtual Machines Used

The following virtual machines were connected using the same NAT Network in VirtualBox:

- Kali Linux
- Windows 10
- Metasploitable2

---

# Network Configuration

All virtual machines were configured on the same NAT Network named:

```text
NatNetwork
```

This allowed:
- VM-to-VM communication
- Internet access
- Isolated lab environment

---

# Initial Issue Faced

During the connectivity testing process, multiple networking issues were encountered:

- Windows 10 VM repeatedly booted into installation setup after restart
- NAT Network was not properly configured initially
- VirtualBox showed:

```text
No NAT Network name specified
```

- Ping requests returned:

```text
Destination Host Unreachable
```

and

```text
No route to host
```

---

# Troubleshooting Steps Performed

## 1. Created a Proper NAT Network

Opened:

```text
File → Tools → Network Manager
```

Created a NAT Network named:

```text
NatNetwork
```

Enabled:
- DHCP
- IPv4 Support

---

## 2. Configured Network Adapter for All VMs

For each virtual machine:

```text
Settings → Network → Adapter 1
```

Configured:
- Attached To: NAT Network
- Name: NatNetwork
- Cable Connected: Enabled

---

## 3. Fixed Windows 10 Boot Issue

The Windows 10 ISO installer was removed after installation to prevent the VM from restarting the setup process during every boot.

Boot order was corrected by prioritizing:
- Hard Disk
- Disabling Optical boot

---

## 4. Renewed Network Configuration

Network interfaces were refreshed and verified using:

### Kali Linux

```bash
ip addr
```

### Windows 10

```cmd
ipconfig
```

### Metasploitable2

```bash
ifconfig
```

---

# Connectivity Testing

## Ping Test from Kali Linux

### Ping Windows 10

```bash
ping <Windows10-IP>
```

### Ping Metasploitable2

```bash
ping <Metasploitable2-IP>
```

---

## Ping Test from Windows 10

### Ping Kali Linux

```cmd
ping <Kali-IP>
```

### Ping Metasploitable2

```cmd
ping <Metasploitable2-IP>
```

---

# Results

Successful communication was established between:
- Kali Linux
- Windows 10
- Metasploitable2

The ping tests confirmed:
- Correct NAT Network configuration
- Functional VM networking
- Successful packet transmission
- Stable communication between all virtual machines

---

# Observations

- Each VM received a unique IP address.
- Network isolation was successfully maintained.
- All virtual machines communicated securely inside the lab environment.


---

# Skills Learned

- VirtualBox networking
- NAT Network configuration
- IP address verification
- Ping command usage
- Network troubleshooting
- VM communication testing
- Virtual lab management
