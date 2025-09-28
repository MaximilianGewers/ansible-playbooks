# Gewers Homelab Ansible Project

## Included content/ Directory Structure

The directory structure follows best practices recommended by the Ansible
community. Feel free to customize this template according to your specific
project requirements.

```
 ansible-project/
 |── .devcontainer/
 |    └── docker/
 |        └── devcontainer.json
 |    └── podman/
 |        └── devcontainer.json
 |    └── devcontainer.json
 |── .github/
 |    └── workflows/
 |        └── tests.yml
 |    └── ansible-code-bot.yml
 |── .vscode/
 |    └── extensions.json
 |── collections/
 |   └── requirements.yml
 |   └── ansible_collections/
 |       └── project_org/
 |           └── project_repo/
 |               └── README.md
 |               └── roles/sample_role/
 |                         └── README.md
 |                         └── tasks/main.yml
 |── inventory/
 |   |── hosts.yml
 |   |── argspec_validation_inventory.yml
 |   └── groups_vars/
 |   └── host_vars/
 |── ansible-navigator.yml
 |── ansible.cfg
 |── devfile.yaml
 |── maintenance.yml
 |── README.md
 |── site.yml
```

## Compatible with Ansible-lint

Tested with ansible-lint >=24.2.0 releases and the current development version
of ansible-core.

## Local testing

Ensure Docker is available locally, install the Molecule tooling with Docker support, and then execute the linux scenario:

```bash
python -m pip install --upgrade pip
python -m pip install ansible molecule "molecule-plugins[docker]"
ansible-galaxy collection install -r collections/requirements.yml --force
molecule test -s linux
```

## Available roles and playbooks

- `gewers.homelab.sync_github_ssh_key`: Syncs SSH public keys from a configurable GitHub profile into an account's
  `authorized_keys` file using the `ansible.posix.authorized_key` module.
- `gewers.homelab.update_linux_deps`: Applies package upgrades on Debian-based hosts, reboots when required, and
  optionally removes unused dependencies.
- `maintenance.yml`: Runs both roles against all non-network hosts (hosts not in the `switches` group) to keep SSH keys
  up to date and ensure operating systems receive routine package maintenance.
