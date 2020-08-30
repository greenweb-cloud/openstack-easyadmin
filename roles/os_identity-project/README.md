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

* `project_name` - Default: demo. project name to create.
* `domain_ID` - Default: "default". domain id name witch project will be created for.
* `project_desc` -Default: "Created by Ansible role:{{ ansible_play_role_names }}, Date created: {{ ansible_date_time.date }}". project description

Dependencies
------------
None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
        # add or update 'demo' project           
        - { role: os_identity-project, project_name: "company1" }
    
    # delete 'demo' domain                              
    # add option --tags=del-project like this:   
    # ansible-playbook os_identity-project.yml --tags=del-project 

License
-------

GPLv3

Author Information
------------------

Iman Darabi <iman.darabi@gmail.com>
