# Ansible Role: Forgejo

This Ansible role installs and configures Forgejo, a self-hosted Git service and GitHub/GitLab alternative, using Docker containers. Forgejo is a community-owned fork of Gitea.

## Requirements

- **Docker**: This role requires Docker to be installed on the target host. The role will check for Docker and fail if not found.
- **Root access** (become: true)

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yaml`):

```yaml
# Installation directory for Forgejo
forgejo_path: /opt/containers/forgejo

# HTTP port mapping (host:container)
forgejo_port_http: 3000

# SSH port mapping (host:container)
forgejo_port_ssh: 2222
```

## Dependencies

- Docker role should be applied first

## Example Playbook

```yaml
- hosts: git_servers
  become: true
  roles:
    - docker
    - forgejo
```

## Role Tasks

This role performs the following tasks:

1. Checks if Docker is installed on the target host
2. Creates a directory for Forgejo configuration and data
3. Deploys a docker-compose.yml file from a template
4. Starts the Forgejo container using docker-compose

## Data Persistence

The role configures a named Docker volume (`forgejo_data`) to persist Forgejo's data between container restarts.

## License

MIT