Description
===========

This role installs apache on target hosts. Creates a virtual host on <hostname>.


Requirements
------------

Target hosts OS: RedHat or Cent OS

Role Variables
--------------

Some variables used within the tasks to find HTTPD status and also in the templates to include hostname.

Dependencies
------------

templates/index.html.j2  - Jinja template for webserver index page.
templates/vhosts.conf.j2 - Virtual host configuration file

Example Playbook
----------------

    - hosts: servers
      gather_facts: yes
      vars:
        web_server_name: "{{ ansible_nodename }}"
      roles:
        - webdeploy

