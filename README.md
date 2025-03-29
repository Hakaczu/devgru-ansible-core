# devgru-ansible-core

A collection of shared Ansible roles used in the `iac-cloud` and `iac-lan` projects.

## Contents

- `roles/docker` – Installation and setup of Docker, including optional tools like LazyDocker.
- `roles/netghost` – Configuration and deployment of NetGhost.
- `roles/forgejo` – Deployment of Forgejo with Docker Compose.
- `roles/tailscale` – Installation and configuration of Tailscale.

## Prerequisites

- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) installed on your system.
- Access to the required repositories and permissions to add submodules.

## Usage

### Adding as a Submodule

To include this repository as a submodule in your project, run the following command:

```bash
git submodule add https://github.com/devgru/devgru-ansible-core.git ansible/roles
make init
```

### Using Roles

Each role is self-contained and can be included in your Ansible playbooks. For example:

```yaml
- name: Setup Docker
  hosts: all
  roles:
    - role: docker

- name: Configure Tailscale
  hosts: all
  roles:
    - role: tailscale
```

Refer to the `README.md` files within each role directory for detailed usage instructions and available variables.

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a feature branch.
3. Commit your changes with clear messages.
4. Submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

