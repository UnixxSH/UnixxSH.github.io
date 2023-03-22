---
layout: default
title: Disk management
parent: linux
nav_order: 1
---

### Force disk disconnect
echo 1 | tee /sys/block/[[device]]/device/delete

### Most disk usage
du -h [[dir]] 2>/dev/null | grep '[0-9\.]\+G'
