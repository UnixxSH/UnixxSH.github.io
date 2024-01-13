---
layout: default
title: Cheatsheet
parent: Linux
nav_order: 3
---

# Cheatsheet

___

## Process mem usage in Mb
```
ps aux | awk '{print $6/1024 " MB\t\t" $11}' | sort -n
```

___

## remove null from exp results in jq
```
jq '<expression> | select(.Timestamp != null)
```

___

## import CA certificate in a snap (mandatory for bitwarden client)
```
certutil -d /path/to/snap/.pki/nssdb -A -t "TC,," -n "CA name" -i /path/to/cert
```