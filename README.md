# Restic

This role handles installing and configuring Restic, including systemd services
and timers to automatically run Restic.

## Requirements

The hosts you are targeting should have the following packages:

- python >= 2.6
- python-dnf

## Role Variables

| Variable | Required | Default | Description |
| --- | --- | --- | --- |
| restic_repos | &#9989; | `[]` | A list of dictionaries defining a restic repo and what files/directories to backup. The required dictionary keys are `name`, `repo`, and `files`.<br><br>See example below for format. |

## Dependencies

None

## Example Playbook

```yaml
- hosts: servers
  roles:
    - role: jaredhocutt.restic
      vars:
        restic_repos:
          - name: b2
            repo: "b2:bucketname:path/to/repo"
            env_vars:
              B2_ACCOUNT_ID: abcdef
              B2_ACCOUNT_KEY: ghijklm
              RESTIC_PASSWORD: password
            files:
              - /home/user1
              - /home/user2
```

## License

MIT

## Author Information

Jared Hocutt (@jaredhocutt)
