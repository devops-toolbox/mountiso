Role Name
=========

mountiso: Mountiso

[![Build Status](https://travis-ci.org/cmihai-ansible/mountiso.svg?branch=master)](https://travis-ci.org/cmihai-ansible/mountiso)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.mountiso](https://galaxy.ansible.com/devops-toolbox.mountiso)

```bash
ansible-galaxy install devops-toolbox.mountiso
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
mountiso_packages_state: present
mountiso_remove_packages: true
mountiso_enable_service: true
mountiso_enable_selinux: true
mountiso_copy_templates: true
mountiso_firewall_configure: true
mountiso_firewall_rules:
  - service: ssh
  - port: 3389
mountiso_users:
  - user: devops
    group: docker
mountiso_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install mountiso on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: mountiso is configured
      import_role:
        name: devops-toolbox.mountiso
      vars:
        mountiso_packages_state: present
        mountiso_remove_packages: true
        mountiso_enable_service: true
        mountiso_enable_selinux: true
        mountiso_copy_templates: true
        mountiso_firewall_configure: true
        mountiso_firewall_rules:
          - service: ssh
          - port: 3389
        mountiso_users:
          - user: devops
            group: docker
        mountiso_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: mountiso
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
