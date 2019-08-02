<img src="https://img.shields.io/badge/status-unstable-orange.svg"> <img src="https://img.shields.io/badge/Python-2.7%2B-brightgreen.svg"> <img src="https://img.shields.io/badge/Ansible-2.8%2B-red.svg"> <img src="https://img.shields.io/badge/Testinfra-3.0%2B-red.svg">

# ansible-playbook
A Handy Skeleton for Ansible Playbook Project

# The Stack
- Python2.7+
- [Ansible](https://www.ansible.com/)
- [Vagrant](https://www.vagrantup.com/) is a tool to setup and provision development environments.
- VirtualBox
- [Testinfra](https://testinfra.readthedocs.org/) to run the tests
- [Pipenv](https://github.com/pypa/pipenv) pacakge manager and setup virtualenv.
- [Tox](https://tox.readthedocs.org/) to setup the [virtualenv](https://virtualenv.pypa.io/en/latest/) and run vagrant and testinfra.

# Install
1) Clone skeleton from GitHub.
```
git clone git@github.com:fsjohnhuang/ansible-playbook.git
```
2) Install pipenv.(Assuming Python2.7+ has installed)
```
pip install --user --upgrade pipenv
```
3) Install development denpendencies.
```
pipenv install --dev
```

# Ansible
## Ansible Project-Based Configuration


## Group and Host Vars
1. The `group_vars` and `host_vars` directories can exist in the playbook directory(i.e. `./src/` in this project) or the inventory directory(i.e. `./inventories` in this project). If both paths exist, variables in the playbook directory will override variables set in the inventory directory.
2. The `ansible-playbook` command looks for `group_vars` and `host_vars` in the playbook directory by default.
3. The `ansible` and `ansible-console` commands will only look for `group_vars` and `host_vars` in the inventory directory, unless you provide the `--playbook-dir` option on the command line.

*For keeping things in same pace, recommand placing `group_vars` and `host_vars` in the inventory directory strongly as this project has done.*

## Variables Merge Rules
The lowest to highest order is:
1. all group
2. parent group
3. child group
4. host

When groups of the same parent/child level are merged in alphabetical order, and the variables of last group loaded overwrites those of the previous groups.

### Sample
In inventory file

``` ini

[web]
x.x.x.x ansible_ssh_user="root" ansible_ssh_pass="root"

[prod-web:children]
web

[windows:children]
web
```

In `group_vars/prod-web.yml`

``` yaml
---
NAME: "prod-web"
FOR: "everyone"
```

In `group_vars/windows.yml`

``` yaml
---
NAME: "windows"
CONNECT: "winrm"
```

The final merged result is:

``` yaml
---
NAME: "prod-web"
FOR: "everyone"
CONNECT: "winrm"
```

# License
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

✨🍰✨
