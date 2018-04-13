# Restic

Installs restic and configures daily backup of the home directory of the user.

## Requirements

None

## Role Variables

| Variable             | Required           | Default                                 | Description                                                                                                                                   |
| -------------------- | ------------------ | --------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `restic_repo`        | :heavy_check_mark: |                                         | The repo for restic to use. The format of this option can be found at <https://restic.readthedocs.io/en/latest/030_preparing_a_new_repo.html> |
| `restic_passwd`      | :heavy_check_mark: |                                         | The password used to encrypt your data.                                                                                                       |
| `restic_env_vars`    | :x:                |                                         | Environment variables needed for the repo type you've chosen (see example playbook below).                                                    |
| `restic_config_dir`  | :x:                | `{{ ansible_user_dir }}/.config/restic` | The directory to use for restic config information                                                                                            |
| `restic_passwd_file` | :x:                | `{{ restic_config_dir }}/passwd`        | The file to save the `restic_passwd`                                                                                                          |


## Dependencies

None

## Example Playbook

```yaml
- hosts: localhost
  vars:
    b2_account_id: 893678543f31
    b2_account_key: 89367dc23f3111e8b4670ed5f89f718b3f3111367d
    b2_bucket: my-restic-backup

    restic_passwd: password123
    restic_repo: "b2:{{ b2_bucket }}:{{ ansible_hostname }}"
    restic_env_vars:
      B2_ACCOUNT_ID: "{{ b2_account_id }}"
      B2_ACCOUNT_KEY: "{{ b2_account_key }}"
  roles:
      - jaredhocutt.restic
```
