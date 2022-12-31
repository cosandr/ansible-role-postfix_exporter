# ansible-role-postfix_exporter

![GitHub](https://img.shields.io/github/license/cosandr/ansible-role-postfix_exporter) ![GitHub last commit](https://img.shields.io/github/last-commit/cosandr/ansible-role-postfix_exporter) ![GitHub issues](https://img.shields.io/github/issues-raw/cosandr/ansible-role-postfix_exporter)

**Ansible role for setting up postfix_exporter.**

When cross-compiling, systemd support is disabled by default.
I assume this is because I'm missing the systemd libraries for other architectures.

## Requirements

Ansible 2.12 or higher, `go` (min 1.16) must be installed.

## Variables

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `postfix_exporter_repo_url` | https://github.com/netzkommune/postfix_exporter | Path to source code to compile |
| `postfix_exporter_version` | master | git reference to checkout |
| `postfix_exporter_listen_address` | :9154 | Exporter web listen address |
| `postfix_exporter_args` | {} | Extra command line arguments to pass to exporter |
| `postfix_exporter_build_localhost` | true | Set to false to build binary on target host, requires `go` |
| `postfix_exporter_nosystemd` | varies | Defaults to false if building on localhost and target architecture is not `x86_64` |

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
          "postfix.showq_path": "/var/spool/whatever/showq"
          "systemd.enable": "true"
          "systemd.unit": "postfix@-.service"
```

## Author

[Andrei Costescu](https://github.com/cosandr/)
