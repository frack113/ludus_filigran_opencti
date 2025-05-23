# Ansible Role: OpenCTI/OpenBAS Server

An Ansible Role that installs [OpenCTI](https://docs.opencti.io/latest/) and [OpenBAS](https://docs.openbas.io/latest/) for [LUDUS](https://ludus.cloud/).

## Requirements

- Linux server
- Internet connection

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
ludus_filigran_opencti_version: 6.6.6
ludus_filigran_openbas_version: 1.15.1

# OpenCTI General Configuration
ludus_filigran_opencti_ADMIN_EMAIL: 'admin@domain.com'
ludus_filigran_opencti_ADMIN_PASSWORD: password
ludus_filigran_opencti_ADMIN_TOKEN: 9079c861-460e-49ba-9948-54137cfeb8ca
ludus_filigran_opencti_HEALTHCHECK_ACCESS_KEY: 9813287b-4234-4b9c-8382-73938f640455
ludus_filigran_opencti_SMTP_HOSTNAME: localhost

# Minio
ludus_filigran_opencti_MINIO_ROOT_USER: d5e955ed-be95-4220-b828-d3d62c00cab3
ludus_filigran_opencti_MINIO_ROOT_PASSWORD: a46c6ee2-d3a8-4cbc-a39e-6f03a1e53524

# Rabbit MQ
ludus_filigran_opencti_RABBITMQ_DEFAULT_USER: guest
ludus_filigran_opencti_RABBITMQ_DEFAULT_PASS: guest

# Elasticsearch
ludus_filigran_opencti_ELASTIC_MEMORY_SIZE: 4G

# PostgreSQL Configuration
ludus_filigran_opencti_POSTGRES_USER: ChangeMe
ludus_filigran_opencti_POSTGRES_PASSWORD: ChangeMe

# OpenBAS General Configuration
ludus_filigran_opencti_OPENBAS_ADMIN_EMAIL: 'admin@domain.com'
ludus_filigran_opencti_OPENBAS_ADMIN_PASSWORD: password
ludus_filigran_opencti_OPENBAS_ADMIN_TOKEN: 8322bcfa-1ce4-4d9b-8798-473381382782
ludus_filigran_opencti_OPENBAS_HEALTHCHECK_KEY: ChangeMe

# Spring Mail Configuration
ludus_filigran_opencti_SPRING_MAIL_HOST: smtp.changeme.com
ludus_filigran_opencti_SPRING_MAIL_PORT: 465
ludus_filigran_opencti_SPRING_MAIL_USERNAME: ChangeMe@domain.com
ludus_filigran_opencti_SPRING_MAIL_PASSWORD: ChangeMe
ludus_filigran_opencti_SPRING_MAIL_PROPERTIES_MAIL_SMTP_AUTH: true
ludus_filigran_opencti_SPRING_MAIL_PROPERTIES_MAIL_SMTP_SSL_ENABLE: true
ludus_filigran_opencti_SPRING_MAIL_PROPERTIES_MAIL_SMTP_STARTTLS_ENABLE: false

# OpenBAS IMAP Configuration
ludus_filigran_opencti_OPENBAS_MAIL_IMAP_ENABLED: false
ludus_filigran_opencti_OPENBAS_MAIL_IMAP_HOST: imap.changeme.com
ludus_filigran_opencti_OPENBAS_MAIL_IMAP_PORT: 993
ludus_filigran_opencti_OPENBAS_MAIL_IMAP_AUTH: true
ludus_filigran_opencti_OPENBAS_MAIL_IMAP_SSL_ENABLE: true
ludus_filigran_opencti_OPENBAS_MAIL_IMAP_STARTTLS_ENABLE: false

# CTI Connectors use the name of the folder
ludus_filigran_opencti_external_import: [cisa-known-exploited-vulnerabilities,mitre]
ludus_filigran_opencti_internal_enrichment: []
ludus_filigran_opencti_internal_export_file: [export-file-csv,export-file-stix,export-file-txt,export-report-pdf,export-ttps-file-navigator]
ludus_filigran_opencti_internal_import_file: [import-document,import-file-misp,import-file-stix,import-file-yara]
ludus_filigran_opencti_stream: []

# BAS Connectors
ludus_filigran_openbas_collectors: [atomic-red-team,mitre-attack]
ludus_filigran_openbas_injectors: [http-query,nmap]
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
      ludus_filigran_opencti_version: 6.6.6
      ludus_filigran_openbas_version: 1.15.1
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [frack113](https://github.com/frack113), for [Ludus](https://ludus.cloud/).
