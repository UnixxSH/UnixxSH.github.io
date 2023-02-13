---
layout: default
title: Wake On Lan
parent: proxmox
nav_order: 1
---

### /etc/network/interfaces
_post-up /usr/sbin/ethtool -s eno1 wol g_