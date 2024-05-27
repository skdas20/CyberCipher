
# Need for Port Forwarding
We need a server to accomplish our task because if we use our Dynamic IP ,the Reception of data from the object end is not possible because our IP would change.Therefore,we either need to pay for a public IP or utilise port forwarding

# Distributed Denial of Service Attack(DDos)
A Distributed Denial of Service (DDoS) attack overwhelms a target server, service, or network with massive traffic from multiple compromised devices, causing disruption and preventing legitimate access. Attackers use botnets to flood the target, exhausting its resources and making it unresponsive.

# Apache2 Service
 Allows users to host web applications and sites.It uses HTTP and HTTPs protocols


# Seeker Utility

A social engineering tool that can be used to attain some informations based on conditions.

- Need to forward the port of interaction
- Using Any of the 4 methods 
Example- With google drive link of a file we can generate location tracker link that uses html to gather location.

- We can customize the HTML page tactfully to ask for informations in a more convincing way

# Whatsapp Preview Must be turned off for safety

 


## Documentation

[Seeker](https://github.com/keralahacker/seeker)


## Apache Installation and utilization



```bash
  sudo apt-get install apache2
  sudo systemctl start apache2
```
# Visit localhost to view apache server

# To change port number,edit the the port.conf with nano 

``` bash
sudo nano /etc/apache2/ports.conf
```

## Port Forwarding the Apache server

```bash
./ngrok http 80
``` 

## Modify index.html to alter the apache server page content

```bash
ls -lh /var/www/html

sudo cp -r index.html /var/www/html
```

# Seeker( A Social Engineering Tool)

```bash 
./install.sh
python3 seeker.py -t manual
```
# Significance of .zshrc file


The .zshrc file can be particularly useful in the context of hacking and penetration testing because it allows you to customize your shell environment for efficiency and automation. 

While attacking a system if the code is embedded in the .zshrc file the hacker gets back a connection when the terminal is restarted.
