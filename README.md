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

# Usage
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

# License
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

✨🍰✨
