Role Name
=========

A brief description of the role goes here.

Requirements
------------
use this role from openstack-ansible deployment server 

Role Variables
--------------
variables are set in default/main.yml: 
+ `disk_cinder_volumes`: name of volume in server which will be used to create "cinder-volumes" volume group.
  		EX: disk_cinder_volumes: "/dev/md0"

+ `proxy_url`: this proxy will be set in "/etc/apt/apt.conf.d/90curtin-aptproxy" file in destination servers.
  	       EX: proxy_url: "http://172.16.104.8:3128/"

+ `pkgs_remove`: packages should be removed from servers
  	       EX: pkgs_remove: ['netplan.io', 'resolvconf', 'cloud-init', 'keepalived', 'haproxy']

+ `pkgs_install`: packages should be installed on destination servers
  	       EX: pkgs_install: ['ifupdown', 'aptitude', 'bridge-utils', 'debootstrap', 'ifenslave', 'ifenslave-2.6', 'lsof', 'lvm2', 'chrony', 'emacs25-nox', 'tcpdump', 'vlan', 'python', 'nmap', 'fping', 'traceroute', 'nload', 'ethstats', 'iftop']

+ `preferred_dns`: preferred dns set to /etc/systemd/resolved.conf
  		   EX: preferred_dns: "172.16.104.1"
+ `fallback_dns`: fallback dns set to /etc/systemd/resolved.conf
  		  EX: fallback_dns: "8.8.8.8"
+ `search_domains`: search domain set to /etc/systemd/resolved.conf
  		  EX: search_domains: ["iranserver"]

Dependencies
------------
None.

Example Playbook
----------------
add the following playbook to pre-deploy.yml file for example, and run playbook by the following command: 
---
- hosts: all

  tasks:
    - name: running pre-deploy role 
      import_role:
        name: pre-deploy

you can use the following tags:
  - compute: this tag will run tasks needed by compute nodes. for example creating cinder-volumes will be run by this tag
  - infra: This tag will run tasks needed by infra nodes
  - clean-env: This tag will clean environments

examples:
	# ansible-playbook -i hosts pre-deploy.yml --tags compute
	# ansible-playbook -i hosts pre-deploy.yml --tags infra


License
-------
BSD

Author Information
------------------
+ Ansible role by [iman darabi]<iman.darabi@gmail.com>
