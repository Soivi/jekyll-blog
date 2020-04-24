---
layout: post
title:  "Clean logs"
categories: cleaning
summary: Remove logs files
---

{% include instructions.md %}

### {{page.title}}

Delete all useful log files
```shell
# rm -r /var/log/apache2
# rm -r /var/log/apt
# rm /var/log/mail*
# rm /var/log/dpkg.log
# rm /var/log/syslog*
# rm /var/log/auth*
```