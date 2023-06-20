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

### Purge notready pods (crictl)
```
for i in `crictl pods | grep NotReady | awk '{print $1}'`; do crictl rmp $i; done
```