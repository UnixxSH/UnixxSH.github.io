---
layout: default
title: Cheatsheet
parent: vault
grand_parent: hashicorp
nav_order: 1
---

# force remove expired certs
```
vault write pki/tidy tidy_cert_store=true tidy_revoked_certs=true
```