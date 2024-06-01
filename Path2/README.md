
# Basics of Networking and Service Commands

Functioning for browser


search bar entry ---> DNS server(Name to IP)---->connection between user IP and Web server IP.

# Port Number 

port number is a unique Identifier for a particular service  on a server with a given IP

HTTP: Port 80 (default for web traffic)
HTTPS: Port 443 (default for secure web traffic)
FTP: Port 21
SMTP: Port 25 (email)


# Internet protocols 


udp- calls, broadcasting,etc.

tcp- email,browsing

icmp-error reporting

# Local host

Its basically our own computer used for testing purpose

For IPv4(32 bits), localhost is represented by the IP address 127.0.0.1.
For IPv6(128 bits), it is ::1.

# Running Secure Shell Service 

```bash
sudo apt-get install openssh-server

sudo systemctl start ssh.service

sudo journalctl -u ssh.service -f
```

sudo: This is a command used in Unix-like operating systems to run programs with the security privileges of another user, typically the superuser or root.
journalctl: This command is used to query and display messages from the systemd journal, which is a centralized logging system.
-u ssh.service: This option filters the output to only show logs related to the "ssh.service" unit, which represents the SSH service.
-f: This option follows the journal in real-time, so you'll see new log entries as they are added.
## IPs and HTTP messages

[Service ports](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers#Table_legend)

[HTTP](https://www.w3schools.com/tags/ref_httpmessages.asp)

[File Permits](https://www.warp.dev/terminus/linux-file-permissions-explained)
