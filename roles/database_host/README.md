# Database Host

This role deploys a PostgreSQL database host. It can also deploy a hot standby server.

NOTE: this role incorrectly uses `postgres_` rather than `database_host_` as its prefix.
This is hold-over from it's original name. I will fix it in a future version!

## Usage

```
- role: fossgalaxy.infra.database_host
  vars:
    postgres_data_path: /var/lib/pgsql/data
    postgres_hba_path: "{{ postgres_data_path }}/pg_hba.conf"
    postgres_replica_password: "{{ vault_postgres_replica_pw }}"
```

### Replica

```
- role: fossgalaxy.infra.database_host
  vars:
    postgres_data_path: /var/lib/pgsql/data
    postgres_hba_path: "{{ postgres_data_path }}/pg_hba.conf"
    postgres_replica_password: "{{ vault_postgres_replica_pw }}"
    postgres_primary: db01.example.com
    postgres_is_standby: true
```
