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
   ![Source: Nmap results](screenshots/NmapResult.png)
     
   


---
## Credits ##
- Shout-out to @Sevuhl for creating this room.
- Visit https://tryhackme.com for great learning.
  
