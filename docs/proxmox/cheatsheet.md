---
layout: default
title: Cheatsheet
parent: proxmox
nav_order: 1
---

### enable Wake on Lan

Add in /etc/network/interfaces
```
_post-up /usr/sbin/ethtool -s eno1 wol g_
```

### disable subscription popup (very annoying)
```
sed -i.bak 's/notfound/active/g' /usr/share/perl5/PVE/API2/Subscription.pm && systemctl restart pveproxy.service
```
OR
```
sed -Ezi.bak "s/(Ext.Msg.show\(\{\s+title: gettext\('No valid sub)/void\(\{ \/\/\1/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js && systemctl restart pveproxy.service
```