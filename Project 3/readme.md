# Linux File System Treasure Hunt

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

![Image](https://images.openai.com/static-rsc-4/ubPTdvJXWJhLUT1X-3kyX670gUgS1JQWxRvtK1lt_y2irTnyPPSo8tmTMTgtnCvB_9Rj5df1GY-a7vj7aY_y9vXg0YE489Ma_clLYqSi65i1H9uz2StwfEQf4kXiYY8kApd12ZDtK33iHuctVRw45Xe7ciwIgSgrfRpvYtAGW6MLUXTUeB--_vxofnu0dnsz?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/VGU44UqbTxnuyESqLKxKW4xfhvsJE7Se0gdYKvcUr4YNUW_ZcBXW_QIrEeYlKIahPXg3-BFfez07W2trWLAwrwZdG038FST_2y0JOk2KoMvdqgh34lbvQSQqo_WUtaAiNCy9_liMEinNgrJc-CadaAzog0GMeMsBWIUZevClbpq2MpLFhfOArNmiP1DqlmiO?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ozVCpDO46-QvzqYf2Z-HRU9MhqMhPSXrGbo4tPFbhif4W631kLi-BlSNWJByQtycArYFHk4hXli8uQWjfyJysJuAKF9I73XAVMGFmfcxaVkGYtHkYO6pwLz9nDCoQdQKkMrmTIo5Rngw-74elAUPCz03TnrCsTy5tw_Q1VmIDPNeBC7UdjbXFVL7L9oJs1wy?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/_HxOdo9f7AYkh3jVEMIyhJW1S9U7yXgOhVLmsj2nHE-pDLKh5XJCmp7GEdn7dn44s2WqydJtG5dYuH9rCOhQSTEz-GzGTWPg3cHpYU1liskgxvvmxLsPeEHIrikLzBN77KwY-GHAdcy71K9OgrAH6-tSc1Ed6NhPzy-OcJlu9LPINYNw7S8FZoXUVzCHYxEs?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/lUdfH16oHVCLwBltpGMMU7-CR1HsFmwq3TGvdqT9AXQb6qP5fidjXIGMIrN728m03KgpKtCnTBGq-Gkz6VTlT_02o9TIbfPLXqI0r6gTpzzfaXnAyRE_AX25Wzaznm7bde9_z6mQy2FEuzD-7eXkhPDPlArarboFcqLGL0sb6gRfvYJoqCWgAgPVoxLiThsh?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/oLZXoPRisVHnlYrXfkNEWl6h8VJDCN6xGsDqGHQ0uVXQafctLfP8LT2syVzKWkUT3TiWVRUmSje1yWP3vjGy9Jm61jCF8EzOnraFlNuUQp-CEZh7jJkgdMzKlKUjcdmJxjWGwNCMOTfl439hLVTX0VimiBw4l3g5co8iwYOiHGFCJMZMD3s0n4l0yGhcV-AO?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/zyyXlbA5fPDmgBQdu-UE2LHFTB5qxNNI4a4rqheAOcUQyx3R4VOQ6FldGqNyaiBElnIdEM12PztrU3MMPYjxboAs7njMNoMsQmYFMjHwlcAsvFAHsdaf58KsihWwoF4KTW6Dm4nADiTFyKYDrLnq0gzf3oICT9lglt9CTOWjbHP5BZTBqgEOAdUwcUkTjk3k?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/Tz6QcuJ0qf7b40qLtElTUGM9B3xQ57kpoOk9NsfcNXGSVNoQfwHfkKcj5oCgOFeJqk20JP810IAvRy-ZTd5hIrTWUjM3qsed7UJo2G1VaCb4ZKJ3XSxEKAO6G1cbbAtRcvPlnzJBjPiM9NA2cuND_KZYWO7msuBrOOVbfG7WK0eOILQfo9k_jhhsDa86HuXk?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/qHIy2HhFlHtn_W2NBCNAiFgN717kOqaWeLjJ6DNvyqsOW1CAYYnKtXDIP_MWAv4NwwFShU_Ivs1H37eCv9nA98BCRE9ejLHftkJHuwnDRStP3mFmTnjriHCUIqrv5keBTh--WL3CtsB_PPYJylSndhSvTkE_-y1qg_C436GQLwW_hnT_xZzREp4LUpNO0H1I?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/hdnRkY5xKFSc7JIO0kke4x_9hJ1pst6HXrwlOzRnTQmfi-5WjGJh9GZMoRn_yiYKi_uNeBGt1sMkRUlIOcXwyPsffnOtrxGbI0P_nAPy2hhmrcXsQa2EakMhH_aABKRM-LIhadw17QL4-gzm-DoT70Z1IIRShs2M9jQxtL-rTwUY0bJj4Gmw-TSsFFeBR_kN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/qHIy2HhFlHtn_W2NBCNAiFgN717kOqaWeLjJ6DNvyqsOW1CAYYnKtXDIP_MWAv4NwwFShU_Ivs1H37eCv9nA98BCRE9ejLHftkJHuwnDRStP3mFmTnjriHCUIqrv5keBTh--WL3CtsB_PPYJylSndhSvTkE_-y1qg_C436GQLwW_hnT_xZzREp4LUpNO0H1I?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/RKwWGdWeNkCJkxpoL5Mp4kgVRPPJfYy8x5gMqP0gaxgZx-pBD_SoH3_4vREF5EZ2xS-Mt18JLksybU1HI_RKAC-CHIN0FIJPbj232UdcjBWW--3qhTrCRBpX0YwQtloMEeiIEByKAPidLHJW8S3bw0rkrG6fFp4tLwqP0-GHfFgf41JRT1HJPAnxIWapOIOS?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/D7LL61Oio5tr-WqknD_t4QfP1v5ntDEUqQq4YYKGRfjsEWvs05oOCbEg1D8IP_nczW0F12h-0AMdHKgTZHJNv74wFrJBIdxV3J6Sxp2HQcLi4ZalAVyV-Gz1XwZVYEMXQ6Elr4Vxd6a34hqA7Lx0enMRiTkt0E6hI4Hi9qm0VB2l3g81oqLlYHdwmVIRuDfN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/JdSpF1qDd4Q249TTTITbj-lwqaSMxF2zgzC17d27H1jRbw7IXu8gHSbouYaK-aFUjvQ-qTMa29cdYHAzS-pIISOMaS_sQPncv_fM5aoNcAw2RxUDbSNNqAM-Lvpm-KFcaI5AVD_GytgsA5GYXM46yD4M5smecoR-KQOhLqqRuBtt7FEGsnQBduQw1FPuxvQD?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/rWw2sZAgHWJnhY0ham0OEsH6q-j2s2oIfto3xbhV5gD372iUjOT6-vanD37Y1KrDomM-7BTzvtIsMK3cPRyCDQkpW9H6Yw3bVKp83tLj8J4BBevC2oQbhe-J9Vfo3RWdaWyQXNVpAGno3rQiDGPht3-y_KWuoE8u9YKCX9smN31F4kasxNED1VQR1QKMaPO0?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/_Ox0DDh_acAfmKwqRr-fZmUHB64C0Q7XnrRpk9jO1JclT8LaBx60YedbTXjQqsSGlQIvPaBuC72weJf3RiU3d2dDHXIvtfmiYFPJ-Kh6qpr-Jyv7vAqEoD8GlybyMj-RmwW08udrKX_SahSBoRsOp_6scr_Mk5BMPtaHus7-2fS1F8dCXCcD5m67ufSui_63?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/VGU44UqbTxnuyESqLKxKW4xfhvsJE7Se0gdYKvcUr4YNUW_ZcBXW_QIrEeYlKIahPXg3-BFfez07W2trWLAwrwZdG038FST_2y0JOk2KoMvdqgh34lbvQSQqo_WUtaAiNCy9_liMEinNgrJc-CadaAzog0GMeMsBWIUZevClbpq2MpLFhfOArNmiP1DqlmiO?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/oyKbx65StybXkhkHk_ZAg6GWYLnrP5xt3NimcKxC5QXiIGoHbLpQIiAjZwUYyp-kdphL-evJMl1NlN932IHrdkdpkxKE_Jdj5aSMoUoPKjlePGqdcFDNSFJyUZUWPJrUGTji6NKomRpT1EkakBNOXhuN2F47XbqAPlbwe4_hUC5kMjarDFXrTtNaWGeDIPAD?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/lG8bqr6YmUJlEJliUoOx6oB4zrXMbojpg08uPWs0oVELKykwu6T-zWHbs3l2yBjZEgSmzSRUSdFU3DEDTfykpFvVGf7_s9_884T93jhozSTqbEhY8ffZtga9Fd9BwPIAuihXkdcH9fCQqTgu391CJqrVLiC6DKTZKp3rLAIy0lk7M-p2MOh-LNiFMJiD98f7?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/NJsBNQs0RBnMjqSB7bn09AYGIjvtu0gsfXS0k9axXwf9TtYBuGSxfUPejufGnYoUU9lojNTrY8fS_2w0GS4WNLdOp6R8CnM8aMwlE0uKr5rh7cT8rtTp9a7oEVOoGi6YZasO2OLbtbMJNqxxvlcCiBVRNr3XTBi9dWC3up-AjHyWU8Qmh6AYyfty9qKpIO4O?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/5LFgndkH7Eeli_JS5QpEo5JLiz7FHOIBEjempo-1H-prV1eKkUiv6KJriT5tQqtY1os2LqCGLm7r_Y-kneslTM_X9EDwTk0yvTsm6gpq8GtQFE1KKV5td2OWyQmcAbJh6nGbo5gDyjS5jRVh94GiItmSDtDrqyBoBloc95iVlkea3-6OgC2DASiFq-0eRrkV?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/Ru5kcCNiyRRUKnxlYox6gLDSXwkA4zy1BWUVp-8XhQcSX_yOdUdNIhAaG6wWg4wDh8DM3QwnphCQI3cDYFT1gJ56BYJz5itpkLyVJ6DI7jL7ZnOdjYhdlMRZFWlj51r9O-B0rKHW_gcueR6g1a2Z2hfQeQQCi0orfHbubBH1XDJh74yhy6sFF1g2EO4W4OTN?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/hc7rB-zvqg8Xbii_XNaZQvngQiz7PJhYJmGUPN-x6xBrjuW9YX_DDka2WACiIQrzOVvJgN-vZ2IfOGpqV01UVC1zKLafuoKcO7YPFxdJLrDHh19jlM2-ccmw6YqphDsZXQbaK3FY7p6IwSijilZhByJqlGY7AN2l3y6TV-OfxkSWrj2juKRYS-CgfKBrzd4t?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/YRM0ayH6Adpmos51zLvL_KkTHDCL42UDivWNJkyy-iiBh-TWGjfFqaB-4DaLZAlFC3q3Pl9L3lrjqo2g69JZIP7tUseSUBeDyIKbFApi1LlEH-zBnoOyTuxg_hE5noxxTei98nuHbJPqmXIhwgmBGJf2Cw95J4Wp1-IBfrU3ytflJCJkt0gnlG1q65tqYhet?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/K7WGASAxXPoAbBHE8jxfxJo17r8DbkWqpuxtLD2rHKLMS34V-NbVVMGbIhYcqLV3GR_32rP2GbwHDfT3Sw0gEKOOhe9gVdE1I3ixuDbY7I-81ltxqjQNuNvf05Z3AiyUCC3i39CMSKJJ4frUyRuRvjlO1D33tDbKDSG9RSkE7cDj1qCS85oN0eg7qGLjdkRR?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/fMpngLbkqI1pPZQSu7azYJdRJNW0B1y_KtZrR2l9h9QFZiThW6h5fEdXKY5Y0_ne9gXkqLF6aSJcwwQ5fCQAhAD_tnI83A3CwPbwFX-VHxwxw3m_dwxHdFQ9aj6HnvJC19ybwWmbtCElWvTmGi2IcImTquK8h-VmHBXr__RdfhNGgJcz7VsmJqxEuS1853BF?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/jlnRuUPLvGYn2cLCWF7h1xi-glgj5NUiuUJan3lumE00jkHyX7ukQdmUcMfriIDdzNcsn01S6HQ-wuj4UL6fZ7O0nOa3uY22BrVxIlW6fooHAx7RhN5vdvx2OhmjzYqvXjB9iXgn3V17oRsios_8EMS6Ij-aeVaj7ug7uLlYxAqfLt_ofmeAGhfRgc4UERDY?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/7_lWjyvnE38moKuV7Ni3E6d-SUi4HDktvTkmXDOAWR-hlsqLc8pYjySO1-ugB0IjV0lXUhiiqWw68OaDhX_XyBNvlqJo36tG8OXRp_eMRk6kDa_V-4Gf2VwLHewvPS_IvrE-kj1lUr9lRA2CR-ciNZBRa8i7HTyAH8goydXRZmjpK8KdP7sHfPVkJlcb0nEO?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/LZt3iSLT2t09krFjzCpCcy4R5fbdi0onKod6iwXG26St92X8f6V_Y3nDoDeobTImdRBFJGMiUVC9HR4lYssNBXKQjT5q8JfPMWMU0UGBatG5Vt-czh4S5LMSMEN9ZfO6CSR9D7ach2qUpHnLiGY1HP336gzy42vuLKgRm5MJsbJ7bQ2VqRZ9Ln97IZcydWS2?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/C8pmwRre5n0Vs4n9Mr8AaiBarlsSKTwQa6xHaZwnP5iFe60WeI-OHA3U198E-1c48ACpRieCBbNCkq6sSQ_xKDhYfHn1UHcIhPxNWSiTH8bXVFzEd3X3pyhU7Cb3so0KrKTJLYVfhbMwQpxdbJOYMoEv5W14b16Y3vSDMNWF99zNS8Dqa-uCJMydjtedDfDt?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/ZoFH2kEHE3MMyi7j9ohkcajojSCSgBiqAZ0yro_uCWKI9EBKE5N8Z9FJfzLDEKtAEfFE2lEXvtR-E9xDkhlPbYQqbwT55rKlp2vbQ5BRerTH0Shy-YqasjkZRaK4lEzsEnsaMQHgDg4U_pRRAMfO8bvBuBVYGDvSq9ei7xCy4obp_7NOmSLP-G39fA5FuAp6?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/eKeAUfaHG0BAMwyJ9jFulIo9dUz4Yqcv0hUcqtMF4-DYyyyZD5Ji6PZRYZo2n70B6aIB_XgyO6AQX3j5Mj-GTko0V9-s0KHYmYEUG3TO8VFBX0m9aiGmtAWBBqkT1cb4tEH_GluZQxHNcfihhh4ydLpekRk2te2DkxDq_z1hLiOWUhBeB-_8WN36JdaWQ3pc?purpose=fullsize)

## Observation

System logs help administrators analyze system events and security incidents.

---

# c. Identify Executable Files in /usr/bin

## Command Used

```bash id="y4w7qa"
cd /usr/bin
ls
```

## Screenshot

![Image](https://images.openai.com/static-rsc-4/_HxOdo9f7AYkh3jVEMIyhJW1S9U7yXgOhVLmsj2nHE-pDLKh5XJCmp7GEdn7dn44s2WqydJtG5dYuH9rCOhQSTEz-GzGTWPg3cHpYU1liskgxvvmxLsPeEHIrikLzBN77KwY-GHAdcy71K9OgrAH6-tSc1Ed6NhPzy-OcJlu9LPINYNw7S8FZoXUVzCHYxEs?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/jNt6jDOwhs2qQNdjvu4N2QbVSoWqnSiGkptr8GYoevv3kmoRNev8hL8KL5xZ42XN8JxahPDafZNLS2Lvsjzb_pYbTUMtHFr3YvnBHJW-IglNM1OwyGPzLbuK9GyAed6llQdx-FIgWshlg6RcXiNpV1Uv1hTIWQS6ktSV8RjoMsBoT0BSfR3p44fmrZGL6BEY?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/BzRO8FJ7XnVacyjLhD6AnIZeNzdH_6As3yxNiGq4rPVzQ9O-auZ21JoA8j2OzahtqeGpm8a6ZxuBJY8XLHf0beOhbM0Q0q_aKZUBgNTF1b1RZdBTg9OUpwR8zL61wTmysv5ffnHdPvdnJhxalJdYBQVZqF9cUPHIB4lYst5sE4dEVkOkC9UrafS7AgiGtFUG?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/OhUs_n8mz2TX5PnVP4O_mtRG_ptr4P0kPI2ct-p0WvxKQD6ltamDp3jr7YJFVQc0CxOcsqcYFbItbl2cV9b6_jXSjtiQkqzyk8nmTXlo66x_VJVvaM4pGak_F08LcIzi3NeVLQvYf81qk08URA7luu4plAyEtGkW1nOxLklb3emHcAiMoNCWoJu6MONIu_zJ?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/wgbv2ehNPqcnyqW-qVH_n2iV-g8JuCCOOZ9cKU2-p0MSUmkbBehJlXe_9hWnorlJuCC34qTDFr8rx5FbNLEyQHdcMWvjrBxARFHd8yC8JVal4bxGthjJI7J3rY7bymhyXsnE0rNPM4bZBuodX7UbvBaPXu6m_DDyXY4ucQNT8OUoC7JimHRVT1ofoVGHBH1w?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/wBkdbLlZnyIiuc986ZbgECZTXreB5vlvlz2N2BfFNATNXysna27wYHGSyDhtl1yg1DjlhpKqKIhHGqxSuA7bSTm8LkhNFPTMxCFq1N3Ex2DTsmgZEBvVC0DGtLuU16ftTob7azPiLgM6BSjQNLoE4YhfwfGno3KOGxCh55G9X48tMJnDa0PfNbAeir2JcnkW?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/iHYXxQ3qouokwcRzDD8Hysekhg74z11KWa6dJjxktKS9A6tlFiorkquNoSed1XObj8YlX11I-QqtfRgMui6cOG5ENvNgQwCz7u1jru90rMTjDtZHWVfZg-lTHuUuFov_6CmbQEXOglA1WO67LQG_CdtWxlLb_2edTICuCd79mH0FCn_bRL278xD8UoHR9fCA?purpose=fullsize)

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

![Image](https://images.openai.com/static-rsc-4/n9L9G4mmCk259gO-P6NyWx6rJv87WveX0xEmf2_CDuIIiEYVKWPCQeAt9Kj66fD0IAGm5ffy7uHIPoEGTyPoCxyFeyrU7mSyCG5BOkbmbr8srDMSGAAZV80_OplBpHNevvn_1rdzPgBBYTPzobovu9bAYTMP3STmRQEo0lCC5ujqvLgq46-pQ8ZVJJMingA-?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/i3uiN9jvIqMhTcHEyZBln5aX73wBicptiaR6gyPQa5SmrGb09riIm1tVU_5fZknR24vkZ4Tsiqs2rCVB2lJmcfAf0oEppkLWmfqlblXftI5XEixwNBxENhsI4mo4XUkDIWUmUBxMxoVaea4MRO4HZyXZIi6z0cikHbPQEJ_gdWXjG6UOBKBAfTKT6SLIUEjz?purpose=fullsize)

![Image](https://images.openai.com/static-rsc-4/wBkdbLlZnyIiuc986ZbgECZTXreB5vlvlz2N2BfFNATNXysna27wYHGSyDhtl1yg1DjlhpKqKIhHGqxSuA7bSTm8LkhNFPTMxCFq1N3Ex2DTsmgZEBvVC0DGtLuU16ftTob7azPiLgM6BSjQNLoE4YhfwfGno3KOGxCh55G9X48tMJnDa0PfNbAeir2JcnkW?purpose=fullsize)

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

Affan Malik

