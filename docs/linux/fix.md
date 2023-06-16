---
layout: default
title: Fixs
parent: linux
nav_order: 2
---

### video stutter (Fedora)
```
dnf groupupdate multimedia --setop="install_weak_deps=False" --exclude=PackageKit-gstreamer-plugin

dnf groupupdate sound-and-video 
```