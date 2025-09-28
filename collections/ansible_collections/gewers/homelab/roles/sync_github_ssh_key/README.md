Sync GitHub SSH Key Role
========================

This role synchronizes a GitHub user's SSH public keys into the `authorized_keys` file of a target account. It fetches the
keys directly from the GitHub API using Ansible's `url` lookup and ensures they are present by leveraging the
`ansible.posix.authorized_key` module.

Requirements
------------

The managed hosts must have an existing user account that can accept the configured SSH public keys.

Role Variables
--------------

The role exposes the following variables which can be overridden as needed:

- `sync_github_ssh_key_user`: Target user account whose `authorized_keys` file will be managed. Defaults to `toor`.
- `sync_github_ssh_key_source_url`: URL used to retrieve the SSH public keys. Defaults to the GitHub keys endpoint for
  `maximiliangewers`.

Dependencies
------------

This role has no external role dependencies. Ensure the `ansible.posix` collection is available on the control node so the
`authorized_key` module can be executed.

Example Playbook
----------------

```yaml
- name: Sync GitHub SSH keys for homelab administrators
  hosts: homelab
  roles:
    - role: gewers.homelab.sync_github_ssh_key
      vars:
        sync_github_ssh_key_user: toor
        sync_github_ssh_key_source_url: https://github.com/maximiliangewers.keys
```

License
-------

BSD

Author Information
------------------

Maintained by the Gewers homelab automation team.
