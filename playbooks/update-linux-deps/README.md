# Update Linux Dependencies and Reboot if Needed

Keeps Debian- and Ubuntu-based systems current by applying package upgrades, rebooting
only when the kernel requests it, and cleaning up orphaned dependencies afterwards.

## What it does
- Runs `apt dist-upgrade` with the package cache refreshed.
- Checks `/var/run/reboot-required` to determine whether a restart is necessary.
- Reboots the host when required to apply kernel or libc updates.
- Removes unused dependencies with `apt autoremove`.

## Requirements
- Managed hosts must use `apt` (tested with Debian/Ubuntu derivatives).
- Privilege escalation enabled for package management and reboot tasks.
- Maintenance windows that allow for automated reboots when required.

## Usage
```bash
ansible-playbook -i inventory.ini playbooks/update-linux-deps/main.yaml
```

## Customization tips
- Limit the play to a host group (for example `--limit webservers`) to stagger upgrades.
- Add notifications to chat/monitoring tooling by extending the handler section after the
  reboot task.
- Tweak the `apt` tasks to pin package versions or skip kernel updates if needed.
