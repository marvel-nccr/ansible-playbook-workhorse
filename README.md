# Quantum Mobile Workhorse

This ansible playbook installs a 
[Quantum Mobile](https://github.com/marvel-nccr/quantum-mobile)
workhorse server on a remote virtual machine (tested on OpenStack and Amazon
Web Services).

### Prerequisites

- A virtual machine running Ubuntu 18.04
- passwordless ssh access to the VM via ssh key
- [python](https://www.python.org/)

```
git clone git@github.com:marvel-nccr/ansible-playbook-workhorse.git
cd ansible-playbook-workhorse
pip install -r requirements.txt
ansible-galaxy install -r requirements.yml
```

### Set up Virtual Machine

1. select aws/os host in `./hosts` file
1. adapt path to your ssh key in corresponding `./group_vars/*.yml` file
1. run `ansible-playbook playbook.yml`

## Acknowledgements

This work is supported by the [MARVEL National Centre for Competency in
Research](http://nccr-marvel.ch) and the [MaX European centre of
excellence](http://www.max-centre.eu/)
