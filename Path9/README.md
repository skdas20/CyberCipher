
## A Basic Overview of Burpsuite functionalities:-
-   **Dashboard**:
    
    -   Provides an overview of your current Burp Suite project.
    -   Displays alerts, activity, and issue progress.
-   **Target**:
    
    -   **Site Map**: Displays all the discovered endpoints and content of the target.
    -   **Scope**: Allows you to define which URLs are in-scope for your testing.
-   **Proxy**:
    
    -   **Intercept**: Intercepts and modifies HTTP/S traffic between your browser and the target.
    -   **HTTP History**: Shows a history of all HTTP/S requests and responses.
-   **Spider**:
    
    -   Automatically crawls the target website to discover content and endpoints.
-   **Scanner**:
    
    -   Automated vulnerability scanner that identifies security issues in the target application.
-   **Intruder**:
    
    -   **Payloads**: Customizes and launches automated attacks with various payloads to test for vulnerabilities like SQL injection, XSS, etc.
    -   **Positions**: Specifies where payloads are injected in the request.
-   **Repeater**:
    
    -   Manually modifies and re-sends HTTP/S requests to observe and analyze responses.
    -   Useful for testing and refining payloads.
-   **Sequencer**:
    
    -   Analyzes the randomness and predictability of tokens like session IDs.
-   **Decoder**:
    
    -   Encodes and decodes data using various formats like Base64, URL encoding, etc.
-   **Comparer**:
    
    -   Compares two pieces of data to highlight differences.
    -   Useful for identifying changes in responses to different inputs.
-   **Extender**:
    
    -   Allows the addition of extensions to enhance Burp Suite's functionality.
    -   Integrates with BApp Store for downloading and managing extensions.
-   **Project Options**:
    
    -   Configures settings specific to the current project, such as logging, sessions, and proxy settings.
-   **User Options**:
    
    -   Configures global settings for Burp Suite, such as display settings, extensions, and miscellaneous preferences.

# Damn Vulnerable Web  Application
- DVWA - A platform to practice Penetration testing
 - [ ] Command  Injection
 - A common separator used for injecting commands can be |(pipe symbol) but it may not work at times and we need to have alternatives to it based on the environment of servers we are dealing with:
 - ### Unix/Linux

1.  **Semicolon (`;`)**
    
    -   Allows you to chain multiple commands.
    -   Example: `command1; command2`
2.  **Double Ampersand (`&&`)**
    
    -   Executes the second command only if the first one succeeds.
    -   Example: `command1 && command2`
3.  **Double Vertical Bar (`||`)**
    
    -   Executes the second command only if the first one fails.
    -   Example: `command1 || command2`
4.  **Backticks (`` ` ``)**
    
    -   Executes the command within backticks and replaces it with its output.
    -   Example: `` `command` ``
5.  **Dollar Sign with Parentheses (`$()`)**
    
    -   Another way to execute a command and replace it with its output.
    -   Example: `$(command)`
6.  **Logical Negation (`!`)**
    
    -   Inverts the exit status of a command.
    -   Example: `!command`
7.  **Subshell (`(command)`)**
    
    -   Runs the command in a subshell.
    -   Example: `(command)`
8.  **Redirection (`>`, `>>`, `<`)**
    
    -   Redirects output to a file or input from a file.
    -   Example: `command > file`

### Windows

1.  **Ampersand (`&`)**
    
    -   Separates commands on a single command line.
    -   Example: `command1 & command2`
2.  **Double Ampersand (`&&`)**
    
    -   Executes the second command only if the first one succeeds.
    -   Example: `command1 && command2`
3.  **Double Pipe (`||`)**
    
    -   Executes the second command only if the first one fails.
    -   Example: `command1 || command2`
4.  **Caret (`^`)**
    
    -   Escapes special characters.
    -   Example: `command1 ^& command2`
5.  **Percent Sign with Parentheses (`%()`)**
    
    -   Executes a command and uses its output in a batch script.
    -   Example: `for /F %i in ('command') do ...`
6.  **Backticks (`` ` ``)**
    
    -   Executes a command within backticks in PowerShell.
    -   Example: `` `command` ``

### Combining Commands

-   **Chaining Multiple Commands**:
    -   Unix/Linux: `command1; command2; command3`
    -   Windows: `command1 & command2 & command3`

### Example Usage in Command Injection

Suppose you have a vulnerable parameter that executes system commands:

-   **Unix/Linux**:
    
    -   Original: `cat file.txt`
    -   Injection: `cat file.txt; ls`
    -   Injection: `cat file.txt && whoami`
-   **Windows**:
    
    -   Original: `type file.txt`
    -   Injection: `type file.txt & dir`
    -   Injection: `type file.txt && whoami`

- In case the Encryption works on the command as well , we need to open the burpsuite and intercept the traffic and then go to repeater which sends requests directly to backend and we can use it for manual testing with ease.
# www.revshells.com -A Website for Payload Generation
- RAT-In cybersecurity, RAT stands for Remote Access Trojan. It's a type of malicious software (malware) that allows attackers to remotely control a victim's computer system without their knowledge or consent.
- A Backdoor-A backdoor is a hidden or unauthorized method for accessing a computer system or network, bypassing normal security measures. It can be used for legitimate purposes by developers but also poses a significant security risk if exploited by attackers to gain unauthorized access.
- A RAT developed by our Mentor-.ps1 file that runs on the RAM and Outdated Antivirus cannot detect it because it will scan the ROM.(A powershell file generally runs on the RAM)
- nmap flag (-A) use for OS detection.
- nc mkfifo- a payload for linux based system
- We inject the command and get a connection back with nc -lvnp

 - [ ] If the website is SQL embedded and the SQL accepts linux commands- It is vulnerable to file inclusion vulnerability.
