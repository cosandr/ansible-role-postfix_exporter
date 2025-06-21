# ansible-role-postfix_exporter

![GitHub](https://img.shields.io/github/license/cosandr/ansible-role-postfix_exporter) ![GitHub last commit](https://img.shields.io/github/last-commit/cosandr/ansible-role-postfix_exporter) ![GitHub issues](https://img.shields.io/github/issues-raw/cosandr/ansible-role-postfix_exporter)

**Ansible role for setting up postfix_exporter.**

Installs https://github.com/sergeymakinen/postfix_exporter

Dashboard https://gist.github.com/sergeymakinen/7a3ceb3de41fd4f79703b1497c32b33a

## Requirements

Ansible 2.12 or higher, `go` (min 1.16) must be installed.

## Variables

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `postfix_exporter_version` | latest | Version to install |
| `postfix_exporter_listen_address` | :9907 | Exporter web listen address |
| `postfix_exporter_args` | [] | Extra command line arguments to pass to exporter |

## Dependencies

None.

## Example Playbook

```yaml
---

- hosts: all
  become: true
  gather_facts: true
  roles:
    - role: postfix_exporter
      vars:
        postfix_exporter_args:
          - "--collector=systemd"
```

## Author

[Andrei Costescu](https://github.com/cosandr/)
