Basic LAMP installation
=========

Prerequisite
------------

- expect ansible module is needed. install if not included in 'pip list'. (pip install pexpect)


#### Dependency Files:
- If copying data over for PHP and mysql DB, will include here


Other Notes
------------

- Vault and mysql pass set to '123456' for testing

Running
---------

- ansible-playbook lampstack.yml --ask-vault-pass
