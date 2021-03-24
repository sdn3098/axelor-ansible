# axelor-ansible
Download Playbook
```
$ git clone playbook address
```
Create a ansible config file in directory
```
$ cd axelor-ansible
$ vim ansible.cfg
[defaults]
inventory      = ./hosts
```
Create a Host file with **SERVERIP or HOSTNAME** 
```
$ vim host
[axelorprod]
server.example.com
```
