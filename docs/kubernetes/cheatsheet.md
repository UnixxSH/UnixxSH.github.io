---
layout: default
title: commands
parent: kubernetes
nav_order: 1
---

### Purge failed pods
```
kubectl delete pods -A --field-selector=status.phase=Failed
```

### exec as user
```
kubectl auth can-i get pods --as=fatuser
```