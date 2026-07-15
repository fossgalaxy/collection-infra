# Create a managed PostgreSQL database

This role is designed to be used by other roles.

## Usage Example

This role is designed to be embedded in other roles:

```
- name: "podman_postgres | Ensure DB exists"
  no_log: true
  ansible.builtin.include_role:
    name: "fossgalaxy.infra.postgres_db"
    tasks_from: ensure_db.yml
  vars:
    pg_host: "psql.example.com"
    pg_db: "appname"
    pg_owner: "appname_admin"
    pg_app_user: "appname_app"
    pg_app_password: "PASSWORD HERE"
    pg_app_inherits_owner: true
```


Many other services we deploy use this role. It should be possible to use this without using the `database_server` role, as it depends on psql utilities
on the database server. It is not designed to be used with containerised PostgreSQL servers.

### Owner inheritance
Although the playbook is designed to support an `owner` and `app` account setup, if your app expects to functionally be a (database) owner account
`pg_app_inherits_owner` can be used to grant it the same rights as the owner.
