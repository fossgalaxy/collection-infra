# Valkey Role

This role deploys a [Valkey](https://valkey.io/) container for use by other containers.

## Usage

This role is most useful when used by other roles that want a Redis-style cache.

For example for the `foobaz` service, it might look something like this:

```yaml
- name: Ensure valkey container exists
  no_log: true
  ansible.builtin.include_role:
    name: "fossgalaxy.infra.valkey"
  vars:
    valkey_service: "foobaz_valkey"
    valkey_network: "foobaz.network"
    valkey_systemd_dir: "/srv/podman/foobaz/"
```

