# openstack-easyadmin
Ansible playbooks and roles to automate openstack administrative tasks 

if run on deployment we don't need openstack-sdk and can run playbook with <b> openstack-ansilbe </b>
# Instalation
1. install python3-openstacksdk:
   $ sudo apt install python3-openstacksdk

as openstacksdk package is installed for python version3 and above, so you should run playbooks with python3 interpreter and set it explicitly when running ansible-playbook command. so add "ansible_python_interpreter=/usr/bin/python3" to group_vars file, or run ansible playbooks like this:

   $ ansible-playbook <playbook.yml>  -e "ansible_python_interpreter=/usr/bin/python3"
