Ansible Infra Backup 
=========

in this Role we backup data from Infras including bellow

* LXC data
* /etc/network 
* /etc/neutron
* /etc/haproxy 
* /etc/keepalived 

here is the way it all works.
we have a nfs server which we wanna use it as storage backend for backup.
first we mount nfs in proper location in all infras , then we list all lxc container and do a backup script for each of them
then we backup some config data in those servers. 


in lxc-backup stage we impelement some sort of strategy which is like this:
 * disable backend lxc server in haproxy - (we must perform this task on only machine that has floating IP)
 * stop lxc container
 * backup stage 
 * start lxc container
 * enable backend lxc server in haproxy - (we must perform this task on only machine that has floating IP)


Requirements
------------

before we move on we need to instalol dependencied . here is the file named req.yml which is contained of all dependencies collections of this role to install those dependencies run the bwllow command.

```sh
ansible-galaxy collections install -r req.yml

```


Role Useage
--------------

First you need to fill all needed Variables in default/main.yml

fip in this file is stands for Floating IP(which is controlled by keepalived)

file test/inventories consist of sample inv file  so edit it as you wish 

then run the command bellow to start the role. 

```sh
cd test/ ansible-playbook -i inventories test.yml

```
