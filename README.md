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
Now create variable file in **var** directory this file will have all the database credentials like username password and database name so we will use **Ansible VAULT** to encrypt this file.
```
$ cd var
$ ansible-vault create main.yml
PASSWORD: **PASSWORD TO SECURE THIS FILE**
RE-ENTER PASSWORD:  **PASSWORD TO SECURE THIS FILE**

# COPY THIS AND CHANGE THE CREDENTIALS
axelor: 
  - url: https://github.com/axelor/open-suite-webapp/releases/download/v5.4.7/axelor-erp-v5.4.7.war

postgresql_databases:
  - name: axelor
postgresql_users:
  - name: axelor
    password: axelor


# REWRITE CREDENTIALS
postgresql_database_app: axelor
postgresql_user_name: axelor
postgresql_user_password: axelor

```
RUN THE PLAYBOOK
```
$ ansible-playbook --
```
