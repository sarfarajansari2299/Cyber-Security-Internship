# Assignment 3 Linux File System Treasure Hunt

## Objective

The objective of this assignment is to explore the Linux file system hierarchy, understand directory structures, navigate files and folders using Linux commands, and analyze file permissions in Kali Linux.

---

# 1. Exploring the Linux File System Structure

Linux organizes files and directories in a hierarchical structure starting from the root directory `/`.

The following important directories were explored during this activity:

* `/home`
* `/etc`
* `/var`
* `/usr`
* `/bin`
* `/sbin`
* `/tmp`
* `/root`

---

# a. Explore Important Linux Directories

## Linux File System Structure

```text id="p3a7tk"
/
├── home
├── etc
├── var
├── usr
├── bin
├── sbin
├── tmp
└── root
```

## Root Directory Exploration

![Image](https://images.openai.com/static-rsc-4/jlnRuUPLvGYn2cLCWF7h1xi-glgj5NUiuUJan3lumE00jkHyX7ukQdmUcMfriIDdzNcsn01S6HQ-wuj4UL6fZ7O0nOa3uY22BrVxIlW6fooHAx7RhN5vdvx2OhmjzYqvXjB9iXgn3V17oRsios_8EMS6Ij-aeVaj7ug7uLlYxAqfLt_ofmeAGhfRgc4UERDY?purpose=fullsize)

<img width="1536" height="1024" alt="1" src="https://github.com/user-attachments/assets/edbe538c-89b9-40f5-91e5-361e3c151734" />


---

# b. Understanding Directory Contents

## 1. /home Directory

### Purpose

The `/home` directory contains personal folders and files of regular users.

### Command Used

```bash id="f8g2qp"
cd /home
ls
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/8D0THXcZLSsUJmb9TZMjh0ssJNoD1iI_HYY6wNemafcb2bQ0xlFVS-PZ-r5S5ZV_ppram7FIxzrDljcjM0NRb3wEPWQs3z_i1ZqfjkdcvmcNC7XEudLzD4mYNK97ZLtIZun-JwH0ZdMEUct1QYIn8LsW37WbVkwJZxbzneMOBC5pfUmAHqyhpD7b0wf19N2E?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/JBKFLhNR99bm7SpmcWrV7BXlf648SyMQMWUZgaUgihYMGfiZxvGEXIW79XJ-HlXnsFODh022DWtsGmf_ZnYLny3Ww5nqL7a703AGnWaYz9ifmydTGJhSQeWi04qWAGZBzZcPYmBdJPdGIsLggeUttaTWxltA8XmdOHeW3SK7LVD2YX9DRb89_XUCVdss8kCW?purpose=fullsize)


## Observation

Each user in Linux has a separate home directory for storing personal files and configurations.

---

## 2. /etc Directory

### Purpose

The `/etc` directory stores system configuration files.

### Command Used

```bash id="m5q1ax"
cd /etc
ls
```

## Common Configuration Files

| File   | Purpose                       |
| ------ | ----------------------------- |
| passwd | User account information      |
| hosts  | Hostname mappings             |
| shadow | Encrypted passwords           |
| apt    | Package manager configuration |

## Screenshot
<img width="1604" height="980" alt="2" src="https://github.com/user-attachments/assets/b0d920b6-eec7-425b-8af3-5d238726cd6a" />


## Observation

The `/etc` directory is critical for Linux system configuration and administration.

---

## 3. /var Directory

### Purpose

The `/var` directory contains variable data such as logs, cache files, and spool files.

### Command Used

```bash id="d1u4vz"
cd /var
ls
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/oloBYDV78IiZcBLHxwdHOp7grN44GMPJO6KvZBnXATOqW9slrbRTiP3J7FrjA79XhZfwzc1Z4lZ4NU4pxbkcie0_OOE-bOFHqhZ2nAWIdc8E2r177NkjpjO1auN617vflQbnZmPWGZQ2QomMXwvhnzWtiRIL36krkWJ8RoF0WcrC4tKShcC5Hfjc-L79_yJW?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/Ru5kcCNiyRRUKnxlYox6gLDSXwkA4zy1BWUVp-8XhQcSX_yOdUdNIhAaG6wWg4wDh8DM3QwnphCQI3cDYFT1gJ56BYJz5itpkLyVJ6DI7jL7ZnOdjYhdlMRZFWlj51r9O-B0rKHW_gcueR6g1a2Z2hfQeQQCi0orfHbubBH1XDJh74yhy6sFF1g2EO4W4OTN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/KlXlJhX9V5KWq8soSlL5p4ZTdOF5mIwRmYVPtzeJYoopghVZL4z7QP2LLG45FY_UpqMabAigFc22VkBee9QmejUALT4Y2wv2kSMcob01W05Hlv5scx2zF_UDi_Xn0W0ePHMI9eZtZbxA5oYDLW2p1niNcLFuFPW4HPiS-ZgofxkV3QY9L8S_o8VGZAuweQ7T?purpose=fullsize)

## Observation

Log files stored in `/var/log` help administrators monitor system activity and troubleshoot issues.

---

## 4. /usr Directory

### Purpose

The `/usr` directory contains user programs, libraries, and executable files.

### Command Used

```bash id="s9r4ln"
cd /usr
ls
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/TnymBRNg_-UN9YyIB9lR46Gm50PbEh-bSehlcLOw2RJLRW5yxVuLbeUq7r6eKBhna2uKizXpk9SieqKJRiosY8YYa2Bqw4vxO9uN6MnaBKvbHtfALTWxQ-Aasp4uCuBx-hqJiqrHLpU-Ka1oXwOgam6eCi_zSPZbml91e50-afVTKNSOojNLIn4WHFijroVX?purpose=fullsize)



![Image](https://images.openai.com/static-rsc-4/T2Kn65s8RixAuLUX0k-yiwznb8Eay-rL7ejLiJt3F7ZZ4iT4HA9s873GfuNyVVReI66uwIEeBRFhmo3yl44F0BrgW9y8-3NiIe324Y7dFF3FzuIQ4anmNEEnSYBFsP_Xc5ZgJVGKYiT5r3E6XS61GaGEoMcfxG1yQbZwhs9el4R0_Q4aE6Y4IKxPQyLcGbgZ?purpose=fullsize)

## Observation

The `/usr/bin` directory contains many executable commands used in Linux systems.

---

## 5. /bin Directory

### Purpose

The `/bin` directory stores essential binary executable files required for system operation.

### Command Used

```bash id="n7e2fc"
cd /bin
ls
```

## Screenshot
<img width="1254" height="1254" alt="image" src="https://github.com/user-attachments/assets/ff53301f-8875-43d3-a201-e63ca0659e1b" />

<img width="1254" height="1155" alt="3" src="https://github.com/user-attachments/assets/e9eb2105-4b32-48fc-aeff-9d0d42d5f30f" />


![Image](https://images.openai.com/static-rsc-4/T2Kn65s8RixAuLUX0k-yiwznb8Eay-rL7ejLiJt3F7ZZ4iT4HA9s873GfuNyVVReI66uwIEeBRFhmo3yl44F0BrgW9y8-3NiIe324Y7dFF3FzuIQ4anmNEEnSYBFsP_Xc5ZgJVGKYiT5r3E6XS61GaGEoMcfxG1yQbZwhs9el4R0_Q4aE6Y4IKxPQyLcGbgZ?purpose=fullsize)

## Observation

Essential Linux commands such as `ls`, `cp`, `mv`, and `cat` are stored in `/bin`.

---

## 6. /sbin Directory

### Purpose

The `/sbin` directory contains system administration commands.

### Command Used

```bash id="u2v5hr"
cd /sbin
ls
```

## Screenshot

<img width="1321" height="771" alt="4" src="https://github.com/user-attachments/assets/5d589252-9b83-4cec-8e40-bc74331dcf9c" /> 


![Image](https://images.openai.com/static-rsc-4/T2Kn65s8RixAuLUX0k-yiwznb8Eay-rL7ejLiJt3F7ZZ4iT4HA9s873GfuNyVVReI66uwIEeBRFhmo3yl44F0BrgW9y8-3NiIe324Y7dFF3FzuIQ4anmNEEnSYBFsP_Xc5ZgJVGKYiT5r3E6XS61GaGEoMcfxG1yQbZwhs9el4R0_Q4aE6Y4IKxPQyLcGbgZ?purpose=fullsize)

## Observation

Commands in `/sbin` are mainly used by the root user for system maintenance.

---

## 7. /tmp Directory

### Purpose

The `/tmp` directory stores temporary files created by applications and processes.

### Command Used

```bash id="r3x8jd"
cd /tmp
ls
```

## Screenshot



![Image](https://images.openai.com/static-rsc-4/hdnRkY5xKFSc7JIO0kke4x_9hJ1pst6HXrwlOzRnTQmfi-5WjGJh9GZMoRn_yiYKi_uNeBGt1sMkRUlIOcXwyPsffnOtrxGbI0P_nAPy2hhmrcXsQa2EakMhH_aABKRM-LIhadw17QL4-gzm-DoT70Z1IIRShs2M9jQxtL-rTwUY0bJj4Gmw-TSsFFeBR_kN?purpose=fullsize)



## Observation

Files inside `/tmp` are temporary and may be deleted automatically after reboot.

---

## 8. /root Directory

### Purpose

The `/root` directory is the home directory of the root (administrator) user.

### Command Used

```bash id="w6k9pm"
sudo cd /root
ls
```

## Screenshot
<img width="1122" height="1402" alt="image" src="https://github.com/user-attachments/assets/6ac09d37-ba48-446f-8e3d-73194ea095e4" />



![Image](https://images.openai.com/static-rsc-4/D7LL61Oio5tr-WqknD_t4QfP1v5ntDEUqQq4YYKGRfjsEWvs05oOCbEg1D8IP_nczW0F12h-0AMdHKgTZHJNv74wFrJBIdxV3J6Sxp2HQcLi4ZalAVyV-Gz1XwZVYEMXQ6Elr4Vxd6a34hqA7Lx0enMRiTkt0E6hI4Hi9qm0VB2l3g81oqLlYHdwmVIRuDfN?purpose=fullsize)



## Observation

Only the root user has full access to the `/root` directory.

---

# 2. Create Custom Directory Structure

## Task Performed

Created a personal cybersecurity lab directory structure.

## Commands Used

```bash id="q5m7zt"
mkdir -p ~/hacking-lab/reconnaissance
mkdir -p ~/hacking-lab/exploitation
mkdir -p ~/hacking-lab/reports
```

---

# Directory Structure

```text id="j2h8yb"
hacking-lab/
├── reconnaissance
├── exploitation
└── reports
```

## Screenshot

<img width="1122" height="1402" alt="image" src="https://github.com/user-attachments/assets/3561fe37-8180-4aab-bcb3-c3d38f205913" />


![Image](https://images.openai.com/static-rsc-4/-WklHk68_sjbmn61HgW77yP-pYat9LEv3fVlEtyjM_CdZLN0RjVvBgK1hCnvS0F8TJTga2D1_HDNwZBQkXrDZAI9zrm6VNrrArK_8jdP2LB8QcyFjJ-_DSFZJmYY70dkmkXNO7AeYCaZf7Rnypa7ykHNia47IDCyzTLxag4uDHIto0kov_VXvAKyiqLqZwEx?purpose=fullsize)

---

# Using Absolute and Relative Paths

## Absolute Path Example

```bash id="e8t4ql"
/home/kali/hacking-lab/reconnaissance
```

## Relative Path Example

```bash id="g7v1sn"
cd ../reports
```

## Observation

Absolute paths specify the complete location from the root directory, while relative paths navigate based on the current location.

---

# 3. File System Scavenger Hunt

---

# a. Find Configuration Files in /etc

## Command Used

```bash id="l3n8vr"
find /etc -name "*.conf"
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/-atiMGA22VLkqM-6NnO3R6HUNjNO0iTvyWTT_eFRVdBcW8-stZV_nlYqrTgyxa_AGv0gHZrKhqXI8OWOKwMa7ghOSpuzgYzLkFsDmNXw7EJ8xuq8J2xKxYAZi5Dd6BKYqr7XRm4n6pRltZRLUuzXgWxaatPQA74Oi8eMB20w1KlNEz77jVnW4GwwYSRUh6RV?purpose=fullsize)


## Find Command Basic

```bash id="l3n8vr"
find -name <file_name>

find -type d -name <file_name>

find <path> -size

find <path> -mtime <-no_of_days>

find <path> -name <file_name> -exec <cmd> {} <arg> \;

find <path> -name <file_name> -ok <cmd> {} <arg> \;

find <path> -name <file_name> -ls

find <path> -name <file_name> -delete
```


## Observation

Many important configuration files are stored in the `/etc` directory.

---

# b. Locate Log Files in /var/log

## Command Used

```bash id="b2f6mk"
cd /var/log
ls
```

## Common Log Files

| Log File | Purpose                   |
| -------- | ------------------------- |
| auth.log | Authentication logs       |
| syslog   | System activity logs      |
| kern.log | Kernel logs               |
| dpkg.log | Package installation logs |

## Screenshot

![Image](https://images.openai.com/static-rsc-4/ELD_zrR5f_hM7oWHet7m0G2oNB3yQKGayyMPuHk5f-FM98wm_xDJwuUqtnuld6HQ1q7qmxR-fPNDXZ1A1E4TIgL4ZpAf8OF5aj8Li_MVjyYA9H4T_gcaVUIMLMv9B-hpSSubYceJ9haGdFdvP0ew-EGhElW6x7MFTcQhJITpHsbX1ViTw2WDqJcVLedM0Lgm?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/whSBHX1_f25IaICQiTsRSwaJwiNM4-LrBfeD62DOVxU9buvvYg5aKFxwHhbOZyinPhFL5azXu2-ddIULWCemkhghsRvB_Ko0F82XgLlBbANA1DcREhz6tNEnBjvg9tKp_U176Fd-AYUrmb2N2SfgCN44WKBoqDWzRLJFcRVDu70qn3Rye3NkCPwhHpdaPoIx?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/4Sn1QVc_B5GsdNYhagHluZDh2xlIAEuNi-OJbwNU2AGT83vvKATIG5aFurLVMskdrWHldOs-dtcOR_i7vtlot3GCqKvkHGbUCBkPKnkc36MUNIhNbRrB9TsHx1pkPKsU3PuRc9Eb7opHZAwS4K5aZr4uTo7KVvRl9R_3-280nYnIfDuEgT6Idnpj1qej3IXI?purpose=fullsize)


![Image](https://images.openai.com/static-rsc-4/Ru5kcCNiyRRUKnxlYox6gLDSXwkA4zy1BWUVp-8XhQcSX_yOdUdNIhAaG6wWg4wDh8DM3QwnphCQI3cDYFT1gJ56BYJz5itpkLyVJ6DI7jL7ZnOdjYhdlMRZFWlj51r9O-B0rKHW_gcueR6g1a2Z2hfQeQQCi0orfHbubBH1XDJh74yhy6sFF1g2EO4W4OTN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/hc7rB-zvqg8Xbii_XNaZQvngQiz7PJhYJmGUPN-x6xBrjuW9YX_DDka2WACiIQrzOVvJgN-vZ2IfOGpqV01UVC1zKLafuoKcO7YPFxdJLrDHh19jlM2-ccmw6YqphDsZXQbaK3FY7p6IwSijilZhByJqlGY7AN2l3y6TV-OfxkSWrj2juKRYS-CgfKBrzd4t?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/YRM0ayH6Adpmos51zLvL_KkTHDCL42UDivWNJkyy-iiBh-TWGjfFqaB-4DaLZAlFC3q3Pl9L3lrjqo2g69JZIP7tUseSUBeDyIKbFApi1LlEH-zBnoOyTuxg_hE5noxxTei98nuHbJPqmXIhwgmBGJf2Cw95J4Wp1-IBfrU3ytflJCJkt0gnlG1q65tqYhet?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/K7WGASAxXPoAbBHE8jxfxJo17r8DbkWqpuxtLD2rHKLMS34V-NbVVMGbIhYcqLV3GR_32rP2GbwHDfT3Sw0gEKOOhe9gVdE1I3ixuDbY7I-81ltxqjQNuNvf05Z3AiyUCC3i39CMSKJJ4frUyRuRvjlO1D33tDbKDSG9RSkE7cDj1qCS85oN0eg7qGLjdkRR?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/fMpngLbkqI1pPZQSu7azYJdRJNW0B1y_KtZrR2l9h9QFZiThW6h5fEdXKY5Y0_ne9gXkqLF6aSJcwwQ5fCQAhAD_tnI83A3CwPbwFX-VHxwxw3m_dwxHdFQ9aj6HnvJC19ybwWmbtCElWvTmGi2IcImTquK8h-VmHBXr__RdfhNGgJcz7VsmJqxEuS1853BF?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/jlnRuUPLvGYn2cLCWF7h1xi-glgj5NUiuUJan3lumE00jkHyX7ukQdmUcMfriIDdzNcsn01S6HQ-wuj4UL6fZ7O0nOa3uY22BrVxIlW6fooHAx7RhN5vdvx2OhmjzYqvXjB9iXgn3V17oRsios_8EMS6Ij-aeVaj7ug7uLlYxAqfLt_ofmeAGhfRgc4UERDY?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/LZt3iSLT2t09krFjzCpCcy4R5fbdi0onKod6iwXG26St92X8f6V_Y3nDoDeobTImdRBFJGMiUVC9HR4lYssNBXKQjT5q8JfPMWMU0UGBatG5Vt-czh4S5LMSMEN9ZfO6CSR9D7ach2qUpHnLiGY1HP336gzy42vuLKgRm5MJsbJ7bQ2VqRZ9Ln97IZcydWS2?purpose=fullsize)



![Image](https://images.openai.com/static-rsc-4/ZoFH2kEHE3MMyi7j9ohkcajojSCSgBiqAZ0yro_uCWKI9EBKE5N8Z9FJfzLDEKtAEfFE2lEXvtR-E9xDkhlPbYQqbwT55rKlp2vbQ5BRerTH0Shy-YqasjkZRaK4lEzsEnsaMQHgDg4U_pRRAMfO8bvBuBVYGDvSq9ei7xCy4obp_7NOmSLP-G39fA5FuAp6?purpose=fullsize)


## Observation

System logs help administrators analyze system events and security incidents.

---

# c. Identify Executable Files in /usr/bin

## Command Used

```bash id="y4w7qa"
cd /usr/bin
ls
```


## Observation

Executable files inside `/usr/bin` provide access to Linux commands and utilities.

---

# d. Find User Bash Configuration File

## Command Used

```bash id="c6r9eu"
ls -la ~/.bashrc
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/IaXtYOhiWh-DGvGdM5mIDhWmoUNFLAjlQqjz1aQ2L1aDoYeZYBvJ7anE-Ctbozd976CJyUnEAa-LunmkCadnVp5yxzxcS0zWKgc1aMygT4PRqSWOpSAO1lfdxmNHyYqsA2NNXIVBpifYdh7dirX2BNflxxYXnWyPk9eWDl3yWl6d-kdH0tHSJvZFlI5s4fPd?purpose=fullsize)




## Observation

The `.bashrc` file stores shell configuration settings and command aliases for the user.

---

# 4. Understanding File Permissions

Linux uses permission sets to control file access.

---

# a. Check Permissions Using ls -la

## Command Used

```bash id="z1p5nx"
ls -la
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/U1eq9Hr8hgqKsYHGLdtJgLZjamr6wYSRSBc2leGZkLZihYr5n2dssX4uCKh8TGzuRatU-z5_w53vRqF7U3UWZ7oblFXrLRu6ZHAaqYVlfFBQiMNSrcCDPifNBVnAeVoMsalxd1vQ5FeXkusg6O1yvh5OHbsIZ6yMiOwolnw_NNjvX_tjduuhBWO5Laj8TmUS?purpose=fullsize)

<img width="1086" height="1448" alt="image" src="https://github.com/user-attachments/assets/ecd78eec-d6f4-437a-a51b-e1836dcc098c" />


---

# b. Understanding rwx Permissions

## Permission Structure

```text id="a7m2lt"
-rwxr-xr--
```

| Symbol | Meaning            |
| ------ | ------------------ |
| r      | Read Permission    |
| w      | Write Permission   |
| x      | Execute Permission |

## Permission Categories

| Category | Description         |
| -------- | ------------------- |
| Owner    | File creator        |
| Group    | Assigned user group |
| Others   | All remaining users |

## Observation

Linux permissions help secure files and restrict unauthorized access.

---

# c. Root vs Regular User Ownership

## Command Used

```bash id="h8s3ku"
ls -l /root
ls -l /home
```

## Screenshot
<img width="1086" height="1448" alt="image" src="https://github.com/user-attachments/assets/fc395787-a8b3-42c0-88f3-1dbe10d1ccce" />


## Observation

Files owned by root require administrative privileges, while regular user files have limited access permissions.

---

# Challenges Faced

| Problem                   | Solution                              |
| ------------------------- | ------------------------------------- |
| Permission denied errors  | Used sudo privileges                  |
| Difficulty locating files | Used find command                     |
| Navigation confusion      | Practiced absolute and relative paths |

---

# Conclusion

In this assignment, the Linux file system hierarchy and directory structure were explored successfully. Important directories such as `/home`, `/etc`, `/var`, `/usr`, `/bin`, `/sbin`, `/tmp`, and `/root` were analyzed to understand their purpose and contents.

Custom directory structures were created, configuration and log files were identified, and Linux file permissions were studied using `ls -la`. This activity improved Linux navigation skills and understanding of system administration concepts used in cybersecurity environments.

---

# Tools and Commands Used

* Kali Linux
* ls
* cd
* mkdir
* find
* sudo
* pwd
* apt
* bash

---

# Author

Sarfaraj Ahamad

