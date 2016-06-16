ansible role apt
================

Ansible role for managing playbooks apt part like :
 - update / upgrade
 - install/uninstall packages
 - add/remove repositories
 - add debconf infos

Role Defaults Variables
-----------------------

See [defaults/main.yml](defaults/main.yml) for more information.

    apt_cache_valid_time: 3600
    apt_upgrade: true
    apt_upgrade_type: safe          # safe, full or dist
    apt_install:
      - python-apt
      - unattended-upgrades
    apt_install_repositories: false
    apt_remove_repositories: false
    apt_debconf_name: false

using Debconf :
-----------------------

    apt_debconf_name: "oracle-java8-installer"
    apt_debconf_question: "shared/accepted-oracle-license-v1-1"
    apt_debconf_value: "true"
    apt_debconf_vtype: "select"

Example Playbook
----------------

    - hosts: localhost
      vars:
          apt_install: [cowsay, cowthink, sl, figlet]
      roles:
        - { role: package_apt, tags: apt }

License
-------

Licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

