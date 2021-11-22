# ubuntu-dev-ansible
Ansible playbook to setup an ubuntu 20.04 development machine

# Tasks

## Prerequisites

### Install ansible in master node (or localhost)

    sudo add-apt-repository ppa:ansible/ansible
    sudo apt-get update
    sudo apt-get install ansible -y

### Create ssh ansible keys

    ssh-keygen -f $HOME/.ssh/ansible -N ""

### Create inventory file

Create a text file with the managed hosts ips, FQDN, alias, etc... One per line.

    vim hosts

### initial-config-ubuntu-20.04.yml

This playbook setups managed nodes to be administrated from ansible master.

You may have to change **cloud_user** with your sudo user.

      ansible-playbook -l ubuntu -i hosts -u cloud_user initial-config-ubuntu-20.04.yml -k -K

- Connects to managed nodes using cloud_user user and password.
- -k option ask for user password.
- -K option ask for become password.
- Create and add **ansible** user to sudoers with NOPASSWD policy in managed hosts
- Copy ssh **ansible** key to managed hosts authorizedkays
- Disable ssh password authentication

# TO-DO
- [X] Prerequisites
- [X] update & upgrade system
- [X] install apt dependencies
    - jq jinja2
- [X] install pip3 dependencies
    - youtube-dl
- [X] add hashicorp repository
- [X] add docker repository
- [X] install terraform
- [X] install vault
- [X] install packer
- [ ] install docker
- [ ] install awscli
- [ ] install azcli
- [ ] install gcloud util
- [ ] install kubectl
- [ ] install kubeadm
- [ ] install eksctl
- [ ] install helm
- [ ] 