---
layout: default
title: Commands
parent: Kubernetes
nav_order: 1
---

# Commands

___

## Purge failed pods
```
kubectl delete pods -A --field-selector=status.phase=Failed
```

___

## exec as user
```
kubectl auth can-i get pods --as=fatuser
```

___

## Purge notready pods (crictl)
```
for i in `crictl pods | grep NotReady | awk '{print $1}'`; do crictl rmp $i; done
```

___

## Force namespace deletion
```
kubectl get namespace <ns> -o json > <ns>.json
```
```
kubectl replace --raw "/api/v1/namespaces/<ns>/finalize" -f ./<ns>.json
```

___

## Allow pods to communicate with firewalld
```
firewall-cmd --permanent --new-zone=<name>
```
```
firewall-cmd --permanent --zone=<name> --set-target=ACCEPT
```
```
firewall-cmd --permanent --zone=<name> --add-source=<cluster_pods_cidr>
```

___

## containerd push registry
```
ctr content fetch --platform linux/amd64 docker.io/library/postgres:15.1-alpine
```

```
ctr images tag docker.io/library/postgres:15.1-alpine localhost:32000/postgres:15.1-alpine
```

```
ctr images push --platform linux/amd64 localhost:32000/postgres:15.1-alpine
```

___

## Get the owner of all pods
```
kubectl get pods -A -o jsonpath='{range .items[*]}{.metadata.name} {.metadata.ownerReferences[].kind}{"\n"}{end}'
```