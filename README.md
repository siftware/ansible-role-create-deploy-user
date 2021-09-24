deploy-user
===========

This Ansible role will create a new user, for deployment use.

Role Variables
--------------

The following variables are used by this role. The default settings (found in `defaults/main.yml`) are as follows:

```yaml
# Name of the user to be created
deploy_user_name: deploy

# User group that the deploy_user will be added to
deploy_user_additional_groups:
  - www-data

# Base URL for obtaining public SSH keys
# Usage will be <key_server>/<user>.keys
deploy_user_key_server: https://gitlab.com

# List of users that will be able to SSH to the deploy_user account
deploy_user_ssh_users:
  - alice
  - bob

# List of additional public SSH keys. Useful for automated deployment systems
deploy_user_additional_ssh_keys: []

# Whether or not to allow the user to SSH back to itself
deploy_user_allow_self_ssh: false
```

Example Playbook
----------------

An example playbook of how to use the role.

```yaml
---

- hosts: all
  roles:
  - { role: deploy-user,
      deploy_user_name: deploy,
      deploy_user_additional_groups: [
        www-data
      ],
      deploy_user_key_server: 'https://gitlab.com',
      deploy_user_ssh_users: [
        alice,
        bob,
      ],
      deploy_user_additional_ssh_keys: [
        "ssh-rsa AAAAB3N.... foo@example.com"
      ],
      deploy_user_allow_self_ssh: false
    }
```

License
-------

MIT

Author Information
------------------

Written by Iain Cuthbertson of [Siftware Ltd](http://siftware.com/)
