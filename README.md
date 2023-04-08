# Ansible Kubernetes

This repository contains ansible playbooks for installing Kubernetes cluster.

I wanted to learn about Kubernetes, related network plugins and have possibility to create lab/test clusters with ansible.  
This was starting idea behind that project.  

Cluster details:
- single control plane node
- multiple workers
- installation with kubeadm
- container runtime - containerd
- network plugin - Calico

Cluster installation was tested on Ubuntu Bionic, Jammy virtual machines.  

# Usage
Install dependencies and add required settings to servers for Kubernetes cluster installation:
```console
ansible-playbook -i hosts playbooks/k8s-prepare.yaml
```

Install Kubernetes cluster:
```console
ansible-playbook -i hosts playbooks/k8s-install.yaml
```

Deploy Calico in Kubernetes cluster:
```console
ansible-playbook -i hosts playbooks/calico-install.yaml
```

# Authentication

SSH key is used for Ansible authentication towards servers.

More informations about deployment and configuration of test VMs which contain  
related SSH public key can be found [here](https://github.com/mbarecki/kvm-ubuntu-server-deployer).

***Note: SSH private key should be kept secret.  
In this repository private key is added for test/lab purposes.***

Account details on Kubernetes control plane node which could be used to interact with cluster:
```console
username: operator
password: test
```

# Ansible installation
Prepare python virtual environment and install ansible in it:
```console
apt-get install python3-venv

python3 -m venv /tmp/ansible
source /tmp/ansible/bin/activate
python3 -m pip install -U pip
python3 -m pip install ansible
```
