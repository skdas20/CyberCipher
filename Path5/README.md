
## Spiderfoot 

SpiderFoot is an open-source intelligence (OSINT) automation tool that gathers extensive information about a target (e.g., domain, IP address) from numerous public sources.

Usage -

- New Scan 
- Put the scan name and scan target website
- We will be able to fetch some basic informations of the website 
- With APIs we can gather all the informations about the website
 
- It is good to go with passive scan which does not make too many requests to the server and we don't get flagged as malicious IP by the Firewall.


##theHarvester (A social Engineering tool)

theHarvester is an open-source intelligence (OSINT) tool designed for gathering information about a specific target, such as an organization or individual. 
## Spiderfoot initialisation


# Know your IP
```bash
  ifconfig eht0
```

# Start Spiderfoot from kali's IP

```bash
sudo spiderfoot -l IP:Port
```

## theHarvester initialisation

# Find a domain
 
 ```bash
 theHarvester -d anydomain.in -b bing
 ```
 
## Documentation

[Dummy Website for testing](testphp.vulnweb.com)

