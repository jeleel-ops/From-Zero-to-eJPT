# Day 07 - VSFTPD v2.3.4 Backdoor RCE | Port 21

## Objective
Exploit VSFTPD 2.3.4 backdoor to get root shell on Metasploitable 2.

## Discovery

```bash
nmap -sV -p 21 192.168.56.101
# 21/tcp open  ftp  vsftpd 2.3.4