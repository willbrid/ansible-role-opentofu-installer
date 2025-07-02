# Ansible-role-opentofu-installer

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/willbrid/ansible-role-opentofu-installer/blob/main/LICENSE) [![CI](https://github.com/willbrid/ansible-role-opentofu-installer/actions/workflows/ci.yml/badge.svg)](https://github.com/willbrid/ansible-role-opentofu-installer/actions/workflows/ci.yml)

Le rôle **ansible-role-opentofu-installer** permet d’installer **OpenTofu** en version standalone sur les systèmes Linux en téléchargeant et plaçant directement le binaire officiel dans un répertoire binaire système (par défaut **/usr/local/bin**). Le rôle ne dépend d’aucun gestionnaire de paquets et garantit une installation simple, propre et portable.

## Exigences

- **Systèmes Linux** : distributions RedHat et Debian

## Description des Variables

|Nom|Type|Description|Obligatoire|Valeur par défaut|
|---|----|-----------|-----------|-----------------|
`opentofu_version`|str|numéro de version d'opentofu. Format : x.y.z|non|`"1.10.2"`
`opentofu_bin_dir`|str|répertoire d'installation du binaire d'opentofu|non|`"/usr/local/bin"`
`should_verify_opentofu_checksum`|bool|dire s'il faut vérifier l'intégrité du fichier archive d'opentofu après téléchargement|non|`true`

## Dépendances

Aucune.

## Exemple Playbook

- Installation du rôle

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

- Utilisation du rôle dans un playbook

```bash
vim $HOME/install-opentofu/playbook.yml
```

```yaml
---
- hosts: localhost
  vars:
    opentofu_version: "1.10.2"
    should_verify_opentofu_checksum: true

  roles:
    - ansible-role-opentofu-installer
```

```bash
cd $HOME/install-opentofu && ansible-playbook playbook.yml
```

## Licence

MIT

## Informations sur l'auteur

William Bridge NGASSAM
