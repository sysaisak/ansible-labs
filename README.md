# Lab01: Debian 13 Hardening

This lab demonstrates configuring a Debian 13 Homelab with essential hardening measures using Ansible. It includes role-based automation for setting up `ufw` and `fail2ban`.

## Objective
- Automate basic hardening tasks: firewall (`ufw`) and intrusion prevention (`fail2ban`).

## Files and Structure
```
lab01/
├── group_vars                   # Group variables
│   └── homelab.yml              # Fail2ban settings and SSH port
├── inventory.ini                # Target hosts and variables
├── sun.yml                      # Main playbook
├── roles                        # Ansible role structure
│   └── hardening
│       ├── tasks
│       │   ├── main.yml         # Main task importer
│       │   └── ufw_fail2ban.yml # Tasks for `ufw` and `fail2ban`
│       ├── handlers
│       │   └── main.yml         # Handlers for restarting services
│       └── templates
│           └── jail.local.j2    # Template for Fail2ban jail config
```

## Highlights
- **Inventory**: Defines `homelab` group targeting Debian 13.
- **Group Vars**: `fail2ban` settings like `bantime`, `findtime`, and ignored IPs in `homelab.yml`.
- **Playbook**: `sun.yml` includes the `hardening` role for applying configurations.

## Role: hardening
- **Tasks**:
  - Install and configure `ufw` and `fail2ban`.
  - Deploy custom `jail.local` configuration.
- **Templates**:
  - `jail.local.j2` dynamically configures `fail2ban` using variables.
- **Handlers**:
  - Restarts `fail2ban` after configuration changes.
