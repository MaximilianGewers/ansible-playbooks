# Add GitHub SSH Keys to a Server

This playbook pulls the public keys that are published on a GitHub account and adds them
to a user's `authorized_keys` file. It is a quick way to bootstrap passwordless SSH
access for yourself or other trusted operators on a fresh machine.

## What it does
- Downloads the `*.keys` listing from the specified GitHub profile.
- Ensures those keys are present for the configured system user via
  `ansible.posix.authorized_key`.

## Requirements
- The target host must already have the user account (defaults to `toor`).
- Outbound HTTPS access from the control node to `github.com`.
- Privilege escalation on the managed host if the target user owns protected files.

## Usage
1. Edit `main.yaml` and set the `user` and `key` values to match the target account and
   GitHub profile you want to authorize.
2. Run the playbook against your inventory:
   ```bash
   ansible-playbook -i inventory.ini playbooks/add-github-ssh-to-server/main.yaml
   ```
