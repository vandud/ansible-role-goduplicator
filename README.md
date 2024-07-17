Ansible Role: Goduplicator
=========

Installs [Goduplicator](https://github.com/mkevac/goduplicator) on any Linux servers  

This role installs and configures the specified version of Goduplicator from the repo releases page on Github  


Requirements
------------

None

Role Variables
--------------

This role is pretty simple  

| Name    | Description    | Required    | Default    |
|:--|:--|:-:|:--|
| `goduplicator_repo_url` | URL to Goduplicator repo |  | https://github.com/mkevac/goduplicator |
| `goduplicator_download_url` | URL to tar with binary |  | `{{ goduplicator_repo_url }}/releases/download/v{{ goduplicator_version }}/goduplicator_{{ goduplicator_version }}_Linux_x86_64.tar.gz` |
| `goduplicator_version` | Goduplicator desired version |  | 0.2.2 |
| `goduplicator_system_user` | User within which Goduplicator will be launched |  | goduplicator |
| `goduplicator_system_group` | Group within which Goduplicator will be launched |  | goduplicator |
| `goduplicator_bin_dir` | Location where to place binary |  | /usr/local/bin |
| `goduplicator_duration` | `-d` flag |  | 20s |
| `goduplicator_forward` | `-f` flag | * | `localhost:8081` |
| `goduplicator_listen` | `-l` flag | * | `localhost:8080` |
| `goduplicator_mirror` | `-m` flag | * | `[localhost:8082, localhost:8083]` |
| `goduplicator_mirror_connect_timeout` | `-t` flag |  | 500ms |
| `goduplicator_mirror_write_timeout` | `-wt` |  | 20ms |
| `goduplicator_use_zero_copy` | `-z` flag |  | `true` |

Dependencies
------------

None 

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - role: vandud.goduplicator
       vars:
         goduplicator_listen: 0.0.0.0:8000
         goduplicator_forward: my-backend-1:8001
         goduplicator_mirror: my-backup-backend:8002
```

License
-------

BSD

Author Information
------------------

This role was created in 2024 by [Ivan Dudin](ivan@dudin.email)
