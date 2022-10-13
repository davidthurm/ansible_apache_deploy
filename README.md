# ansible_apache_deploy
```
ansible-playbook -i hosts -l centos main.yml 
ansible-playbook -i hosts -l rocky main.yml 
```
# The Playbook
```
---
- hosts: [centos]
  become: yes
  tasks:
        - name: install apache
          yum: name=httpd state=present

        - name: Enable service httpd and ensure it is not masked
          ansible.builtin.systemd:
            name: httpd
            enabled: yes
            state: started
            masked: no
```

# The Hosts File
```
## Change the IP and Path to your Private key.
[centos]
52.90.245.157 ansible_user=centos ansible_ssh_private_key_file=/root/PatchesTheDog.pem
3.88.217.153 ansible_user=centos ansible_ssh_private_key_file=/root/PatchesTheDog.pem

[rocky]
52.70.141.219 ansible_user=rocky ansible_ssh_private_key_file=/root/PatchesTheDog.pem
```
