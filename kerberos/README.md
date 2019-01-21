Basic Kerberos Server and Cient Configuration
=========

Prerequisite
------------

- The ansible playbooks kerb_server.yml and kerb_client.yml are designed to work over CENTOS
- Need pre-configured kerberos configuration files
- expect ansible module is needed

#### Dependency Files:
- kadm5.acl
- kdc.conf
- krb5.conf
- users_list.txt (list of users for kerberos principles)


Other Notes
------------

- Kadmin password, vault password and all user passwords are defaulted to '123456' by using ansible vault. prompt variables can be used to dynamicaly input the passwords
- For readability, usability and demonstration the playbook is created as is
- For an optimum situation the playbook itsellf is best created with ansible vault due to the passwords involved

Running
---------

- ansible-playbook kerb_server.yml --ask-vault-pass
- ansible-playbook kerb_client.yml --ask-vault-pass
