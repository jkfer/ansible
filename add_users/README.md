# Add users to the systems and copy SSH keys

## Files:

#### user_vars.yml

Add user information here.

#### pubkeys/

Add the public keys to this folder. Key name format:
id.rsa.{{ username }}.pub

#### add_users.yml

Add users to the system.
Add sudo users to the wheel group.
Copy the user SSH keys from pubkeys/ to the designated destinations.
