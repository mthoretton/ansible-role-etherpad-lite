# Ansible role: etherpad-lite

This role should be called from an ansible playbook.  
Etherpad-lite should be placed behind a reverse proxy.  
  
This role will install etherpad from source and will create a service "etherpad-lite".  

Default port binding (Vgrantfile): ``9001`` => ``9001``

## Get started

### commands

``vagrant up``  
``vagrant ssh -c "specs"`` (first time)  
``vagrant ssh -c "specs -p"``  

### config files files

``/tests/ansible-role-etherpad-lite/inventory``  
``/tests/ansible-role-etherpad-lite/playbooks``

## Requirements

nickhammond.logrotate

## Role Variables

- ``etherpad_user_name``: (default: etherpad)
- ``etherpad_user_password``: (default: etherpad)
- ``etherpad_user_home``: (default: /home/etherpad)

- ``etherpad_user_app_path``: (default: "{{etherpad_user_home}}/etherpad-lite")
- ``etherpad_user_log_path``: /!\ Check user permissions on this file (default: /var/log/etherpad-lite.log)

- ``etherpad_title``: (default: Etherpad Lite !)
- ``etherpad_ip``: (default: 0.0.0.0)
- ``etherpad_port``: (default: 9001)

- ``etherpad_admin_name``: (default: admin)
- ``etherpad_admin_password``: (default: admin)

#### database
- ``etherpad_db_dbtype``: (default: dirty)
  - ``etherpad_db_filename``: (default: var/dirty.db)  
or
  - ``# etherpad_db_dbtype``: 
  - ``# etherpad_db_user``: 
  - ``# etherpad_db_host``: 
  - ``# etherpad_db_password``: 
  - ``# etherpad_db_database``: 
- ``etherpad_plugins``: (default: list below)
    - ep_adminpads 
    - ep_chat_always_on_screen_and_tokbox_link
    - ep_copy_paste_images
    - ep_headings2
    - ep_markdown
    - ep_monospace_default
    - ep_previewimages
    - ep_sizes
    - ep_stats

#### nickhammond.logrotate (https://github.com/nickhammond/ansible-logrotate)
- ``name``: The name of the script that goes into /etc/logrotate.d/
- ``path``: Path to point logrotate to for the log rotation
- ``options``: List of directives for logrotate, view the logrotate man page for specifics
- ``scripts``: Dict of scripts for logrotate


## License

MIT

## Author

Mathieu Thoretton