# Ansible-role-opentofu-installer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/willbrid/ansible-role-opentofu-installer/blob/main/LICENSE) [![CI](https://github.com/willbrid/ansible-role-opentofu-installer/actions/workflows/ci.yml/badge.svg)](https://github.com/willbrid/ansible-role-opentofu-installer/actions/workflows/ci.yml)

The **ansible-role-opentofu-installer** role allows you to install **OpenTofu** in standalone mode on Linux systems by directly downloading and placing the official binary into a system binary directory (by default **/usr/local/bin**). The role does not depend on any package manager and guarantees a simple, clean, and portable installation.

## Requirements

- **Linux Systems** : Red Hat and Debian distributions

## Description of Variables

|Name|Type|Description|Mandatory|Default value|
|----|----|-----------|---------|-------------|
`opentofu_version`|str|opentofu version number. Format: x.y.z|no|`"1.10.2"`
`opentofu_bin_dir`|str|opentofu binary installation directory|no|`"/usr/local/bin"`
`should_verify_opentofu_checksum`|bool|specify whether the integrity of the opentofu archive file should be checked after downloading.|no|`true`

## Dependencies

None.

## Example Playbook

- Role installation

```bash
mkdir -p $HOME/install-opentofu
```

```bash
vim $HOME/install-opentofu/requirements.yml
```

```yaml
- name: ansible-role-opentofu-installer
  src: git+https://github.com/willbrid/ansible-role-opentofu-installer.git
  version: v0.0.1
```

```bash
cd $HOME/install-opentofu && ansible-galaxy install --force -r requirements.yml
```

- Using the role in a playbook

```bash
vim $HOME/install-opentofu/playbook.yml
```

```yaml
---
- hosts: localhost
  become: true
  vars:
    opentofu_version: "1.10.2"
    should_verify_opentofu_checksum: true

  roles:
    - ansible-role-opentofu-installer
```

```bash
cd $HOME/install-opentofu && ansible-playbook playbook.yml
```

## License

MIT

## Author Information

William Bridge NGASSAM
