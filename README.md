# Ansible Role: OpenCTI/OpenBAS Server

An Ansible Role that installs [OpenCTI](https://docs.opencti.io/latest/) and [OpenAEV](https://docs.openaev.io/latest/) for [LUDUS](https://ludus.cloud/).


Use the [XTM Docker Deployment](https://github.com/FiligranHQ/xtm-docker)

⚠️ check memory requirements

## Requirements

- Linux server
- Internet connection

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
ludus_filigran_opencti_ELASTIC_MEMORY_SIZE: 4G

ludus_filigran_opencti_MINIO_ROOT_PASSWORD: d8b68174-f25e-4f42-af24-a902c62cb241
ludus_filigran_opencti_RABBITMQ_DEFAULT_PASS: guest
ludus_filigran_opencti_POSTGRES_PASSWORD: ChangeMe
ludus_filigran_opencti_OPENSEARCH_ADMIN_PASSWORD: ChangeMe

ludus_filigran_opencti_SMTP_HOST: localhost
ludus_filigran_opencti_SMTP_PORT: 587
ludus_filigran_opencti_SMTP_USERNAME: 'ChangeMe@domain.com'
ludus_filigran_opencti_SMTP_PASSWORD: ChangeMe
ludus_filigran_opencti_SMTP_AUTH: true
ludus_filigran_opencti_SMTP_SSL_ENABLE: true
ludus_filigran_opencti_SMTP_STARTTLS_ENABLE: false

ludus_filigran_opencti_IMAP_HOST: localhost
ludus_filigran_opencti_IMAP_PORT: 993
ludus_filigran_opencti_IMAP_USERNAME: 'ChangeMe@domain.com'
ludus_filigran_opencti_IMAP_PASSWORD: ChangeMe
ludus_filigran_opencti_IMAP_AUTH: true
ludus_filigran_opencti_IMAP_SSL_ENABLE: true
ludus_filigran_opencti_IMAP_STARTTLS_ENABLE: false

ludus_filigran_opencti_OPENCTI_ADMIN_EMAIL: 'admin@opencti.io'
ludus_filigran_opencti_OPENCTI_ADMIN_PASSWORD: ChangeMePlease
ludus_filigran_opencti_OPENCTI_ADMIN_TOKEN: 3f752a3b-b4b6-44d0-bb80-ff3807469164
ludus_filigran_opencti_OPENCTI_HEALTHCHECK_ACCESS_KEY: 1b7f65f9-65c9-4391-93e0-5a92a4852c20

ludus_filigran_opencti_OPENAEV_ADMIN_EMAIL: 'admin@opencti.io'
ludus_filigran_opencti_OPENAEV_ADMIN_PASSWORD: ChangeMePlease
ludus_filigran_opencti_OPENAEV_ADMIN_TOKEN: 3f4dc0cf-eff8-4f6a-aec7-07e6566931ef
ludus_filigran_opencti_OPENAEV_HEALTHCHECK_KEY: 1b7f65f9-65c9-4391-93e0-5a92a4852c20
ludus_filigran_opencti_OPENAEV_MAIL_IMAP_ENABLED: false

ludus_filigran_opencti_COLLECTOR_NVD_NIST_CVE_API_KEY: ''

ludus_filigran_opencti_INJECTOR_CALDERA_ENABLE: false
ludus_filigran_opencti_INJECTOR_CALDERA_URL: http://caldera:8888
ludus_filigran_opencti_INJECTOR_CALDERA_PUBLIC_URL: http://caldera:8888
ludus_filigran_opencti_INJECTOR_CALDERA_API_KEY: Qb5-gN6hy2-iFNi2P0dvf_vE6-5zaq59YG4SQZQrpu4
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
    ram_gb: 16
    cpus: 4
    linux: true
    roles:
      - frack113.ludus_filigran_opencti
    role_vars:
      ludus_filigran_opencti_OPENCTI_ADMIN_EMAIL: 'admin@ludus.io'
      ludus_filigran_opencti_PENAEV_ADMIN_EMAIL: 'admin@ludus.io'
```

## Example Ludus Range Config with caldera

```yaml
ludus:
  - vm_name: "{{ range_id }}-Caldera"
    hostname: "{{ range_id }}-Caldera"
    template: debian-12-x64-server-template
    vlan: 50
    ip_last_octet: 2
    ram_gb: 4
    cpus: 2
    linux: true
    roles:
      - frack113.ludus_caldera_server
    role_vars:
      ludus_caldera_admin_pwd: 'password'

  - vm_name: "{{ range_id }}-Filigram"
    hostname: "{{ range_id }}-Filigram"
    template: ubuntu-24.04-x64-server-template
    vlan: 50
    ip_last_octet: 1
    ram_gb: 16
    cpus: 6
    linux: true
    roles:
      - ludus_filigran_opencti
    role_vars:
      ludus_filigran_opencti_OPENCTI_ADMIN_EMAIL: 'admin@ludus.io'
      ludus_filigran_opencti_PENAEV_ADMIN_EMAIL: 'admin@ludus.io'
      ludus_filigran_opencti_INJECTOR_CALDERA_ENABLE: true
      ludus_filigran_opencti_INJECTOR_CALDERA_URL: http://10.2.50.2:8888
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [frack113](https://github.com/frack113), for [Ludus](https://ludus.cloud/).
