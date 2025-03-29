# Role: netghost

Creates an additional user `netghost` with full sudo privileges and SSH login capability.

## What it does:

- Creates the `netghost` account
- Adds it to the `sudo` group with `NOPASSWD:ALL`
- Sets the SSH key from the file `files/netghost.pub`
- Creates an entry in `/etc/sudoers.d/netghost`

## Usage:

```yaml
- hosts: all
  become: true
  roles:
    - netghost
```

## Important:

Make sure to add the public key file `netghost.pub` in the `files` directory before running the playbook. You can create the key as follows:

1. Generate an SSH key pair (if not already created):
   ```bash
   ssh-keygen -t rsa -b 4096 -C "netghost@example.com" -f netghost
   ```

2. Place the public key `netghost.pub` in the `files` directory of this role:
   ```bash
   mv netghost.pub /path/to/roles/netghost/files/
   ```