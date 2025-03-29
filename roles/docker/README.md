# Role: docker

The `docker` role installs and runs Docker along with LazyDocker on Debian/Ubuntu-based systems.

## What it does:

- Installs the `docker.io` package
- Enables and starts the `docker` service
- Installs `lazydocker` (a TUI interface for Docker)
  - Downloads the binary from GitHub Releases
  - Extracts it to `/usr/local/bin/`
  - Sets appropriate permissions

## Requirements:

- Works on systems with `apt` (Debian, Ubuntu, Alpine with `apt` will not work)
- Requires `become: true` privileges (sudo/root)

## Usage:

```yaml
- hosts: all
  become: true
  roles:
    - docker