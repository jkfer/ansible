Role Name
=========

#### Share a directory to clients using NFS.

- NFS Installation takes distribution into consent - RedHat/CentOS vs Debian
- Assuming firewall does not block the NFS reachability
-- configuration of firewall can be extended upon
- This is a basic fileshare sharing one folder to all clients. Can be extended on:
-- Shared to specific domain
-- Group access control: Access to NFS be granted only to members of specific group


Requirements
------------

#### Inventory Groups:
- nfs_server: One host to provide the newtwork file share location to clients
- nfs_client: Hosts readily available to access the network files share. Shared directory to be mounted here.

Server/client distribution to be RedHat/CentOS/Debian

Role Variables
--------------

#### In nfsconfig/vars/main.yml
- nfs_share: Folder location in nfs_server that is to be shared to the clients
- nfs_mountpoint: Mount point in nfs clients

#### In Playbook:
- type: "server" or "client". Defined within the play to recognize server/client roll-out


Dependencies
------------

- Tested on Ansible 2.6 only

- Jinja template for nfs_server: nfsconfig/templates/exports.j2
- Handlers in nfsconfig/handlers/main.yml: Hnadler to restart NFS services


Example Playbook
----------------

See ../nfsconfig.yml for sample playbook.
