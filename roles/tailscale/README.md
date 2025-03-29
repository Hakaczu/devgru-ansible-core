# Ansible Role: Tailscale

This Ansible role installs and configures Tailscale on target hosts and connects them to your Tailnet using an auth key.

## Requirements

- Supported operating systems:
  - Debian/Ubuntu
  - RHEL/CentOS/Fedora
  - macOS

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
# Path for Tailscale configuration
tailscale_path: "/etc/tailscale"

# Whether to authenticate immediately after installation
tailscale_auth_enabled: true

# Default Tailscale options 
tailscale_extra_flags: ""

# Access controls
tailscale_become: true
tailscale_become_user: root

# Package version - empty means latest
tailscale_package_version: ""
```

## Required Secret Variables

This role requires you to provide the following variable securely (using ansible-vault or a secrets manager):

```yaml
# Tailscale authentication key
tailscale_auth_key: "tskey-auth-xxx"
```

## Example Playbook

```yaml
- hosts: servers
  vars_files:
    - tailscale_secrets.yml  # Contains encrypted tailscale_auth_key
  roles:
    - tailscale
```

## Secure Usage With Ansible Vault

Create an encrypted file for your Tailscale auth key:

```bash
ansible-vault create tailscale_secrets.yml
```

Add your auth key to this file:

```yaml
tailscale_auth_key: "tskey-auth-xxxxx"
```

Then run your playbook with vault password:

```bash
ansible-playbook -i inventory playbook.yml --ask-vault-pass
```

## License

MIT