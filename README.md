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
1. adapt path to your ssh key (to connect as admin to the VM)
   in corresponding `./group_vars/*.yml` file
1. Tune the `globalconfig.yml` file (in particular `vm_user`, `vm_memory`, `vm_cpus`)
1. edit the `playbook.yml` file replacing, in the role `"add user {{ vm_user }} with key" (marvel-nccr.add_user`),
   under `add_user_public_key`, the correct path to the public key the students will have: 
1. Tune what you want to have in the machine in the `playbook.yml` file
1. run `ansible-playbook playbook.yml`

## Acknowledgements

This work is supported by the [MARVEL National Centre for Competency in
Research](http://nccr-marvel.ch) and the [MaX European centre of
excellence](http://www.max-centre.eu/)
