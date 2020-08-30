Role Name
=========

Create and Delete projects for openstack

Requirements
------------

Ansible 2.8 or higher
python version 3.8 or higher
python3-openstacksdk 0.46 or higher 

Role Variables
--------------

Currently the following variables are supported:

* `user_role` - Default: _member_. role of user, you can use from ['_member_', 'admin']
* `user_name` - Default: demo. user name to be created.
* `user_password` - Default: password. password of new created user which will be shown at plays
* `project_name` - Default: demo. user will be assigned as member of {{ project_name }} variable
* `domain_name` - Default: default. user will be assigned as member  of {{ domain_name }} variable
* `password_lenght` - Default: 8. password length.


Dependencies
------------
you should specifiy `domain_name` and `project_name`. but you can use `os_identity-domain` and `os_identity-project` roles within this collection to create project and domain names as well. 

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
       # add/update 'demo' user
       - { role: os_identity-user } 
    
       # To delete user 'demo':
       #    add option --tags=del-user like this:
       #    ansible-playbook os_identity-domain.yml --tags=del-user


the following sample will create domain, project and assing newly create domain and project to user:

     ---
     - hosts: localhost
       gather_facts: yes
       vars:
         domain_name: 'default'
         project_name: 'admin'
         user_name: 'iman'
         user_role: 'admin'
    
       roles:
         # add/update 'demo' domain
         - { role: os_identity-domain }  

         # add/update 'demo' project
         - { role: os_identity-project }

         # add/update 'demo' user
         - { role: os_identity-user } 

License
-------

GPLv3

Author Information
------------------

Iman Darabi <iman.darabi@gmail.com>
