# Workhorse

This is an ansible playbook for installing a 
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
git clone git@github.com:materialscloud-org/ansible-playbook-workhorse.git
cd ansible-playbook-workhorse
pip install -r requirements.txt  # installs python requirements
ansible-galaxy install -r requirements.yml  # installs ansible roles
wget https://networkgenomics.com/try/mitogen-0.2.8.tar.gz && tar xf mitogen-0.2.8.tar.gz
```

### Set up Virtual Machine

1. select aws/os host in `./hosts` file
1. adapt path to your ssh key in corresponding `./host_vars/*.yml` file
1. run `ansible-playbook playbook.yml`

## Acknowledgements

This work is supported by the [MARVEL National Centre for Competency in
Research](http://nccr-marvel.ch) and the [MaX European centre of
excellence](http://www.max-centre.eu/)
