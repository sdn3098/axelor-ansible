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
$ ansible-playbook --ask-vault-pass play.yml
```
# Directory Structure
```
axelor-ansible/
├── README.md
├── ansible.cfg
├── axelor
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── templates
│   │   └── application.j2
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── git
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   ├── main.yml
│   │   ├── setup-Debian.yml
│   │   └── setup-Redhat.yml
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── hosts
├── java
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   ├── main.yml
│   │   ├── setup-Debian.yml
│   │   └── setup-Redhat.yml
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
├── play.yml
├── postgres
│   ├── LICENSE
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── molecule
│   │   └── default
│   │       ├── converge.yml
│   │       └── molecule.yml
│   ├── tasks
│   │   ├── configure.yml
│   │   ├── databases.yml
│   │   ├── initialize.yml
│   │   ├── main.yml
│   │   ├── setup-Debian.yml
│   │   ├── setup-RedHat.yml
│   │   ├── users.yml
│   │   ├── users_props.yml
│   │   └── variables.yml
│   ├── templates
│   │   ├── pg_hba.conf.j2
│   │   └── postgres.sh.j2
│   └── vars
│       ├── Debian-10.yml
│       ├── Debian-7.yml
│       ├── Debian-8.yml
│       ├── Debian-9.yml
│       ├── Fedora-29.yml
│       ├── Fedora-30.yml
│       ├── Fedora-31.yml
│       ├── Fedora-32.yml
│       ├── RedHat-7.yml
│       ├── RedHat-8.yml
│       ├── Ubuntu-16.yml
│       ├── Ubuntu-18.yml
│       └── Ubuntu-20.yml
├── tomcat
│   ├── README.md
│   ├── defaults
│   │   └── main.yml
│   ├── handlers
│   │   └── main.yml
│   ├── meta
│   │   └── main.yml
│   ├── tasks
│   │   └── main.yml
│   ├── tests
│   │   ├── inventory
│   │   └── test.yml
│   └── vars
│       └── main.yml
└── vars
    └── main.yml

```
