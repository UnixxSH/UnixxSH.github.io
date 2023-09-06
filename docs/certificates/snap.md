---
layout: default
title: snap
parent: certificates
nav_order: 2
---

### import CA certificate in a snap (mandatory for bitwarden client)
```
certutil -d /path/to/snap/.pki/nssdb -A -t "TC,," -n "CA name" -i /path/to/cert
```
