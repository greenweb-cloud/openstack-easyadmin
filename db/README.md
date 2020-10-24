## Best Practices for Backups
Some recommendations to consider for a good scheduled backup regime:

You should be able to completely recover from a catastrophic failure from at least two previous full backups. Just in case the most recent full backup is damaged, lost, or corrupt,
Your backup should contain at least one full backup within a chosen cycle, normally weekly,
Store backups away from the current data location, preferably off site,
Use a mixture of mysqldump and Xtrabackup for extra safety, and not rely on one method,
Test restore your backups on a regular basis, e.g. every two months.
A weekly full backup combined with daily incremental backup is normally enough. Keeping a number of backups for a period of time is always a good plan, maybe keep each weekly backup for one month. This allows you to recover an older database in case of emergencies or if for some reason you have local backup file corruption

<img src=./img/1.png></img>



## backup openstack databse
ansible-playbook -i inventory --tags backup backup_restor.yml

ansible-playbook -i inventory --tags backup_one_by_one  backup_restor.yml

ansible-playbook -i inventory --tags nova_backup  backup_restor.yml

ansible-playbook -i inventory --tags cinder_backup  backup_restor.yml

ansible-playbook -i inventory --tags keystone_backup  backup_restor.yml

ansible-playbook -i inventory --tags neutron_backup  backup_restor.yml

ansible-playbook -i inventory --tags placement_backup  backup_restor.yml

ansible-playbook -i inventory --tags rally_backup  backup_restor.yml


## restart mariadb
ansible-playbook -i inventory --tags mysql_restart  backup_restor.yml

## Restore openstack database
 
ansible-playbook -i inventory --tags restore backup_restor.yml

ansible-playbook -i inventory --tags resotor_one_by_one  backup_restor.yml

ansible-playbook -i inventory --tags nova_restore  backup_restor.yml

ansible-playbook -i inventory --tags cinder_restore  backup_restor.yml

ansible-playbook -i inventory --tags keystone_restore  backup_restor.yml

ansible-playbook -i inventory --tags neutron_restore  backup_restor.yml

ansible-playbook -i inventory --tags placement_restore  backup_restor.yml

ansible-playbook -i inventory --tags rally_restore  backup_restor.yml





## destroy lxc container in galera cluster
ansible-playbook -i inventory --tags galera_destroy  destroy_container_galera_cluster.yml

## reconviguration galera cluster in openstack (lxc)
ansible-playbook -i inventory --tags galera_infra  reconfigure_galera_cluster.yml


