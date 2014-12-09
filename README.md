CouchPotato
===========
This role deploys [CouchPotato](https://couchpota.to), an automatic NZB & torrent downloader.

Requirements
------------
This role has been written with [SmartOS](https://smartos.org) in mind, and is designed to be deployed to a [zone](https://wiki.smartos.org/display/DOC/Zones), for use as a server.
However, if popular demand shows, I'll happily add in support for other operating systems.

Role Variables
--------------
All variables have sensible defaults, which can be found in `defaults/main.yml`.
The current version includes the following variables:

| Name               | Default Value | Description                  |
|--------------------|---------------|------------------------------|
| couchpotato_user_name  | couchpotato | username to run the CouchPotato service |
| couchpotato_group_name | couchpotato | groupname to run the CouchPotato service |
| couchpotato_user_uid | 1000 | UID of the CouchPotato service user |
| couchpotato_group_gid | 1000 | GID of the CouchPotato service group |
| couchpotato_user_home | /opt/{{ couchpotato_user_name }} | home directory for the CouchPotato service user |
| couchpotato_conf_path | {{ couchpotato_user_home }}/.couchpotato | configuration directory for the CouchPotato service |
| couchpotato_library_path | {{ couchpotato_user_home }}/data | root library path, to be used for download directories, movie library etc. |
| couchpotato_binary_path | {{ couchpotato_user_home }}/bin/CouchPotato | path where the CouchPotato source will reside |
| couchpotato_pid_file | {{ couchpotato_conf_path }}/couchpotato.pid | pidfile for the CouchPotato service to write the pid to |
| couchpotato_path_var | /opt/local/bin:/opt/local/sbin:/usr/bin:/bin | set $PATH for the CouchPotato service script |
| couchpotato_service_args | --data_dir {{ couchpotato_conf_path }} --config_file<br> {{ couchpotato_conf_path }}/settings.conf<br> --daemon --pid_file {{ couchpotato_pid_file }} | arguments the CouchPotato service will use when starting |

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
