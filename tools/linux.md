# Commands

## Cron
* `contab -l`: List user cron jobs

## Ping
* Sends ICMP ECHO_REQUEST to network hosts
* Checks to see if a network can be reached

## scp
* OpenSSH secure file copy (like ftp)
* Copy a file from remote to local: `scp USER@IP:/remote/path /local/path`

## Sudo
* `sudo -l`: View what sudo rights the current user has

## Traceroute
* Traces the route from your device to the destination device

## Whois
* Get DNS information for a website

# Files

## Etc
* `crontab`: View system-wide crontab
	* Cron is the name of the tool, crontab is the list of jobs, and cron jobs are the actual jobs
	* Format: # = ID, m = minute, h = hour, dom = day of the month, mon = month, dow = day of the week, user = what user the command will run as, command = command
* `group`: Shows groups
	* See who is in the root group: `root:x:0:USERS`
* `passwd`: All of the users are stored here. Basic information about each user is here.
	* Format: `Username:password:UserID:GroupID:UserIDInfo:HomeDir:Command/shell`
		* Each field is separated by a ':'
		* Password is generally x, meaning encrypted and stored in "/etc/shadow"
		* Each user has a unique UID. 0 is reserved for root. 1-99 are reserved for other predefined accounts. 100-999 are reserved by system for administrative and system accounts/groups. 1000+ are for normal users.
		* GID is the primary group ID. Stored in "/etc/group"
		* User ID Info is a comment field that contains general user information
		* Home directory is the directory entered when logging in. If this directory does not exist, "/" becomes the default
		* The command/shell is the absolute path to a command to run. Does not have to be a shell
	* Attack:
		* If we have write access to the file, then we can add a new root user.
			* To create a password hash use:
				* `openssl passwd -1 -salt <SALT> <PASSWORD>`
			* Example to add to "etc/passwd"
				* `new:$1$new$p7ptkEKU1HnaHpRtzNizS1:0:0:root:/root:/bin/bash`
* `shadow`: Where passwords are stored. They are salted and hashed.
* `shells`: Available shells (like bash)
