# Ansible Collection - fossgalaxy.infra

These are roles designed to make deploying key services required by our other playbooks easier.

## Services

* `container_host` sets a host up as a Podman server
* `database_host` sets a PostgreSQL server up (designed to be used on a VM/bare metal server)
* `traefik` will create a reverse proxy which can be used to access deployed containers (designed to be used with `container_host`)

## Utilities

* `postgres_db` can be used to manage a PostgreSQL database
* `keycloak_client` can be used to auto-provision a Keycloak OIDC client.
