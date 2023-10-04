---
layout: default
title: Cheatsheet
parent: vyos
nav_order: 2
---

### script post-boot

do not forget to load env
```
#!/bin/vbash
source /opt/vyatta/etc/functions/script-template
```

### openvpn client template

```
client
dev tun
proto udp
remote vpn.liawtdne.fr 1194
resolv-retry infinite
persist-key
persist-tun
remote-cert-tls server
cipher AES-256-CBC
nobind
<ca>
-----BEGIN CERTIFICATE-----
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
-----END PRIVATE KEY-----
</key>
```