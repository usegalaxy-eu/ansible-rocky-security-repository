# Ansible Molecule tests

Tests run in Podman containers using Ansible Molecule.

## Setup (Ubuntu)

Run all commands from the root of the repository.

Install the required Python packages.

```shell
uv pip install -r requirements.txt -r molecule/requirements.txt
```

Install Podman.

```shell
sudo apt-get install --yes podman
```

Install the Ansible collection required by the role.

```shell
uv run ansible-galaxy collection install -r meta/collection-requirements.yml
```

## Running tests

Use the base configuration file when running the Ansible Molecule tests (do it from the root of the repository), like
this.

```shell
uv run molecule --base-config molecule/base.yml test
```
