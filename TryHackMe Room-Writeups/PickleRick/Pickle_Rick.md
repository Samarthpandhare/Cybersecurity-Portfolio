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
![Source: web server source code](<TryHackMe Room-Writeups/PickleRick/screenshots/source_code_of_web_server.png>)


