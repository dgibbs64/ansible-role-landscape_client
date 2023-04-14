# landscape_client

An [Ansible](https://www.ansible.com) role to configure [Canonical Landscape Client](https://landscape.canonical.com/) on Ubuntu.

<p align="center">
  <a href="https://ubuntu.com/landscape"><img src="https://user-images.githubusercontent.com/4478206/198877394-eb340178-bd86-4736-be24-77011ae89122.png" alt="Landscape"></a>

<br>
</p>
<p align="center">
<a href="https://app.codacy.com/gh/dgibbs64/ansible-role-landscape_client"><img src="https://img.shields.io/codacy/grade/1a892d499efd4dabb73beffa8d64ed01?logo=codacy&style=flat-square" alt="Codacy grade"></a>
<a href="https://github.com/dgibbs64/ansible-role-landscape_client/actions/workflows/molecule.yml"><img alt="GitHub Workflow Status" src="https://img.shields.io/github/actions/workflow/status/dgibbs64/ansible-role-landscape_client/molecule.yml?label=molecule&logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/landscape_client"><img alt="Ansible Quality Score" src="https://img.shields.io/ansible/quality/61042?logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/landscape_client"><img alt="Ansible Role" src="https://img.shields.io/ansible/role/d/61042?color=EE0000&logo=ansible&style=flat-square"></a>
<a href="https://galaxy.ansible.com/dgibbs64/landscape_client"><img alt="GitHub tag (latest by date)" src="https://img.shields.io/github/v/tag/dgibbs64/ansible-role-landscape_client?color=EE0000&label=release&logo=ansible&style=flat-square"></a>
<a href="https://github.com/dgibbs64/ansible-role-landscape_client/blob/main/LICENSE.md"><img src="https://img.shields.io/github/license/dgibbs64/ansible-role-landscape_client?style=flat-square" alt="MIT License"></a>
</p>

## Requirements

Landscape SaaS Account or self-hosted Landscape Server.

## Role Variables

```yaml
---
# defaults file for ansible-role-landscape_client

# Landscape server
landscape_client_server: "{{ groups['landscape_server'][0] }}"

# Landscape server self-hosted
landscape_client_server_self_hosted: false

# Landscape account name
landscape_client_account_name: account-name

# Landscape Client computer title
landscape_client_computer_title: "computer title"

# Landscape Client access group
landscape_client_access_group: "access-group"

# Landscape Client tags
landscape_client_tags: "tag1, tag2"

## Self-hosted only
# Server certificate on client that will be used
landscape_client_ssl_cert: "/etc/landscape/server.pem"
## Directory of the SSL public key on the primary app server.
landscape_client_server_ssl_cert: "/etc/ssl/certs/ssl-cert-snakeoil.pem"

# Landscape Server urls
landscape_client_server_ping_url: "http://landscape.canonical.com/ping"
landscape_client_server_url: "https://landscape.canonical.com/message-system"

# Landscape client data path
landscape_client_data_path: "/var/lib/landscape/client"

# Landscape client log level: debug, info, warning, error or critical
landscape_client_log_level: "info"

# Force landscape client to register
landscape_client_force_register: false

# Enable Landscape script execution
landscape_client_enable_script_users: false

# Users that can execute Landscape scripts
landscape_client_script_users: root
```

## Dependencies

None

## Example Playbook

### Landscape SaaS

```yaml
---
- name: "Configure Landscape Client"
  hosts: all
  vars:
    landscape_client_account_name: landscape-account-name
    landscape_client_computer_title: "Computer Title"
    landscape_client_access_group: "access-group"
    landscape_client_tags: "web, db, apache"
  roles:
    - role: dgibbs64.landscape_client
```

### Self-hosted

```yaml
---
- name: "Configure Landscape Client"
  hosts: all
  vars:
    landscape_client_server: "{{ groups['landscape_server'][0] }}"
    landscape_client_account_name: landscape-account-name
    landscape_client_computer_title: "Computer Title"
    landscape_client_access_group: "access-group"
    landscape_client_tags: "web, db, apache"
    landscape_client_server_ping_url: "http://landscape.example.com/ping"
    landscape_client_server_url: "https://landscape.example.com/message-system"
  roles:
    - role: dgibbs64.landscape_client
```

## License

MIT

## Author Information

Updated by: Daniel Gibbs

- [Daniel Gibbs](https://danielgibbs.co.uk)

Original by Larry Smith Jr.

- [@mrlesmithjr](https://www.twitter.com/mrlesmithjr)
- [EverythingShouldBeVirtual](http://www.everythingshouldbevirtual.com)
- mrlesmithjr [at] gmail.com
