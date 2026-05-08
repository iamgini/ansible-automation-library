# ansible-automation-library

> A curated library of production-ready Ansible playbooks, roles, and collections for real-world automation use cases — free and open source.

[![Ansible Galaxy](https://img.shields.io/badge/Ansible%20Galaxy-iamgini.automation__library-blue)](https://galaxy.ansible.com/ui/repo/published/iamgini/automation_library/)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![ansible-lint](https://img.shields.io/badge/ansible--lint-passing-brightgreen)](https://github.com/iamgini/ansible-automation-library)

---

## What Is This?

**ansible-automation-library** is an open-source Ansible Collection covering real-world IT automation scenarios across Linux, cloud, VMware, Kubernetes, OpenShift, and more.

Whether you are provisioning infrastructure, managing configurations, deploying applications, or hardening systems — this library has a playbook or role for it.

---

## Install

```bash
ansible-galaxy collection install iamgini.automation_library
```

Or install from GitHub directly:

```bash
ansible-galaxy collection install git+https://github.com/iamgini/ansible-automation-library.git
```

---

## What's Inside

| Category | Prefix | Examples |
|---|---|---|
| Linux | `linux_` | user management, package install, system config |
| AWS | `cloud_aws_` | EC2 provisioning, S3 buckets, VPC setup |
| Azure | `cloud_azure_` | VM deployment, resource groups |
| GCP | `cloud_gcp_` | Compute instances, GKE |
| VMware | `vmware_` | VM clone, snapshot, power management |
| Networking | `network_` | Cisco backup, interface config |
| Security | `security_` | RHEL hardening, compliance, patching |
| Kubernetes | `k8s_` | Namespace setup, deployments |
| OpenShift | `ocp_` | Project onboarding, operator config |
| AAP | `aap_` | Job templates, inventory sync, housekeeping |
| Databases | `db_` | PostgreSQL, MySQL backup and config |
| Applications | `app_` | Nginx, Apache, app deployment |

---

## Usage

```bash
# Run a playbook from the collection
ansible-playbook ~/.ansible/collections/ansible_collections/iamgini/automation_library/playbooks/linux_user_management.yml -i inventory/hosts.yml

# Or reference a role in your own playbook
- hosts: all
  roles:
    - iamgini.automation_library.<role_name>
```

---

## Requirements

- Ansible `>= 2.14.0`
- Python `>= 3.9`

Additional collection dependencies vary by playbook — see individual playbook headers.

---

## Contributing

Contributions are welcome! Please read the [Contributing Guide](docs/CONTRIBUTING.md) before submitting a PR.

- Follow the playbook naming convention: `<prefix>_<action>_<target>.yml`
- Include a header comment block in every playbook
- Run `ansible-lint` before submitting — zero warnings expected

---

## Author

**Gineesh Madapparambath**
- Website: [gineesh.com](https://gineesh.com)
- Blog: [techbeatly.com](https://techbeatly.com)
- GitHub: [@iamgini](https://github.com/iamgini)

---

## License

[MIT](LICENSE) — free to use, fork, and contribute.