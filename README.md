# Quantum Mobile Workhorse

This ansible playbook installs a 
[Quantum Mobile](https://github.com/marvel-nccr/quantum-mobile)
workhorse server on a remote virtual machine (tested on OpenStack, Amazon Web Services and Huawei Cloud).

### Prerequisites

#### Server
- A server running Ubuntu 18.04 
  Can be hardware or virtual machine (tested on OpenStack, Amazon Web Services and Huawei Cloud).
- Access to server via SSH key

Note on security rules:
- SSH access requires port 22 to be open
- You may want to open further port for other servers:
  - port 8888 to connect to Jupyter Notebook Servers (AiiDA lab)
  - port 5000 to connect to the AiiDA REST API

#### Client
- [python](https://www.python.org/)
- [git](https://git-scm.com)

To get set up, run the following on your client:
```
git clone https://github.com/marvel-nccr/ansible-playbook-workhorse.git
cd ansible-playbook-workhorse
pip install -r requirements.txt  # installs python requirements
ansible-galaxy install -r requirements.yml  # installs ansible roles
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

## Tweaks

### Slow network connection

.inWhen provisioning machines in remote networks (e.g. Asia), the time needed for establishing an SSH connection can be prohibitively slow.
In such cases, the "mitogen" connection plugin can lead to dramatic speedups (it uses python remote procedure calls).

In order to enable mitogen, execute the following command
```
wget https://networkgenomics.com/try/mitogen-0.2.8.tar.gz && tar xf mitogen-0.2.8.tar.gz
```
and uncomment the corresponding lines in the `ansible.cfg` file.

In my tests, an example task (adding the "max" user to two new user groups) took 15s on an AWS VM in the hongkong region, and 156s on a Huawei Cloud VM in the Guangzhou region (and that's after turning on "pipelining" to reduce the number of SSH connections).
Switching to mitogen brought down the timings to 1s for the AWS hongkong machine and 3s on the Huawei VM (i.e. more than one order of magnitude).

## Acknowledgements

This work is supported by the [MARVEL National Centre for Competency in
Research](http://nccr-marvel.ch) and the [MaX European centre of
excellence](http://www.max-centre.eu/)
