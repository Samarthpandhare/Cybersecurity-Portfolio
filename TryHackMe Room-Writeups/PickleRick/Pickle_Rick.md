# [PICKLE RICK]
[TryHackMe Room Link](https://tryhackme.com/room/picklerick)

---
## Introduction
this writeup is for documenting the steps I took to complete Tryhackme.com (THM)’s room Pickle Rick hacking tasks.

---
## 🏆 Objective
This Ricky and Morty themed challenge requires you to exploit a webserver.
To find the three Flags.
Find the three ingredients that will help Rick make his potion to transform himself back into a human from a pickle.

---

## 🛠 Tools Used
- Nmap
- Gobuster
- netcat
- http://pentestmonkey.net/cheat-sheet/shells/reverse-shell-cheat-sheet

---

## 📝 Steps / Solution

1. **Find the open ports of machine using Nmap**

I ran an Nmap full-port service/version scan to discover open TCP ports and services:

```bash
nmap -T4 -p- -sV -vv 10.10.122.238
```

- `-p-` scans all 65535 TCP ports  
- `-sV` attempts service/version detection  
- `-T4` is aggressive but safer than `-T5` on target networks (avoid `-T5` on production/public infra)

**Sample output:**
```text
PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 8.2p1
80/tcp   open  http       Apache httpd 2.4.41
```
ports 22 & 80 are open!

2. **Browsed to webpage**
Reviewed the source of this page that gave a username “R1ckRul3s”.
![Source: web server source code](screenshots/source_code_of_web_server.png)

3. **Used gobuster to brute force directories to discover directories and pages on this website. Gobuster discovered few interesting pages**
```bash
sudo gobuster dir -u http://10.10.122.238/ -w /usr/share/wordlists/dirb/common.txt -e -x php,html,txt -t 40 
```
`-u http://10.10.122.238/` Target URL to test
`-w /usr/share/wordlists/dirb/common.txt` The wordlist Gobuster will use
`-e (or --expanded)` Expanded mode — print full URLs
`-x php,html,txt (or --extensions)` Try the specified file extensions for each word
`-t 40` Number of concurrent threads (workers). Higher = faster but more load on target and your network. 40 is aggressive; if the target is slow or rate‑limits, lower it.

![Source: Gobuster Output](screenshots/GoBuster_output.png)
We found some intresting Directories as follows:
(a) login.php
(b) robots.txt
(c) server-status

4. **Browsed to “robots.txt” file and found one interesting piece of information there**
`Wubbalubbadubdub`
5. **Browsed to “login.php” and found a login page asking for a username and password**
Tried information gathered in previous steps to login to this portal.
username : `R1ckRul3s`
password : `Wubbalubbadubdub`

We got access to the command panel!

5. **Tried listing the contents of directory**
use: `ls`
![Source: contents of directory](screenshots/Contents_of_dir)
