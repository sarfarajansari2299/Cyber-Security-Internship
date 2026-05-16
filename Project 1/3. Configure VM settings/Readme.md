# Virtual Machine Configuration and Network Setup

## Objective
The objective of this task was to configure virtual machine resources and establish a secure NAT Network environment for communication between all virtual machines in the cybersecurity lab.

---

# Kali Linux RAM Configuration

## Configuration Steps

### Step 1: Open VirtualBox
Launched Oracle VM VirtualBox and selected the Kali Linux virtual machine.

### Step 2: Open Settings
Navigated to:

Settings → System → Motherboard

### Step 3: Allocate Memory
Configured RAM allocation for Kali Linux.

## RAM Settings
- Allocated RAM: 2048 MB (2 GB)

This allocation provided smooth performance for:
- Kali Linux tools
- Web browsing
- Terminal operations
- Network analysis
- Security testing

---

# Processor Configuration

## CPU Allocation
Configured:
- 1 CPU Cores

This improved:
- VM responsiveness
- Tool execution speed
- Multitasking performance

---

# NAT Network Configuration

## Objective
Configured all virtual machines on the same NAT Network to allow communication between:
- Kali Linux
- Metasploitable2
- Windows 10

while maintaining isolation from the host network.

---

# Steps to Configure NAT Network

## Step 1: Create NAT Network

Opened:

File → Tools → Network Manager

Created a new NAT Network with:
- DHCP Enabled
- IPv4 Support Enabled

---

## Step 2: Attach VMs to NAT Network

For each VM:

Settings → Network → Adapter 1

Configured:
- Enable Network Adapter
- Attached To: NAT Network
- Name: NatNetwork

Applied the same network settings to:
- Kali Linux
- Metasploitable2
- Windows 10

