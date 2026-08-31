# PostgreSQL Configuration

## Replication
The PostgreSQL role is designed to support simple replication between an active server and a backup out of the box.

* `postgres_replica_password` the password for the replication

## TLS integration

## FreeIPA
The role is primarily designed to be used on a FreeIPA enrolled host. If enabled, it can fetch TLS certs from your FreeIPA server.
If you have not enabled FreeIPA, the TLS integration will be disabled (as it does not know how to get the certificates).

* `postgres_freeipa`

To fetch the certificates, we need a suitable account. By default, these will try to use the FreeIPA admin vars, but can be changed
to a different user if needed.

* `postgres_freeipa_admin_user`
* `postgres_freeipa_admin_pass`

