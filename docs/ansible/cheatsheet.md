---
layout: default
title: Cheatsheet
parent: ansible
nav_order: 1
---

### dynamic variables
{% raw %}
```
'{{ lookup('vars', 'somevar_' ~ other_var) }}'
```
{% endraw %}