# Workhorse

This is an ansible playbook for installing a workhorse server on an OpenStack virtual machine.

### Prerequisites

- A virtual machine running Ubuntu 16.04
- passwordless ssh access to the VM via ssh key
- [python](https://www.python.org/)

### Create Virtual Machine

```
git clone git@github.com:materialscloud-org/ansible-playbook-workhorse.git
cd ansible-playbook-workhorse
pip install -r requirements.txt
ansible-galaxy install -r requirements.yml
# todo: add path to your ssh key in ./host_vars/workhorse.yml
ansible-playbook playbook.yml
```

## Acknowledgements

This work is supported by the [MARVEL National Centre for Competency in
Research](http://nccr-marvel.ch) and the [MaX European centre of
excellence](http://www.max-centre.eu/)
