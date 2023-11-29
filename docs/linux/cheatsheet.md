---
layout: default
title: Cheatsheet
parent: linux
nav_order: 3
---

### Process mem usage in Mb
```
ps aux | awk '{print $6/1024 " MB\t\t" $11}' | sort -n
```

### remove null from exp results in jq
```
jq '<expression> | select(.Timestamp != null)
```
