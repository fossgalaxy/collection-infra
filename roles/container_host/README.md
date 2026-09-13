# Container Host

This role is designed to deploy a Podman container host.

## Usage

```
- hosts: appservers
  roles:
    - role: fossgalaxy.infra.container_host
```

You'll probably want a reverse proxy to make it useful. We can deploy Traefik using the `fossgalaxy.infra.traefik` role.
