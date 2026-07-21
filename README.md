Ansible Role: Rocky Linux Security Repository
==============================================

Enables the [Rocky Linux Security Repository](https://rockylinux.org/news/2026-05-14-introducing-security-repository), an optional repository that provides urgent security fixes ahead of upstream Red Hat Enterprise Linux when serious vulnerabilities (such as CopyFail and Dirty Frag) are disclosed.

## Requirements

None.

## Role Variables

Ansible variables are listed below, along with their default values (see
`defaults/main.yml`):

```yaml
rocky_security_repository_repo_definitions_upgrade: false
rocky_security_repository_system_upgrade: false
```

Set `rocky_security_repository_repo_definitions_upgrade` to `true` to always update the Rocky Linux repository definitions package `rocky-repos`, even if the Rocky Linux Security Repository is already enabled. It defaults to `false`.

Set `rocky_security_repository_system_upgrade` to `true` to update all installed packages after enabling the repository. It defaults to `false`.

## Dependencies

This role depends on the `community.general` Ansible collection (version >= 8.2.0). It is installed automatically from the role's `meta/collection-requirements.yml` file when the role is installed through Ansible Galaxy.

## Example Playbook

```yaml
- hosts: all
  gather_facts: true
  become: true
  roles:
    - role: usegalaxy_eu.rocky_security_repository
      when: ansible_facts['distribution'] == "Rocky"
      rocky_security_repository_system_upgrade: true
```

If the Rocky Linux Security Repository is not already enabled, this playbook updates the repository definitions package `rocky-repos` and enables the `security` repository using `dnf config-manager`. Set `rocky_security_repository_repo_definitions_upgrade` to `true` to update repository definitions regardless of whether the security repository is already enabled. A full system upgrade is optional and is disabled by default; setting `rocky_security_repository_system_upgrade` to `true` enables it.

> **Note**
> Packages in this repository are explicitly versioned to be superseded by the next upstream release. When Red Hat ships their fix, it will replace the security repository's fix automatically.

## License

[MIT](LICENSE.md)

## Author Information

This role was created in 2026 by [José Manuel Domínguez](https://github.com/domgz).
