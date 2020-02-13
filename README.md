# HTTPS reverse proxy

This Ansible role sets up a nginx server block and issues a certificate
for it using Letsencrypt. The certificate is set to be autorenewed every 3 months. The Nginx server block is just a reverse proxy to a service running on the provided host and port.

# Requirements

The role currently supports only Ubuntu

# Installation

Use Ansible Galaxy:

```sh
ansible-galaxy install zbrox.https_reverse_proxy
```

# Usage

In order to use the role just include it in your playbook, for example like this:

```ansible
    roles:
        - role: zbrox.https_reverse_proxy
          https_reverse_proxy_domain_name: example.com
          https_reverse_proxy_site_name: my_example_site
          https_reverse_proxy_service_port: 12345
          https_reverse_proxy_certificate_contact_email: me@example.com
```

## Required variables

- `https_reverse_proxy_domain_name`: The domain name for the server block which will be used as the domain name to issue a certificate for
- `https_reverse_proxy_site_name`: a user friendly name to use for the server block file
- `https_reverse_proxy_service_port`: specify which port on localhost to proxy the server block domain traffic to
- `https_reverse_proxy_certificate_contact_email`: the email to be used when issuing a certificate from Letsencrypt; it's needed for expiry notifications and security alerts;

## Optional variables

- `https_reverse_proxy_service_host`: the default value is `localhost`; you can specify this in order to proxy the traffic to some other host instead

# License

MIT