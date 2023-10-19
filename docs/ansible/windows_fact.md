---
layout: default
title: windows_fact.ps1
parent: ansible
nav_order: 2
---

```
$someValue = value

@{
    othervalue = $someValue
}
```

```
- hosts: windows
  tasks:
    - name: Set Windows Ansible facts folder, and add informations to setup vars
      setup:
        fact_path: "C:\\Program Files\\Ansible\\facts"
      register: setupvar
    - debug:
        var: ansible_windows_fact.othervalue
```
