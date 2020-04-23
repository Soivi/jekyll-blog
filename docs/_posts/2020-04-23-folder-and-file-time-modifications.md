---
layout: post
title:  "Folder and File time modifications"
categories: cleaning
summary: Change folder and file modification times
---

{% include instructions.md %}

### {{page.title}}

Check a folder or a file creation and modification time
```shell
# stat [target folder/file]
```

Change a folder or a file creation and modification time to YYYYMMDDhhmm
```shell
# touch -t 201212211111 [target folder/file]
```

Change a folder or a file modification time to YYYYMMDDhhmm
```shell
# touch -mt 201212211111 [target folder/file]
```

Copy creation and modification time from other file or folder
```shell
# touch [target folder/file] -r [source folder/file]
```

List all files that has been changed in 7 days
```shell
# find [target folder] -iname "*" -atime -7 -type f
```

List all folders that has been changed in 7 days
```shell
# find [target folder] -iname "*" -atime -7 -type d
```

Change creation and modification time for all files that has been modified in 7 days
```shell
# touch -t 201212211111 $(find [target folder] -iname "*" -atime -7 -type f)
```

Change creation and modification time for all folders that has been modified in 7 days
```shell
# touch -t 201212211111 $(find [target folder] -iname "*" -atime -7 -type d)
```

Copy creation and modification time for all files that has been modified in 7 days. Source folder could be something like /bin

```shell
# touch $(find [target folder] -iname "*" -atime -7 -type f) -r [source folder/file]
```
