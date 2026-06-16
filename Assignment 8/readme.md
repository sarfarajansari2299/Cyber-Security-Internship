# ASSIGNMENT 8 : WINDOWS LOGIN BYPASS TECHNIQUES

## Objective

The objective of this assignment is to study Windows authentication mechanisms, password recovery concepts, accessibility features, and virtual machine recovery procedures in a controlled lab environment.

---

# 1. Sticky Keys Accessibility Feature

## Objective

Understand how Windows accessibility features operate before user authentication and why they must be protected from unauthorized modification.

---

## a. Overview

Sticky Keys is an accessibility feature that assists users who have difficulty pressing multiple keys simultaneously.

### Key Learning Points

* Accessibility applications can run before user login.
* System files should be protected from unauthorized changes.
* Physical access to a system can introduce security risks.
* Full-disk encryption helps mitigate offline attacks.

---

## Screenshot

<img width="1047" height="872" alt="image" src="https://github.com/user-attachments/assets/9f152a7a-8278-45d0-be38-5948ca6c3a07" />


---

## Observation

Accessibility features are designed to improve usability but can become a security concern if system files are modified by unauthorized users with physical access to a device.

---

# 2. Password Recovery Concepts

## Objective

Understand Windows password storage and recovery mechanisms.

---

## a. Password Storage

Windows stores local account information within the Security Account Manager (SAM) database.

### Key Learning Points

* User credentials are protected by Windows security mechanisms.
* Password recovery should only be performed on systems you own or are authorized to manage.
* Recovery tools are commonly used by system administrators when users forget passwords.

---

## Screenshot

<img width="1280" height="1032" alt="image" src="https://github.com/user-attachments/assets/83ad177a-5d66-42a5-a3df-3be767645bd4" />

<img width="1280" height="1032" alt="image" src="https://github.com/user-attachments/assets/c0004ca2-9ff7-4a56-a36f-3116e75c8afc" />


---

## Observation

Password recovery procedures demonstrate the importance of strong authentication controls and proper administrative access management.

---

# 3. Accessibility Utility Security

## Objective

Examine the role of accessibility applications within the Windows login environment.

---

## a. Accessibility Features

Examples include:

* Sticky Keys
* Narrator
* Magnifier
* On-Screen Keyboard
* Utility Manager

### Security Considerations

* Accessibility programs run before authentication.
* Operating system files should be protected through proper permissions.
* Security updates help prevent misuse of accessibility features.

---

## Screenshot

<img width="1280" height="1032" alt="image" src="https://github.com/user-attachments/assets/87818e69-b30b-433c-89a2-217cf56a03cc" />

<img width="1280" height="1032" alt="image" src="https://github.com/user-attachments/assets/262a45c8-2f2b-44de-b219-b01dd4def9e5" />

---

## Observation

Accessibility tools provide important functionality but must be protected through operating system security controls.

---

# 4. Password Recovery Tools Overview

## Objective

Learn how password auditing and recovery tools operate in authorized environments.

---

## a. Ophcrack

### Purpose

Ophcrack demonstrates password recovery techniques using rainbow tables.

### Concepts Covered

* Password hashing
* Hash comparison
* Rainbow tables
* Password complexity
* Authentication security

---

## Screenshot

```
Insert Screenshot Here
```

---

## Observation

Weak passwords are more susceptible to recovery techniques. Strong passwords significantly increase resistance to password-cracking methods.

---

# 5. Virtual Machine Snapshot and Recovery

## Objective

Practice safe testing procedures using virtual machine snapshots.

---

## a. Create Snapshot

### Procedure

1. Shut down the Windows VM.
2. Open VirtualBox Snapshot Manager.
3. Create a snapshot before testing.
4. Name the snapshot appropriately.

---

## Screenshot

```
Insert Screenshot Here
```

---

## b. Restore Snapshot

### Procedure

1. Open Snapshot Manager.
2. Select the desired snapshot.
3. Restore the snapshot.
4. Verify system functionality.

---

## Screenshot

```
Insert Screenshot Here
```

---

## Observation

Snapshots provide a reliable mechanism for reverting virtual machines to a known-good state after testing and experimentation.

---

# Security Best Practices

| Practice                    | Purpose                            |
| --------------------------- | ---------------------------------- |
| Strong Passwords            | Reduce password-cracking risk      |
| BitLocker Encryption        | Protect data from offline access   |
| Multi-Factor Authentication | Add an additional security layer   |
| Regular Updates             | Patch security vulnerabilities     |
| Restricted Physical Access  | Prevent unauthorized system access |
| Secure Backups              | Enable recovery after incidents    |

---

# Challenges Faced

| Problem                         | Solution                                       |
| ------------------------------- | ---------------------------------------------- |
| VM boot issues                  | Verified VirtualBox configuration              |
| Snapshot recovery confusion     | Practiced restore procedures                   |
| Authentication concepts         | Reviewed Windows security architecture         |
| Password security understanding | Studied password hashing and recovery concepts |

---

# Conclusion

This assignment provided practical exposure to Windows authentication concepts, password recovery mechanisms, accessibility feature security, and virtual machine recovery procedures. The exercises highlighted the importance of strong passwords, system hardening, physical security, and backup strategies in maintaining secure Windows environments.

---

# Tools and Platforms Used

* Windows 10 Virtual Machine
* VirtualBox
* Kali Linux
* Ophcrack (Concept Study)
* Windows Accessibility Features
* Snapshot Manager

---

# Author

Sarfaraj Ahamad

