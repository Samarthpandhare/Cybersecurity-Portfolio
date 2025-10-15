# Room: Bounty Hacker # (https://tryhackme.com/room/cowboyhacker)
---
## Description ##
- We have to find the user & password.
- find the user flag.
- find the root flag.
---
## Tools needed ## 
- linux
- nmap
- Hydra
---
## Skills Required ##
- linux(tools & commands)
- Privilage Escalation
- security
- tar
---
## Steps to complete this machine ##

1. ### Network & Ports scanning ###
   - Use the Nmap for scanning the target network and ports to find the important information about open ports.
   ```bash
   nmap -T5 -p- -VV -sV 10.10.148.152
   ```
   - `-T5` Aggressive scan
   - `-p-` Scan ports from 1 to 1000
   - `-sV` To find Service Versions
   - `-VV` For Verbose scanning
 - Output
   ![Source: Nmap results](screenshots/NmapResult.png)
 - The first interesting information from the nmap scan result is “anonymous” login is allowed through FTP protocol. We can do this by connecting using: ftp 10.10.148.152.
   
 2. ### FTP anonymous login ###
 - When prompted to enter a username/name, use: anonymous and login.
 - Let's see what is on the FTP server where we're logged in.
 - Output:
   ![Source: FTP anonymous](screenshots/ftp.png)
      

     
   


---
## Credits ##
- Shout-out to @Sevuhl for creating this room.
- Visit https://tryhackme.com for great learning.
  
