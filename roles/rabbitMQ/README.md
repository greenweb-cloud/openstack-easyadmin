# RabbitMq Status and Restart
   
# step 1

clone the repository

# step 2

create hosts inventory files

host sample-->

```
[rabbit]
infra1_rabbit
infra2_rabbit
infra3_rabbit

```

# step 3

For get Status of the RabbitMq run this command
` ansible-playbook -i /path/to/hosts --tag status  role/rabbitMQ/test/pb.yml  `

For Restart the RabbitMq run this command 
` ansible-playbook -i /path/to/hosts --tag restart role/rabbitMQ/test/pb.yml  `

this will first stop from 1 to 3 and start vise-versa 
the reason of this task is not to loose cluster (the last node you stop will be the first node to start)

more doc at https://docs.openstack.org/openstack-ansible/pike/admin/maintenance-tasks/rabbitmq-maintain.html

