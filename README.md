# ansible-infra
Collection ansible roles and playbooks

### Install ansible

Debian like
```
apt -y install ansible sshpass
```
RedHat like 
```
yum -y install ansible sshpass
```

### Inventory
https://docs.ansible.com/ansible/2.8/user_guide/playbooks_best_practices.html#alternative-directory-layout

Show inventory
````
ansible-inventory -i inventories/test --list
````

### Examples usage

For example tests inventory

Install key on remote hosts
```
ansible-playbook playbooks/upload-sshkey.yml -i inventories/test -u root -k -e username="root"
```

Ubuntu become (user sa)
````
ansible-playbook playbooks/docker.yml -i inventories/test/hosts.yml -l ubuntu.test.lab -u sa -K
````

Debian,Centos,Fedora (root)
````
ansible-playbook playbooks/docker.yml -i inventories/test/hosts.yml -l ubuntu.test.lab -u root
````

Check alive hosts
```
ansible -i inventories/test -m ping all -u root
```
