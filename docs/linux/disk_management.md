---
layout: default
title: Disk management
parent: linux
nav_order: 1
---

### Force disk disconnect
echo 1 | tee /sys/block/[[device]]/device/delete