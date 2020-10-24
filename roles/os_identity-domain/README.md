Role Name
=========

Create and Delete domains for openstack

Requirements
------------

Ansible 2.8 or higher
python version 3.8 or higher
python3-openstacksdk 0.46 or higher 

Role Variables
--------------

Currently the following variables are supported:

* `domain_name` - Default: demo. domain name to create.
* `domain_desc` - Default: "Created by Ansible role:{{ ansible_play_role_names }}, Date created: {{ ansible_date_time.date }}"

Dependencies
------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: os_identity-domain, domain_name: "my_domain" }

License
-------

GPLv3

Author Information
------------------

Iman Darabi <iman.darabi@gmail.com>
