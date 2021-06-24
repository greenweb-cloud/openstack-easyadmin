# openstack-easyadmin
Ansible playbooks and roles to automate openstack administrative tasks 

if run on deployment we don't need openstack-sdk and can run playbook with <b> openstack-ansilbe </b>
# Instalation
1. install python3-openstacksdk:
   $ sudo apt install python3-openstacksdk

as openstacksdk package is installed for python version3 and above, so you should run playbooks with python3 interpreter and set it explicitly when running ansible-playbook command. so add "ansible_python_interpreter=/usr/bin/python3" to group_vars file, or run ansible playbooks like this:

   $ ansible-playbook <playbook.yml>  -e "ansible_python_interpreter=/usr/bin/python3"
   
   
# step 1

` ansible-galaxy collection install -r requirements.yml `

# step 2

create hosts inventory files

host sample-->
`
[all]
infra1
infra2
infra3
compute1
compute2


[computes]
compute1
compute2

[infras]
infra1
infra2
infra3
`

# step 3

` ansible-playbook -i /path/to/hosts --tag infra -e 'machine=infras' pre-deploy.yml  `
` ansible-playbook -i /path/to/hosts --tag compute -e 'machine=computes' pre-deploy.yml  `

