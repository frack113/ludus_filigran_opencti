# Ansible Role: OpenCTI/OpenBAS Server

An Ansible Role that installs [OpenCTI](https://docs.opencti.io/latest/) and [OpenBAS](https://docs.openbas.io/latest/) for [LUDUS](https://ludus.cloud/).


Use the [XTM Docker Deployment docker](https://github.com/FiligranHQ/xtm-docker)

## Requirements

- Linux server
- Internet connection

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
ludus_filigran_opencti_MINIO_ROOT_PASSWORD: ChangeMe
ludus_filigran_opencti_RABBITMQ_DEFAULT_PASS: ChangeMe
ludus_filigran_opencti_POSTGRES_PASSWORD: ChangeMe
ludus_filigran_opencti_OPENSEARCH_ADMIN_PASSWORD: ChangeMe

ludus_filigran_opencti_SMTP_HOST: 'smtp.gmail.com'
ludus_filigran_opencti_SMTP_PORT: 587
ludus_filigran_opencti_SMTP_USERNAME: 'ChangeMe@domain.com'
ludus_filigran_opencti_SMTP_PASSWORD: ChangeMe
ludus_filigran_opencti_SMTP_AUTH: true
ludus_filigran_opencti_SMTP_SSL_ENABLE: true
ludus_filigran_opencti_SMTP_STARTTLS_ENABLE: false

ludus_filigran_opencti_IMAP_HOST: 'imap.changeme.com'
ludus_filigran_opencti_IMAP_PORT: 993
ludus_filigran_opencti_IMAP_USERNAME: 'ChangeMe@domain.com'
ludus_filigran_opencti_IMAP_PASSWORD: ChangeMe
ludus_filigran_opencti_IMAP_AUTH: true
ludus_filigran_opencti_IMAP_SSL_ENABLE: true
ludus_filigran_opencti_IMAP_STARTTLS_ENABLE: false

ludus_filigran_opencti_OPENCTI_ADMIN_EMAIL: 'admin@opencti.io'
ludus_filigran_opencti_OPENCTI_ADMIN_PASSWORD: ChangeMe
ludus_filigran_opencti_OPENCTI_ADMIN_TOKEN: '3f752a3b-b4b6-44d0-bb80-ff3807469164'
ludus_filigran_opencti_OPENCTI_HEALTHCHECK_ACCESS_KEY: ChangeMe

ludus_filigran_opencti_PENAEV_ADMIN_EMAIL: 'ChangeMe@domain.com'
ludus_filigran_opencti_OPENAEV_ADMIN_PASSWORD: ChangeMe
ludus_filigran_opencti_OPENAEV_ADMIN_TOKEN: 3f4dc0cf-eff8-4f6a-aec7-07e6566931ef
ludus_filigran_opencti_OPENAEV_HEALTHCHECK_KEY: ChangeMe
ludus_filigran_opencti_OPENAEV_MAIL_IMAP_ENABLED: false

ludus_filigran_opencti_COLLECTOR_NVD_NIST_CVE_API_KEY: ''
```

## Dependencies

Ansible :

- community.docker
- geerlingguy.docker

## Example Playbook

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-OpenCTI"
    hostname: "{{ range_id }}-OpenCTI"
    template: ubuntu-24.04-x64-server-template
    vlan: 99
    ip_last_octet: 2
    ram_gb: 12
    cpus: 4
    linux: true
    roles:
      - frack113.ludus_filigran_opencti
    role_vars:
      ludus_filigran_opencti_OPENCTI_ADMIN_EMAIL: 'admin@ludus.io'
      ludus_filigran_opencti_PENAEV_ADMIN_EMAIL: 'admin@ludus.io'
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [frack113](https://github.com/frack113), for [Ludus](https://ludus.cloud/).
