# Traefik Role

This role deploys a Traefik container for use by other containers.

```
- hosts: appservers
  roles:
    - role: fossgalaxy.infra.traefik
      vars:
        traefik_https_provider: freeipa
        traefik_manage_firewalld: false
```
