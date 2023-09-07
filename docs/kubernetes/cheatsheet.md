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

### Force namespace deletion
```
kubectl get namespace <ns> -o json > <ns>.json
```
```
kubectl replace --raw "/api/v1/namespaces/<ns>/finalize" -f ./<ns>.json
```

### Allow pods to communicate with firewalld
```
firewall-cmd --permanent --new-zone=<name>
```
```
firewall-cmd --permanent --zone=<name> --set-target=ACCEPT
```
```
firewall-cmd --permanent --zone=<name> --add-source=<cluster_pods_cidr>
```