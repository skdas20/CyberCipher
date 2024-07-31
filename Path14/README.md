# Privilege Escalation
-```sudo visudo```(Special Editor for sudo)
- Move to the User Privilege specifications
- below root add ``` kali ALL=(ALL) NOPASSWORD: /bin/ftp```
- Move to gtfobins.github.io and search for ftp and use the command to escalate Privilege 
- ``` sudo ftp    !/bin/bash```
- We can use nano and mv also to perform a similar privilege escalation 
 ## Using Sudo for privilege Escalation
```bash
TF = $(mktemp)
echo "sumit' >$TF
sudo mv $TF /etc/name.txt
```
## /etc/passwd significance
```cat /etc/passwd |grep bash```
- and we can find out the username and then use a ssh attack with hydra to login
## /etc/shadow 
- ```cat /etc/shadow```
- and we can see the hash value of our password
## htop
```sudo apt-get install htop -y```
- The utility tells us about every execution taking place in machine
## netstat
- 0.0.0.0 -- Accepting any IP for connection
- ```netstat -tuln```
##ss command
-```ss```
- used to check if we have any incoming connection
### Sockets
Sockets are endpoints for communication between two machines over a network. They enable data exchange between devices, typically in client-server architecture.

## lsof
```sudo lsof``` //used to see all the connection 

```sudo lsof -i -P -n | grep LISTEN```//used to see any listening connection
The command `sudo lsof -i -P -n | grep LISTEN` is used to display information about the network sockets that are currently in a listening state on your system. Let's break it down:

-   **sudo**: Runs the command with superuser (root) privileges, which is often necessary to view all network connections.
    
-   **lsof**: Stands for 'list open files'. It is a command used to display information about files that are currently open by processes. In Unix-like systems, everything is a file, including network connections.
    
-   **-i**: Option to list files related to network connections. It can be refined further with specific protocols or port numbers, but here it’s used generally for all network interfaces.
    
-   **-P**: Tells `lsof` to display port numbers instead of port names. Without this, `lsof` would display port names (e.g., 'http' instead of '80').
    
-   **-n**: Prevents `lsof` from attempting to resolve hostnames from IP addresses, which speeds up the command.

-   **| grep LISTEN**: Filters the output to show only lines containing the word 'LISTEN', which indicates that the socket is in a listening state, meaning it is waiting for incoming connections.


 Assetfinder
 **Assetfinder** is a tool designed for subdomain discovery. It helps security researchers and penetration testers to find subdomains for a given domain. Here are the key points about Assetfinder:

#### Key Features

1.  **Subdomain Discovery**: Assetfinder is primarily used to find subdomains of a given domain.
2.  **Multiple Data Sources**: It aggregates data from various sources, providing a comprehensive list of subdomains.
3.  **Speed**: It is designed to be fast and efficient, making it suitable for quick reconnaissance.

#### Installation

You can install Assetfinder using Go, as it is written in the Go programming language.

1.  **Install Go**: If you don't have Go installed, you need to install it first. You can download it from [the official Go website](https://golang.org/dl/).
    
2.  **Set up Go Environment**: Set the Go environment variables if not already set.
    
    bash
    
    Copy code
    
    `export GOPATH=$HOME/go
    export PATH=$PATH:$GOPATH/bin` 
    
3.  **Install Assetfinder**:
    
    bash
    
    Copy code
    
    `go install github.com/tomnomnom/assetfinder@latest` 
    

#### Usage

Basic usage of Assetfinder is straightforward. Here are some common commands:

1.  **Find Subdomains**: To find subdomains for a given domain:
    
    bash
    
    Copy code
    
    `assetfinder example.com` 
    
2.  **Exclude Subdomains**: To exclude certain subdomains, use the `-subs-only` flag:
    
    bash
    
    Copy code
    
    `assetfinder --subs-only example.com` 
    
3.  **Save Output to File**: To save the output to a file, you can redirect the output:
    
    bash
    
    Copy code
    
    `assetfinder example.com > subdomains.txt` 
    

#### Example Commands

1.  **Basic Subdomain Search**:
    
    bash
    
    Copy code
    
    `assetfinder example.com` 
    
    This command searches for subdomains of `example.com`.
    
2.  **Subdomain Search with Only Subdomains**:
    
    bash
    
    Copy code
    
    `assetfinder --subs-only example.com` 
    
    This command outputs only the subdomains, excluding the main domain itself.
    
3.  **Subdomain Search and Save to File**:
    
    bash
    
    Copy code
    
    `assetfinder example.com > subdomains.txt` 
    
    This command saves the list of found subdomains to `subdomains.txt`.
    

#### Best Practices

-   **Combine with Other Tools**: Assetfinder is often used in combination with other tools like `amass`, `sublist3r`, and `subfinder` for comprehensive subdomain enumeration.
-   **Automate Workflow**: Integrate Assetfinder into automated reconnaissance scripts to streamline the information-gathering process.
-   **Verify Results**: Always verify the discovered subdomains, as the tool might generate false positives or miss some subdomains.

#### Troubleshooting

-   **Installation Issues**: Ensure Go is correctly installed and configured in your system.
-   **Empty Output**: If no subdomains are found, verify that the domain is correct and that you have an active internet connection.

### Conclusion

Assetfinder is a powerful tool for subdomain enumeration, providing quick and comprehensive results. By integrating it into your reconnaissance process, you can effectively identify subdomains and enhance your security assessments.
