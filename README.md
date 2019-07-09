# HTTPS reverse proxy

This Ansible role sets up a nginx server block and issues a certificate
for it using Letsencrypt. The certificate is set to be autorenewed every 3 months. The Nginx server block is just a reverse proxy to a service running on the provided localhost port.

## Required variables

- `domain_name`: The domain name for the server block which will be used as the domain name to issue a certificate for
- `site_name`: a user friendly name to use for the server block file
- `service_port`: specify which port on localhost to proxy the server block domain traffic to
- `certificate_contact_email`: the email to be used when issuing a certificate from Letsencrypt; it's needed for expiry notifications and security alerts;