# Overview
* Nmap is used to scan the ports of a target host. This can reveal lots of information, such as the target's OS, what they are running, along with the version of what they are running.

# Commands

## Output
* `-oA <file>`: Saves output in all three file types, XML, script kiddie, and grepable
* `-oG <file>`: Saves output in a grepable format
* `-oS <file>`: Saves output in a script kiddie format
* `-oX <file>`: Saves output as an XML file

* `-v`: Verbose. Some output is nice to see the progress.
	* `-vv`: Very verbose

## Scans
* `-A`: Aggressive scan. Enable OS detection, version detection, script scanning, and traceroute
	* Same as: `-O -sV -sC --traceroute` (same order as above bullet)
* `-O`: Operating system detection
* `-p <ports,>`: Specify ports to scan
	* `-p-`: Scan every portA
* `-Pn`: Treat each host as active. Skip host discovery.
* `-sS`: TCP SYN scan (stealth scan)
    * Quick scan
	* Does not complete the TCP connection
* `-sT`: TCP connect scan
* `-sU`: UDP scan
* `-sV`: Service version scan

## Scripts
* To use a script: `--script <script name>`
* `vuln`: Check for known vulnerabilities

## Timing
* `-T<N>`: How aggressively (quickly) to scan. <N> ranges from 0 to 5
	* `0`: Paranoid. Waits 5 minutes between each probe.
	* `1`: Sneaky. Waits 15 seconds between probes.
	* `2`: Polite. Waits 0.4 seconds between probes.
	* `3`: Normal. Default. Includes parallelization.
	* `4`: Aggressive
	* `5`: Insane
	* 1 and 2 are useful to avoid IDS alerts
