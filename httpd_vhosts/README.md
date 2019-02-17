Basic Vhost deployment on remote server(s)
==========================================

## This playbook sets up a basic virtual host on the target servers. Servers will be accessible using the set vhost name  <hostname>
### Test using http://<ip> or http://<hostname>

# Pre-requisites and assumtions:
- Target server OS: CentOS or RedHat

## Jinja2 templates for dynamic vhost naming
- vhosts.conf.j2
- index.html.j2

