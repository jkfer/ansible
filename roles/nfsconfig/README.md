Role Name
=========

Share a directory to clients using NFS.

- NFS Installation takes distribution into consent - RedHat/CentOS vs Debian
- Assuming firewall does not block the NFS reachability
---- configuration of firewall can be extended upon
- This is a basic fileshare sharing one folder to all clients. Can be extended on:
---- Shared to specific domain
---- Group access control: Access to NFS be granted only to members of specific group


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Inventory Groups:
nfs_server: One host to provide the newtwork file share location to clients
nfs_client: Hosts readily available to access the network files share. Shared directory to be mounted here.

Server/client distribution to be RedHat/CentOS/Debian

Role Variables
--------------

In nfsconfig/vars/main.yml
nfs_share: Folder location in nfs_server that is to be shared to the clients
nfs_mountpoint: Mount point in nfs clients

In Playbook:
type: "server" or "client". Defined within the play to recognize server/client roll-out


Dependencies
------------

Jinja template for nfs_server: nfsconfig/templates/exports.j2
Handlers in nfsconfig/handlers/main.yml: Hnadler to restart NFS services


Example Playbook
----------------

- hosts: nfs_server
  user: test
  become: yes
  become_method: sudo
  gather_facts: yes
  vars:
    - type: "server"
  roles:
    - nfsconfig
  tasks:
    - name: Assigning NFS Server name to a variable
      set_fact:
        NFS_Server: "{{ ansible_nodename }}"

- hosts: nfs_client
  user: test
  become: yes
  become_method: sudo
  gather_facts: yes
  vars:
    - type: "client"
    - NFSServer: "{{hostvars[groups['nfs_server'][0]]['NFS_Server']}}"
  roles:
    - nfsconfig


