CouchPotato
===========
This role deploys [CouchPotato](https://couchpota.to), an automatic NZB & torrent downloader.

Requirements
------------
This role requires Ansible 2.0

Supported Platforms
-------------------
- Ubuntu: 15.04
- Debian: 8
- EL: 7

Role Variables
--------------
All variables have sensible defaults, which can be found in `defaults/main.yml`.
The current version includes the following variables:

### Defaults
| Name               | Default Value | Description                  |
|--------------------|---------------|------------------------------|
| `couchpotato_user_name`  | couchpotato | The user to run the CouchPotato service |
| `couchpotato_group_name` | couchpotato | The primary group for `couchpotato_user_name` to run the CouchPotato service |
| `couchpotato_user_uid` | 1005 | UID of the CouchPotato service user |
| `couchpotato_group_gid` | 1005 | GID of the CouchPotato service group |
| `couchpotato_user_home` | /var/lib/{{ couchpotato_user_name }} | home directory for the CouchPotato service user |
| `couchpotato_library_path` | {{ couchpotato_user_home }}/data | Root library path, to be used for download directories, movie library etc. |
| `couchpotato_clone_uri` | 'git://github.com/RuudBurger/CouchPotatoServer' | The remote Git repo to clone CouchPotato from |
| `couchpotato_dependencies` | - git-core | A list of dependency packages for CouchPotato |
|                            | - python-lxml | |
|                            | - python-openssl | |
|                            | - unrar-free | |
| `couchpotato_service_file` | | |
| `    src`                  | couchpotato.service.j2 | The source template for the CouchPotato service manifest |
| `    dest`                 | /etc/systemd/system/couchpotato.service | The destination to deploy the CouchPotato service manifest to |
| `couchpotato_service_reload_command` | `systemctl daemon-reload` | The command to use when reloading the CouchPotato service configuration |

### CentOS 7
| Name               | Default Value | Description                  |
|--------------------|---------------|------------------------------|
| `couchpotato_dependencies` | - git-core | A list of dependency packages for CouchPotato |
|                            | - python-lxml | |
|                            | - pyOpenSSL | |
|                            | - unar | |


Example Playbook
----------------

    - hosts: couchpotato_servers
      roles:
        - role: cmacrae.couchpotato

Or, passing parameter values:

	- hosts: couchpotato_servers
	  roles:
	    - { role: cmacrae.couchpotato, couchpotato_user_name: downld, couchpotato_group_name: downld }
License
-------
MIT

Author Information
------------------
Created by [Calum MacRae](http://cmacr.ae)

Feel free to:  
Contact me - [@calumacrae](https://twitter.com/calumacrae), [mailto:calum0macrae@gmail.com](calum0macrae@gmail.com)  
[Raise an issue](https://github.com/cmacrae/ansible-couchpotato/issues)  
[Contribute](https://github.com/cmacrae/ansible-couchpotato/pulls)  
