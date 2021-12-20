# checkBackup.yml
# check database backup 

Using this playbook, the openstack database backup validation process is performed.

This process is performed in three steps:

## First Step 
Check the backup file size. If the new backup file size is less than the old backup file size, the PlayBook will be fail.

## Second Step 
Restore backup and run two queries for testing.

## Third Step 
Delete the backup file


## variables

* pass1: mysql root password
* backup_dir: path of backup file

