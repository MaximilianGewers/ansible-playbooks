# Ansible Playbooks

Automation recipes for repeatable home lab maintenance tasks. Each playbook targets a
specific bit of day-to-day server administration, such as keeping systems patched or
bootstrapping SSH access for new machines.

## Requirements
- [Ansible](https://docs.ansible.com/) 2.12 or newer on the control node.
- SSH access to the managed hosts (usually with privilege escalation enabled).
- An inventory file describing the hosts you want to target.

## Repository layout
- `playbooks/add-github-ssh-to-server/` – Grants a server login user the public keys
  published on a GitHub account.
- `playbooks/update-linux-deps/` – Runs unattended package upgrades and reboots hosts if
  the kernel requests it.

## Usage
1. Update your Ansible inventory so it includes the hosts you want to manage.
2. From the repository root, run the desired playbook. For example:
   ```bash
   ansible-playbook -i inventory.ini playbooks/update-linux-deps/main.yaml
   ```
3. Review the output and logs to confirm the tasks completed successfully.

See each playbook directory for playbook-specific variables, prerequisites, and optional
post-run steps.
