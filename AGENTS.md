# Summary
- Automates home network maintenance with Ansible playbooks for SSH key management and system updates.

# Repo structure
- `playbooks/` — Individual playbooks and documentation for each automation task.
  - `add-github-ssh-to-server/` — Adds a GitHub public key to servers' `authorized_keys`.
  - `update-linux-deps/` — Upgrades packages, reboots when needed, and cleans dependencies.

# Development
- Stick to YAML best practices: two-space indents, lowercase module names, and document tasks with descriptive `name` fields.
- Keep playbooks idempotent; prefer Ansible modules over shell commands whenever possible.
- Update or add accompanying `README.md` files whenever you change playbook behavior.
- Use variables for user-specific values (e.g., GitHub usernames, package lists) instead of hardcoding them.

# Testing
- Validate syntax with `ansible-playbook <playbook>/main.yaml --syntax-check` before committing.
- For playbooks with dependencies, dry-run with `--check` against a staging inventory if feasible.

# Commit & PR workflow
- Use [Conventional Commits](https://www.conventionalcommits.org/) for every commit message (e.g., `feat: add system update playbook`).
- Squash or amend local commits to maintain clean history before opening a PR.
- PR titles should also follow the Conventional Commit format and summarize the change at a high level.
- In PR descriptions, summarize functional changes, mention affected playbooks, and note any new variables or inventory requirements.

# Additional context
- Target hosts generally require privilege escalation; confirm `become` configuration when adding tasks.
- Document manual steps or prerequisites in each playbook's README to keep operations reproducible.
