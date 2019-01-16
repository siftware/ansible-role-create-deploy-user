deploy-user
===========

This Ansible role will create a new user, for deployment use.

Role Variables
--------------

The following variables are used by this role. The default settings (found in `defaults/main.yml`) are as follows:

```yaml
# Name of the user to be created
deploy_user: deploy

# User group that the deploy_user will be added to
httpd_user: www-data

# Base URL for obtaining public SSH keys
# Usage will be <key_server>/<user>.keys
key_server: https://code.siftware.com

# List of users that will be able to SSH to the deploy_user account
ssh_users:
  - bealers
  - iain
  - Kalaitzis

# Whether or not to install the public SSH key for Siftware's Jenkins CI server
deploy_user_add_jenkins_ssh_key: true

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
      deploy_user: deploy,
      httpd_user: www-data,
      key_server: 'https://code.siftware.com',
      ssh_users: [
        bealers,
        iain,
        Kalaitzis
      ],
      deploy_user_additional_ssh_keys: [
        "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDYM4DgLfa0XaA7ZhtbVlRybyZ+u1awfBW9LY6EzkeDUszDYs1or2sQeAZXLINV9Ha/HXklxEjvb1BmPcmeavYRMsQ0ctOC2x3Cft4v3VuI46ORtaFk5C1uliDmo4kkts19lPIMa53UjSrlKcpWiRTZxaTZhkY8CJbGXR/0UYYzs1LLRcMiyq1Rh1pWj3pKrRInKcnRyKmWTfkcxU+uMjJoP2GZCyl8KgmQOOn10Uh0QB9TtL3DcJWsAmAQuRrQjrdpWPpbhgCB6t2jElOB7cXQNYvStHtZcA8K3jhTyN+qYmm7uiJtt60UhKRHITejwrqsjcdnGQBrLx4bOjE6Zo4/ jenkins@code.siftware.net"
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
