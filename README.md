deploy-user
===========

This Ansible role will create a new user, for deployment use.

Role Variables
--------------

The following variables are used by this role. The default settings (found in `defaults/main.yml`) are as follows:

```yaml
---

# Name of the user to be created
deploy_user: deploy

# User group that the deploy_user will be added to
httpd_user: www-data

# Base URL for obtaining public SSH keys
# Usage will be <key_server>/<user>.keys
key_server: https://code.siftware.com

# List of users that will be able to SSH to the deploy_user account
ssh_users:
  - ashleyhindle
  - iain
  - stephen
```

Example Playbook
----------------

An example playbook of how to use the role.

```yaml
---

- hosts: all
  roles:
  - { role: deploy-user,
      deploy_user: deploy,
      httpd_user: www-data,
      key_server: 'https://code.siftware.com',
      ssh_users: [
        ashleyhindle,
        iain,
        stephen,
      ]
    }
```

License
-------

MIT

Author Information
------------------

Written by Iain Cuthbertson of [Siftware Ltd](http://siftware.com/)
