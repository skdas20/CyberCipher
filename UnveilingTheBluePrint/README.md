# msfconsole
- we can type msfconsole in the terminal but to start with the database running type ```msfdb run```
- ```db_nmap 192.168.1.242 -A``` - conducts a general sV sC scan
- ```search konica minolta```(Port 21 was open with konica)
- use 2
- choose a Payload or provide for hosts if autochosen
- ```show targets```
- ```set rhosts 192.168.1.242```
- ```run j```
- ```sessions```
- ```sessions 1```
-  OR directly write ```exploit``` to get into meterpreter
` ```sysinfo```/ pay heed to the architecture and the meterpreter , if both are different then change the meterpreter to the same as Architecture
``` ps```
pick a process of desired architecture and migrate to it
- ``` migrate 8104```
- Use metasploit as per requirements but dont rely on it completely because it may hinder deep learning
# Web App PenTesting
- nmap scan
- wappalyzer for planning attack
- nikto  ``` nikto -h<target> -p<port>```
- directory brute forcing using hydra and enumeration of directories using gobuster
- fastest scanner ```dirb http://target```   
- Dirbuster GUI
- we can use curl command to view the page source
- ```curl -v http://121093029323/images```
- we wont get it bcz we r using http 1.1 , we need to downgrade to 1.0
- use netcat ```nc -v 192.168.1.52.80 \n GET / HTTP/1.0```
- 



















# beef-xss -- client side browser exploitation
#sudo su - switch user
#passwd root - change root password
# Linux File System
- root - for root user
- home - user names
- etc - pass word shadow files
- bin / sbin- binaries
- var - web files
- usr - binaries
# We can also use net cat to scan IPs
- nc -nv -w 1 -z 12.12.1.2 1-1000
- nv for verbosity'
-  w1 timeout to 1 sec
-  z port to scan
# -sT flag of nmap to do a three way handshake with any port (-p 23)
### Under Progress
