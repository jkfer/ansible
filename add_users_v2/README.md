# Add users to the systems and copy SSH keys

## Files:

#### user_vars.yml
Add user information here.

#### create_new_users.yml

Add users to the system.

Add sudo users to the wheel group.

Create the private and public keys for the new users

Ensure the /home/{{ item.username }}/.ssh folder is created with the correct permissions

Copy the user public SSH keys of the new users to the designated destinations on remote hosts

Ensure public key authentication is enabled in all hosts

reload sshd service
