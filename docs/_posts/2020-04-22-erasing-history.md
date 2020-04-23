---
layout: post
title:  "Erasing history"
categories: cleaning
summary: Cleaning your evil deeds
---

{% include instructions.md %}

### {{page.title}}

Remove old history
```shell
# rm -r ~/.bash_history
```

Clean session history and exit
```shell
# history -c && exit
```

Link history to /dev/null so history does not save anything
```shell
# ln -sf /dev/null ~/.bash_history
```