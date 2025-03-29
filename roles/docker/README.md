# Ansible Role: Docker

This Ansible role installs and configures Docker Community Edition (CE) and Docker Compose on target hosts. It also provides an option to install LazyDocker, a terminal UI for Docker.

## Requirements

- Supported operating systems:
  - Debian/Ubuntu
- Root access (become: true)

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Whether to install LazyDocker
install_lazydocker: true
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: servers
  become: true
  roles:
    - docker
```

## Role Tasks

This role performs the following tasks:

1. Installs Docker CE dependencies
2. Adds Docker's official GPG key
3. Adds the Docker CE repository
4. Installs Docker CE, CLI and containerd
5. Installs Docker Compose plugin 
6. Enables and starts the Docker service
7. Adds the user to the docker group for non-root access
8. Optionally installs LazyDocker if `install_lazydocker` is set to true

## LazyDocker

[LazyDocker](https://github.com/jesseduffield/lazydocker) is a simple terminal UI for Docker, helping you manage containers, images, and volumes with ease.

## License

MIT