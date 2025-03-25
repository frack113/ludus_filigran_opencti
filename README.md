# Ansible Role: OpenCTI/OpenBAS Server

An Ansible Role that installs [OpenCTI](https://docs.opencti.io/latest/) and [OpenBAS](https://docs.openbas.io/latest/) for [LUDUS](https://ludus.cloud/).

## Requirements

- Linux server
  - Debian 12
  - Ubuntu 24 LTS
- Internet connection

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
ludus_filigran_opencti_version: 6.5.9
ludus_filigran_openbas_version: 1.14.1

# Docker .env
ludus_filigran_opencti_ADMIN_EMAIL: 'admin@opencti.io'
ludus_filigran_opencti_ADMIN_PASSWORD: password
ludus_filigran_opencti_ADMIN_TOKEN: 9079c861-460e-49ba-9948-54137cfeb8ca
ludus_filigran_opencti_HEALTHCHECK_ACCESS_KEY: 9813287b-4234-4b9c-8382-73938f640455
ludus_filigran_opencti_MINIO_ROOT_USER: d5e955ed-be95-4220-b828-d3d62c00cab3
ludus_filigran_opencti_MINIO_ROOT_PASSWORD: a46c6ee2-d3a8-4cbc-a39e-6f03a1e53524
ludus_filigran_opencti_RABBITMQ_DEFAULT_USER: guest
ludus_filigran_opencti_RABBITMQ_DEFAULT_PASS: guest
ludus_filigran_opencti_ELASTIC_MEMORY_SIZE: 4G
ludus_filigran_opencti_CONNECTOR_HISTORY_ID: 8576ff97-a469-4941-80c9-b5d4c44e6c52
ludus_filigran_opencti_CONNECTOR_EXPORT_FILE_STIX_ID: be7cc4f6-56af-40ae-ad90-7c387c510fc5
ludus_filigran_opencti_CONNECTOR_EXPORT_FILE_CSV_ID: 2d238944-62cd-4abf-b7d3-14551709a832
ludus_filigran_opencti_CONNECTOR_IMPORT_FILE_STIX_ID: d9c14294-ab97-4a96-b87a-4fbfacfe9e15
ludus_filigran_opencti_CONNECTOR_EXPORT_FILE_TXT_ID: da38132d-7663-4bb9-a956-8621f52170e6
ludus_filigran_opencti_CONNECTOR_IMPORT_DOCUMENT_ID: a5fea1b1-a12b-468d-9d45-0cd4b13b33be
ludus_filigran_opencti_CONNECTOR_ANALYSIS_ID: b13e11c6-028e-426b-8cfd-1e334cb95161
ludus_filigran_opencti_SMTP_HOSTNAME: localhost
ludus_filigran_opencti_CONNECTOR_CISA_EXPVUL: 14de3c6f-0e6d-46d9-8aaa-9ce92230c3be
ludus_filigran_opencti_CONNECTOR_MALWAREBAZAAR: f2a1a9f6-1fcc-43cb-a981-875216672bde
ludus_filigran_opencti_CONNECTOR_MITRE: 6a833c97-3b93-46f7-876c-18e145de04ca


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

# Collector MITRE ATT&CK Configuration
ludus_filigran_opencti_COLLECTOR_MITRE_ATTACK_ID: 3050d2a3-291d-44eb-8038-b4e7dd107436

# COLLECTOR Atomic Red Team Configuration
ludus_filigran_opencti_COLLECTOR_ATOMIC_RED_TEAM_ID: 0f2a85c1-0a3b-4405-a79c-c65398ee4a76
```

## Dependencies

Ansible :

- community.docker

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
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [frack113](https://github.com/frack113), for [Ludus](https://ludus.cloud/).
