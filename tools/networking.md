# DNS
* When making a request, the first place your computer will look for information at is the local cache
	* If the local cache fails, then it will make a request to the recursive DNS server, which is known by the router, and is usually set up by the ISP provider
	* If the recursive DNS server comes up dry, then a request is made to the root name DNS server. There are 13 of these in the world. They keep track of the DNS servers of the world.
	* The request then goes to the Top-Level Domain (TLD) server with the correct extension (ex ".com")
	* The request then goes to a Authoritative name server, which stores the DNS records directly
* `dig` is a helpful tool to query DNS servers. Example: `dig daltoncole.com @8.8.8.8`

# IP Addresses

## IPv4
* There are 5 IP address classes:
	* Class A: 1-127
	* Class B: 128-191
	* Class C: 192-223
	* Class D: 224-239
	* Class E: 240-255
* Private IP Address Space
	* Class A: 10.0.0.0
	* Class B: 172.16.0.0 to 172.31.255.255
	* Class C: 192.168.0.0 to 192.168.255.255


# OSI Model
The OSI (Open Systems Interconnection) model is a standardised model behind computer networking. It's a way to compartmentalize each step in the networking process.
* Consists of 7 layers: Application -> Presentation -> Session -> Transport -> Network -> Data Link -> Physical

## Overview
7. Application
	* Data flows to and from an application
6. Presentation
	* Translates application data into a standardized format. 
	* Handles encryption, compression, and other necessary transformations
5. Session
	* Checks to see if a session can be started on the network. It then maintains this connection.
	* Must synchronise communications with the remote computer
4. Transport
	* Determines how the data is transmitted
	* Two most common protocols: TCP (Transmission Control Protocol) and UDP (User Datagram Protocol)
		* TCP
			* Connection-Based: Connection is established and maintained
			* Reliable transmission
			* Lost data is re-sent
			* Segments: what packets are called
		* UDP
			* Data is essentially "thrown" at the receiving computer
			* If data is lost, then it is not re-sent
			* Datagram: what packets are called
3. Network
	* Locates the destination of your request
	* Finds the best route to take
	* IP address layer (logical addressing)
	* Last software controlled layer
	* Data is called a "Packet"
2. Data Link
	* Focuses on the physical addressing of the transmission
	* Adds the physical (MAC) address to the packet
	* MAC addresses are hardware specific and cannot be changed (can be spoofed)
		* The MAC address identifies where to send the data
	* Makes sure that the data is in a suitable format for transmission
	* Makes sure that received transmissions are not corrupted
	* Data is called a "Frame"
	* Unlike all previous layers, this layer adds a "Trailer" in addition to a "Header" at the tail of the data
1. Physical
	* Electrical pulse layer
	* Converts binary into a signal and vise-versa

# SMB
* SMB (Server Message Block) protocol is used to share access to files, printers, and other resources on a network.
* Microsoft Windows has included client and server SMB protocol support since Windows 95.
	* Samba is a server that supports the SMB protocol for UNIX systems
* SMB is a response-request protocol

## Commands
* `enum4linux` is a tool to enumerate SMB shares on windows and linux systems
	* Syntax: `enum4linux <flags> <IP>`
	* Flags:
		* `-U`: Get userlist
        * `-M`: Get machine list
        * `-N`: Get namelist dump (different from `-U` and `-M`)
        * `-S`: Get sharelist
        * `-P`: Get password policy information
        * `-G`: Get group and member list
        * `-A`: All of the above
* `smbclient`: Allows you to connect to a SMB server
	* Syntax: `symbclient //<IP>/<SHARE>`
	* Flags:
		* `-U`: Username
        * `-P`: Port
	* Some SMB servers may be poorly set up and allow "Anonymous" as the username. This means that authentication is not required to view the files
	* Some useful SMB commands:
		* `more <file>`: Same as more/less
		* `get <remote> <local>`: Get remote file
		* `help`/`?`: Print possible commands

# Web

## Cookies
* Cookies have four parts: a name, a value, an expiration date, and a path
	* The path determines with what requests the cookie will be sent with

## Curl
* A Linux command
* By default, sends a GET request
* Different requests can be sent via the `-X` flag, for example `curl SITE -X POST`
* `--data` can be used to supply data

## Requests
* There are 9 different HTTP verbs (similar to REST)
	* Get: Retrieve data
    * Head
    * Post: Send data
    * Put
    * Delete
    * Connect
    * Options
    * Trace
    * Patch

## Responses

### Status Codes
* 100-199: Information
* 200-299: Success (200 OK = "normal" response for a get)
* 300-399: Redirects
* 400-499: Client errors
* 500-599: Server errors
