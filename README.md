![ansible](ansible-logo.png)

# Ansible - Deploy Kubernetes cluster on CentOS 7 (with Firewalld)
Current Ansible template create Kubernetes cluster on CentOS 7 with enabled Firewalld service and join nodes

## Requires Ansible version >= 2.7

## This template works with Ansible roles:

`vars/main.yaml` contains name of user for Kubernetes (not a root)

First you must copy all directory `roles` to `/etc/ansible/roles/`

```bash
sudo cp -R roles/* /etc/ansible/roles/ 
```

Edit your ansible config file `/etc/ansible/ansible.cfg`
Make sure that the server option is not commented out and contains the correct path

```bash
/etc/ansible/roles
```

### Template expect, that Kubernetes master will be `localhost` and nodes will added to hosts file `/etc/ansible/hosts` like this:

```bash
[node]
192.168.1.101 ansible_ssh_user=root
```

## Create cluster
```bash
ansible-playbook master.yaml
```

## Add nodes
```bash
ansible-playbook node.yaml
```