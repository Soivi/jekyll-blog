---
layout: post
title:  "SSH listening different port using reverse shell"
categories: ssh reverse_shell
summary: Add new listening port to SSH using reverse shell
---

{% include instructions.md %}

### {{page.title}}

Add PORT 2222 end of the /etc/ssh/sshd_config
```shell
# echo PORT 2222 >> /etc/ssh/sshd_config
```

Restart SSH daemon
```shell
# service ssh restart
```

Now you can take SSH to port 2222
```shell
# ssh [username]@[victim ip address] -p 2222
```
