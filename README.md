# devgru-ansible-core

A collection of shared Ansible roles used in the `iac-cloud` and `iac-lan` projects.

## Contents

- `roles/docker` – installation and setup of Docker
- `roles/netghost` – configuration and deployment of NetGhost

## Usage

Add as a submodule:

```bash
git submodule add https://github.com/devgru/devgru-ansible-core.git ansible/roles
make init
```

