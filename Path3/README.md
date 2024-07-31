
# Linux File Permissions

R-4,W-2,X-1;

   owner - group -  all
   d- directory and - File
 upgrading Permissions =chmod code filename  (Code- 421 or 600)
 Changing Owner =chown Travis filename(Travis-owner)


 # Editors

 hexeditors filename

 graohical= mousepad filename

 # Custom Commands
 we can create our custom commans with Ai tools


 # File Identification

 OS identifies a file type by its signature
 It can differentiate file and directory only


 # Port Forwarding with Ngrok

 install and set up ngrok in kali linux 

![Example Image](./Screenshot(550).png)
![Example Image](./Screenshot(551).png)

# Why Port Forwarding
with PF we can forwar any service like apache,ssh,etc. unlike simple ssh.

 # New Commands used

 - wget link(Download)
 
 - nmap -p- localhost(for knowing service ports)
## Port Forwarding

To run , run the following command

```cmd(linux)
  ./ngrok tcp 22

```

```cmd(Connecting device)
  ssh kali@0.tcp.in.ngrok.io -p 14788
```
