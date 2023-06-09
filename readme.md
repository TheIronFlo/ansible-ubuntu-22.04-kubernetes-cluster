# Ansible-repository for a kubernetes-cluster

## about

This repository is just a bit of Ansible-code to build and maintain my kubernetes--reference-cluster v1.26.* based on Ubuntu Linux 22.04 LTS.


## prerequesites

You need exactly six VMs with installed Ubuntu 22.04, a minimum of 2 GB of RAM and SSH access to the machines. I use some VMs on my Laptop using KVM with `192.168.122.0/24` (NAT) network.

One (control-plane) will be called `k8s-master`, the others are workers named `worker[1..5]`. Adjust IP-Adresses in `inventory` file and in `01-preparations.yaml`. Adjust SSH-key-file (`ansible_ssh_private_key_file`) in `inventory` file.

## tools

Grafana: http://192.168.122.150/grafana
Longhorn: http://192.168.122.150/longhorn

## run the playbooks

```
ansible-playbook -i inventory 01-preparations.yaml
```

```
ansible-playbook -i inventory 02-controlplane.yaml
```

```
ansible-playbook -i inventory 03-workers.yaml
```
