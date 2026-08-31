# Traefik Reverse Proxy
The playbook can manage the traefik reverse proxy as part of its configuration.

## TLS support

* `traefik_https` controls if traefik will expose HTTPS ports

This is done using system sockets.

Traefik will need the certificates to use. Although it has the ability to fetch these itself, this playbook
assumes that traefik is not being exposed publicaly (ie, is on an internal network or behind a reverse proxy).

Instead, it will bind the hosts `/etc/pki/tls/private` directory inside the container to provide the certificates.
You can override this by setting `traefik_tls_dir` to another directory.

### FreeIPA integration
The playbook can generate and fetch HTTPS certs from FreeIPA if enabled.

The account used to fetch/setup certificates is defined by:

* `traefik_ipa_admin_user`
* `traefik_ipa_admin_pass`

These will default to `ipaadmin_principal` and `ipaadmin_password` if set.

#### Certificate hosts
FreeIPA is quite strict on what hostnames a server can fetch certificates for by default.

* `traefik_https_hostname` is the default certificate host, it will default to the inventory hostname do not change this unless you know what you are doing
* `traefik_https_certifcates` is a dictionary which defines the additional hostnames to fetch

```yaml
traefik_https_certificates:
  - hostname: "app.example.com"
  - hostname: "otherapp.example.com"
```

Fetched certificates will be stored inside `/etc/pki/tls/private/`

