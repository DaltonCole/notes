# Clues

## Binary
* Run `strings` on a binary
* If a misconfigured binary is found, check out: "https://gtfobins.github.io"

## Commands
* `sudo -l` to see what commands you are able to run as root

# Exploits

## Path
* If a script takes advantage of a binary, we can use out own binary instead. :) Just alter $PATH so out binary would be looked at first
	* For example, say there a program executes `ls` and has the SUID flag set. We could add write our own `ls` command in "/tmp" with `echo "/bin/bash" > ls` and update the path via `export PATH=/tmp:$PATH`. Then run the original binary. 

# Guides / Check-lists

## Privilege Escalation
* https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Linux%20-%20Privilege%20Escalation.md
* https://sushant747.gitbooks.io/total-oscp-guide/privilege_escalation_-_linux.html
* https://payatu.com/guide-linux-privilege-escalation
* https://github.com/netbiosX/Checklists/blob/master/Linux-Privilege-Escalation.md
