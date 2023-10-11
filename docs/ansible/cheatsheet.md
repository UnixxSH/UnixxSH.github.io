---
layout: default
title: Cheatsheet
parent: ansible
nav_order: 1
---

### dynamic variables
##### example1
{% raw %}
```
'{{ lookup('vars', 'somevar_' ~ other_var) }}'
```
##### example2
```
'{{ regex_search('/.+?(?=/' ~ sid ~ ')') }}'
```
{% endraw %}

### get file names from find module
{% raw %}
```
- ansible.builtin.find:
    paths: "/my/path"
  register: my_list

- ansible.builtin.set_fact:
    myvar: "{{ my_list['files'] | map(attribute='path') | map('basename') | list }}"
```
{% endraw %}
