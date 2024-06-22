# Nmap OSINT Recon IDs and IPs
Nmap (Network Mapper) is a versatile and powerful tool widely used in network security for reconnaissance and security auditing. It helps in OSINT (Open Source Intelligence) by identifying hosts, services, operating systems, and potential vulnerabilities on a network based on IP addresses and domain names. Nmap can scan large networks, provide detailed information about active devices, and assess the security posture of a target by revealing open ports, running services, and even the specific versions of those services.


Nmap
Nmap (Network Mapper) is a powerful open-source tool used for network discovery and security auditing. It helps in discovering hosts and services on a computer network, providing detailed information about active devices, open ports, running services, and potential vulnerabilities. Nmap is widely used by network administrators, security professionals, and ethical hackers for mapping network layouts and assessing security.

Recon
Reconnaissance involves gathering information about a target network or system. This is the first step in ethical hacking and security assessments, aiming to collect as much data as possible to identify potential vulnerabilities. Recon can be passive (collecting data without directly interacting with the target) or active (engaging with the target to gather information).

OSINT
Open Source Intelligence (OSINT) involves collecting data from publicly available sources to gather information on a target. OSINT sources include websites, social media, forums, publicly accessible databases, and other open resources. This intelligence-gathering technique is crucial in cybersecurity, helping to identify exposed information that could be exploited by attackers.

IDS and IPS
IDS (Intrusion Detection System): Monitors network traffic for suspicious activity and alerts administrators of potential threats. It acts as a passive system, detecting and logging incidents without taking direct action against the threats.

IPS (Intrusion Prevention System): Monitors network traffic like an IDS but also takes action to prevent detected threats. An IPS can block malicious traffic, terminate sessions, and take other proactive measures to protect the network from attacks.

# Nmap Commands
Here are some commonly used Nmap commands with brief descriptions:

-sV: Service Version Detection
Detects the versions of the services running on open ports. This helps in identifying specific software and versions to look for vulnerabilities.
-oN <filename>: Normal Output
Saves the scan results in a human-readable format to the specified file. Useful for logging and reviewing scan results later.
-A: Aggressive Scan
Enables OS detection, version detection, script scanning, and traceroute. This provides comprehensive information about the target but is more intrusive and time-consuming.
-T4: Timing Template (Aggressive)
Sets the scan timing template to 4 (Aggressive), making the scan faster but potentially more detectable. Balances speed and accuracy well for most networks.
-p <port ranges>: Port Specification
Specifies which ports to scan. You can define individual ports, ranges of ports, or a combination of both (e.g., -p 80,443,1000-2000).
-O: Operating System Detection
Attempts to determine the operating system of the target device. Useful for tailoring further attacks or defenses based on the OS.
-Pn: No Ping
Disables host discovery, treating all hosts as online. Useful for scanning targets that might be blocking ICMP echo requests (pings).
-sC: Default Scripts
Runs a set of default scripts against the target, which can include vulnerability detection, version checking, and general information gathering.
-sS: Stealth Scan (SYN Scan)
Performs a TCP SYN scan, which is less detectable by the target and often faster than a full connect scan. Useful for evading detection while still gathering significant information.
-sP: Ping Scan
Performs a ping scan to discover active hosts on the network without scanning ports. Useful for a quick check of which IPs are up.
# WafW00f
WafW00f is a tool used to detect the presence and identify the type of Web Application Firewall (WAF) protecting a website. It helps security professionals understand the WAF configuration and potential bypass techniques. WafW00f works by sending a series of crafted HTTP requests to the target website and analyzing the responses. Based on the response patterns, it can identify the WAF and often the specific version, aiding in vulnerability assessment and penetration testing.

Example Commands
Nmap Service Version Detection:

bash
Copy code
nmap -sV example.com
This command will perform a service version detection scan on example.com.

Nmap Aggressive Scan:

bash
Copy code
nmap -A example.com
This command will perform an aggressive scan, providing detailed information about example.com.

WafW00f Detection:

bash
Copy code
wafw00f example.com
This command will check if example.com is protected by a WAF and identify the type of WAF.

These tools and commands are essential in the toolkit of network administrators and security professionals, providing deep insights into network security and helping in the detection and mitigation of potential threats.# Nmap 7.94SVN scan initiated Tue Jun 18 12:08:09 2024 as: nmap -sS -sV -p- --script vuln,auth,default,discovery,external -oN scan_results.txt stjosephandmarysschool.com




Let's Scan a random school website with Nmap and store the results in a file 

```Pre-scan script results:
| targets-ipv6-multicast-mld: 
|   IP: fe80::1207:b6ff:fe1b:90da  MAC: 10:07:b6:1b:90:da  IFACE: eth1
|   IP: fe80::6a88:3f4c:b092:6c94  MAC: f8:54:f6:98:14:21  IFACE: eth1
|   IP: fe80::8133:562c:8db1:d2a5  MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|   IP: fe80::9cc2:bafb:f146:b561  MAC: 0a:00:27:00:00:12  IFACE: eth0
|   IP: fe80::f427:f9ff:fe56:3eed  MAC: f6:27:f9:56:3e:ed  IFACE: eth1
| 
|_  Use --script-args=newtargets to add the results as targets
| ipv6-multicast-mld-list: 
|   fe80::9cc2:bafb:f146:b561: 
|     device: eth0
|     mac: 0a:00:27:00:00:12
|     multicast_ips: 
|       ff02::1:ff46:b561         (NDP Solicited-node)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:ff5d:ed8a         (Solicited-Node Address)
|       ff02::fb                  (mDNSv6)
|       ff02::1:ff60:1735         (Solicited-Node Address)
|       ff02::c                   (SSDP)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|   fe80::6a88:3f4c:b092:6c94: 
|     device: eth1
|     mac: f8:54:f6:98:14:21
|     multicast_ips: 
|       ff02::c                   (SSDP)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|       ff02::1:ffaa:49e8         (Solicited-Node Address)
|       ff02::1:ffa1:963          (Solicited-Node Address)
|       ff02::fb                  (mDNSv6)
|       ff02::1:ffa7:58ab         (Solicited-Node Address)
|       ff02::1:ff04:f96f         (Solicited-Node Address)
|       ff02::1:ff92:6c94         (NDP Solicited-node)
|       ff02::1:3                 (Link-local Multicast Name Resolution)
|   fe80::f427:f9ff:fe56:3eed: 
|     device: eth1
|     mac: f6:27:f9:56:3e:ed
|     multicast_ips: 
|       ff02::1:ff56:3eed         (NDP Solicited-node)
|       ff05::2                   (unknown)
|       ff02::1:ff00:0            (Solicited-Node Address)
|       ff02::2                   (All Routers Address)
|       ff02::1:ff7d:6d08         (Solicited-Node Address)
|       ff02::1:ffa5:b900         (Solicited-Node Address)
|   fe80::8133:562c:8db1:d2a5: 
|     device: eth1
|     mac: b4:e2:65:3f:da:f8
|     multicast_ips: 
|       ff02::1:ffb1:d2a5         (NDP Solicited-node)
|       ff02::1:ff0e:ceac         (Solicited-Node Address)
|       ff02::1:ffaa:2726         (Solicited-Node Address)
|       ff02::1:ffff:b102         (Solicited-Node Address)
|       ff02::1:ff69:744c         (Solicited-Node Address)
|   fe80::1207:b6ff:fe1b:90da: 
|     device: eth1
|     mac: 10:07:b6:1b:90:da
|     multicast_ips: 
|       ff02::1:ffe6:3d4b         (Solicited-Node Address)
|_      ff02::1:ff1b:90da         (NDP Solicited-node)
| targets-ipv6-multicast-slaac: 
|   IP: fe80::be81:6157:f40e:ceac  MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|   IP: fe80::7074:b51e:af69:744c  MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|   IP: fe80::42af:14c5:555d:ed8a  MAC: 0a:00:27:00:00:12  IFACE: eth0
|   IP: fe80::e395:76f8:8eaa:49e8  MAC: f8:54:f6:98:14:21  IFACE: eth1
|   IP: fe80::588b:8dc0:cf60:1735  MAC: 0a:00:27:00:00:12  IFACE: eth0
|   IP: fe80::258c:dc70:33a7:58ab  MAC: f8:54:f6:98:14:21  IFACE: eth1
|   IP: fe80::1207:b6ff:fe1b:90da  MAC: 10:07:b6:1b:90:da  IFACE: eth1
|   IP: fe80::7120:59eb:74e6:3d4b  MAC: 10:07:b6:1b:90:da  IFACE: eth1
|   IP: fe80::f427:f9ff:fe56:3eed  MAC: f6:27:f9:56:3e:ed  IFACE: eth1
|   IP: fe80::4132:161e:4ea5:b900  MAC: f6:27:f9:56:3e:ed  IFACE: eth1
|_  Use --script-args=newtargets to add the results as targets
| targets-asn: 
|_  targets-asn.asn is a mandatory parameter
|_hostmap-robtex: *TEMPORARILY DISABLED* due to changes in Robtex's API. See https://www.robtex.com/api/
| targets-ipv6-multicast-invalid-dst: 
|   IP: fe80::9cc2:bafb:f146:b561               MAC: 0a:00:27:00:00:12  IFACE: eth0
|   IP: fe80::6a88:3f4c:b092:6c94               MAC: f8:54:f6:98:14:21  IFACE: eth1
|   IP: 2405:201:8017:8809:644b:6a46:63a1:963   MAC: f8:54:f6:98:14:21  IFACE: eth1
|   IP: fe80::8133:562c:8db1:d2a5               MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|   IP: 2405:201:8017:8809:2c9b:ab3a:82aa:2726  MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|_  Use --script-args=newtargets to add the results as targets
| targets-ipv6-multicast-echo: 
|   IP: fe80::f2ed:b8ff:fe4a:eee8               MAC: f0:ed:b8:4a:ee:e8  IFACE: eth1
|   IP: 2405:201:8017:8809:f2ed:b8ff:fe4a:eee8  MAC: f0:ed:b8:4a:ee:e8  IFACE: eth1
|   IP: fe80::8133:562c:8db1:d2a5               MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|   IP: 2405:201:8017:8809:2c9b:ab3a:82aa:2726  MAC: b4:e2:65:3f:da:f8  IFACE: eth1
|   IP: fe80::1207:b6ff:fe1b:90da               MAC: 10:07:b6:1b:90:da  IFACE: eth1
|   IP: fe80::f427:f9ff:fe56:3eed               MAC: f0:ed:b8:4a:ee:ea  IFACE: eth1
|   IP: 2405:201:8017:8809:7120:59eb:74e6:3d4b  MAC: 10:07:b6:1b:90:da  IFACE: eth1
|   IP: 2405:201:8017:8809:8431:3df1:8a7d:6d08  MAC: f0:ed:b8:4a:ee:ea  IFACE: eth1
|_  Use --script-args=newtargets to add the results as targets
| broadcast-igmp-discovery: 
|   192.168.29.1
|     Interface: eth1
|     Version: 2
|     Group: 224.0.0.2
|     Description: All Routers on this Subnet
|   192.168.29.1
|     Interface: eth1
|     Version: 2
|     Group: 224.0.0.22
|     Description: IGMP
|   192.168.29.62
|     Interface: eth1
|     Version: 2
|     Group: 224.0.0.252
|     Description: Link-local Multicast Name Resolution (rfc4795)
|   192.168.29.134
|     Interface: eth1
|     Version: 2
|     Group: 224.0.0.251
|     Description: mDNS (rfc6762)
|   192.168.56.1
|     Interface: eth0
|     Version: 2
|     Group: 224.0.0.252
|     Description: Link-local Multicast Name Resolution (rfc4795)
|   192.168.29.62
|     Interface: eth1
|     Version: 2
|     Group: 239.255.255.250
|     Description: Organization-Local Scope (rfc2365)
|   192.168.56.1
|     Interface: eth0
|     Version: 2
|     Group: 239.255.255.250
|     Description: Organization-Local Scope (rfc2365)
|_  Use the newtargets script-arg to add the results as targets
|_http-robtex-shared-ns: *TEMPORARILY DISABLED* due to changes in Robtex's API. See https://www.robtex.com/api/
```
