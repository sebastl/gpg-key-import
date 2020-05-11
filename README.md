GPG key import
=========

Importing a gpg key to a specific host.

## Features

- Tests if your gpg key is present
- Easy to use: you have only to supply your key files
- Idempotency is present in all actions
- Key is added to a specific user

Requirements
------------
Before running the role you should update `defaults/main.yml` with your personal informations and add your gpg key in `files/`.

### How to add the gpg keys
- public.key -> `gpg -a --export username@email > files/public.key`

- secret.key -> `gpg -a --export-secret-keys username@email > files/secret.key`

- ownertrust.txt -> `gpg --export-ownertrust > files/ownertrust.txt`

Role Variables
--------------
`gpg_user`: Name of the user <br />
`gpg_system_user`: Whether the user shall be a system user instead of a regular user (default: yes) <br />
`gpg_group`: Name of the group <br />
`gpg_system_group`: Whether the group shall be a system group instead of a regular group (default: yes) <br />
`gpg_email`: Email of the gpg key <br />
`gpg_home`: Where the GPG home directory will be located <br />
`gpg_pubkey_path`: Custom path to GPG public key <br />
`gpg_seckey_path`: Custom path to GPG private key <br />
`gpg_trustfile_path`: Custom path to GPG ownertrust file

Dependencies
------------

The role is modular and has no dependencies

Example Playbook
----------------
```
   - hosts: reposerver
     become: yes
     vars:
        gpg_user: repo_user
        gpg_group: repo_group
        gpg_email: repo@mail.com
        gpg_home: /var/lib/repo
     roles:
        - role: gpg_key_import
```

License
-------
MIT

Author Information
------------------
Alexis Miles Oortmann (@MisterMiles) <mister_dev@mailbox.org>
