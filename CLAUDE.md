# CLAUDE.md — ansible-automation-library

This file provides context for AI assistants (Claude, Copilot, etc.) working in this repository.

## Project Overview

**ansible-automation-library** is an open-source Ansible Collection containing production-ready
playbooks, roles, and plugins covering real-world IT automation scenarios — infrastructure
provisioning, configuration management, application deployment, and cloud operations.

- GitHub: https://github.com/iamgini/ansible-automation-library
- Ansible Galaxy: https://galaxy.ansible.com/ui/repo/published/iamgini/automation_library/
- Galaxy Namespace: `iamgini`
- Collection Name: `iamgini.automation_library`
- License: MIT

---

## Repository Structure

This repo follows the **Ansible Collection standard directory layout** so it can be published
directly to Ansible Galaxy.

```
ansible-automation-library/
├── galaxy.yml              # Collection metadata — version, description, dependencies
├── README.md               # Collection landing page
├── CHANGELOG.md            # Version history
├── LICENSE
├── playbooks/              # Flat directory — prefixed filenames for organisation
│   ├── linux_*.yml
│   ├── cloud_aws_*.yml
│   ├── cloud_azure_*.yml
│   ├── cloud_gcp_*.yml
│   ├── vmware_*.yml
│   ├── network_*.yml
│   ├── security_*.yml
│   ├── k8s_*.yml
│   ├── ocp_*.yml
│   ├── aap_*.yml
│   ├── db_*.yml
│   └── app_*.yml
├── roles/                  # Reusable Ansible roles
│   └── <role_name>/
│       ├── defaults/
│       ├── handlers/
│       ├── tasks/
│       ├── templates/
│       ├── vars/
│       ├── meta/
│       └── README.md
├── plugins/                # Custom Ansible plugins
│   ├── modules/
│   ├── filter/
│   ├── lookup/
│   └── callback/
├── docs/                   # Additional documentation
├── tests/                  # Molecule and integration tests
│   └── integration/
└── meta/                   # Collection-level metadata
    └── runtime.yml
```

---

## Playbook Naming Convention

Playbooks live in a **flat** `playbooks/` directory. Subdirectories are not supported in
Ansible Collections. Use filename prefixes to organise by category.

### Prefix Reference

| Prefix | Scope |
|---|---|
| `linux_` | General Linux — RHEL, Ubuntu, Fedora |
| `cloud_aws_` | Amazon Web Services |
| `cloud_azure_` | Microsoft Azure |
| `cloud_gcp_` | Google Cloud Platform |
| `vmware_` | VMware / vSphere |
| `network_` | Networking devices — Cisco, Juniper, etc. |
| `security_` | Hardening, compliance, patching |
| `k8s_` | Kubernetes |
| `ocp_` | OpenShift / OCP |
| `aap_` | Ansible Automation Platform |
| `db_` | Databases — MySQL, PostgreSQL, etc. |
| `app_` | Application deployment |

### Naming Pattern

```
<prefix>_<action>_<target>.yml
```

Examples:
```
linux_user_management.yml
linux_package_install.yml
cloud_aws_ec2_provision.yml
cloud_azure_vm_deploy.yml
vmware_vm_clone.yml
vmware_snapshot_create.yml
security_hardening_rhel.yml
k8s_namespace_setup.yml
ocp_project_onboarding.yml
aap_job_housekeeping.yml
db_postgresql_backup.yml
app_nginx_deploy.yml
```

---

## Playbook Style Guide

- Always include `name:` for every play and task — no unnamed tasks
- Use FQCN (Fully Qualified Collection Names) for all modules:
  - `ansible.builtin.copy` not `copy`
  - `ansible.builtin.template` not `template`
- Use `become: true` at task level only unless the entire play requires privilege escalation
- Avoid hardcoded values — use variables with defaults in `vars/` or role `defaults/main.yml`
- Every playbook must start with a header comment block:

```yaml
---
# Playbook   : <filename>
# Description: <what it does>
# Author     : Gineesh Madapparambath <gineesh.com>
# Usage      : ansible-playbook playbooks/<filename>.yml -i <inventory>
# Variables  :
#   var_name  : description (default: value)
```

---

## Role Conventions

- Follow standard Ansible role directory structure
- Prefix role variables with the role name: `webserver_port`, `db_backup_dir`
- Sensitive variables must use `no_log: true` — never hardcode secrets
- Every role must have a populated `README.md` with a usage example
- Molecule tests required for all roles before merging

---

## Variable Naming

- `snake_case` for all variable names
- Role variables prefixed with role name
- Collection-wide variables prefixed with `aal_` (ansible_automation_library)

---

## Plugin Conventions

- Custom modules go in `plugins/modules/`
- Use FQCN when referencing: `iamgini.automation_library.<module_name>`
- Every plugin must have a `DOCUMENTATION`, `EXAMPLES`, and `RETURN` block

---

## Versioning

- Semantic versioning: `MAJOR.MINOR.PATCH`
- `galaxy.yml` is the single source of truth for the version
- Update `CHANGELOG.md` with every release
- Tag releases in Git matching the version: `v1.0.0`

---

## Testing

```bash
# Lint all playbooks
ansible-lint playbooks/

# Lint entire collection
ansible-lint

# Run Molecule tests for a role
cd roles/<role-name>
molecule test

# Build collection tarball locally
ansible-galaxy collection build

# Install locally for testing
ansible-galaxy collection install iamgini-automation_library-*.tar.gz -p ./collections
```

---

## Publishing to Galaxy

```bash
# Build
ansible-galaxy collection build

# Publish
ansible-galaxy collection publish iamgini-automation_library-<version>.tar.gz --api-key <token>
```

---

## What This Repo Is NOT

- Not a tutorial repo — content must be production-quality, not step-by-step learning material
- Not vendor-locked — avoid hardcoding assumptions unless scoped clearly by filename prefix
- Not a dumping ground — every addition must solve a real, practical use case

---

## Contributing

- Open a GitHub Issue before submitting large PRs
- Follow the playbook naming convention and style guide above
- Add or update playbook header comment for every file
- Run `ansible-lint` before submitting — zero warnings expected

---

## Maintainer

**Gineesh Madapparambath**
- Web: https://gineesh.com
- Techbeatly: https://techbeatly.com
- GitHub: https://github.com/iamgini
