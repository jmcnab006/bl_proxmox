# Bridgeline Proxmox role

This role installs and configures network, snmpd, packages, sets the hostname, system time and NTP for a proxmox 9.X host or cluster.

## Requirements

Proxmox install of 9.1 or greater.

## Dependencies

- `community.general.timezone`

## Use the role

You can use this role through Ansible `requirements.yaml` or Git submodules to install the role in your playbook's `roles/` directory.

### Ansible requirements.yaml

Ansible can also pull the role from GitLab directly. Add this to your `requirements.yaml` file at the root of your playbook:

```yaml
roles:
  - name: bl_proxmox
    src: git+https://github.com/jmcnab006/bl_proxmox
    version: main
```

Use the `ansible-galaxy` command to install all roles defined in your `requirements.yaml`:

```command
ansible-galaxy install -r requirements.yaml
```

Use the name of the role directory in the `roles:` list to use it in your playbook.

```yaml
- name: ROLES | Run Bridgeline Proxmox role on all hosts. 
  hosts: all
  roles:
    - bl_proxmox
```

### Git submodules

Add the role to your deployment repository as a submodule into a `roles/` directory. Set the submodule to track the `main` branch.

```shell
git submodule add https://github.com/jmcnab006/bl_proxmox.git roles/bl_proxmox
git config -f .gitmodules submodule.roles/bl_proxmox.branch main
```

To pull changes to all submodules, add the `--recurse-submodules` when pulling your deployment repository.

```shell
git pull--recurse-submodules
```

Optionally, set your deployment repository to automatically pull all submodules with `git pull`.

```shell
git config submodule.recurse true
```

## Role variables

The role is designed to run defaults the majority of the time, but has some customizations to accommodate different environments.

Refer to [argument specifications](meta/argument_specs.yaml) for detailed information on all role variables.
