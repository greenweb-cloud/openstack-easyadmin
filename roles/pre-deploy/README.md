#Role Name
=========

A brief description of the role goes here.


## First, we explain the general working method for a better understanding of server configuration before deployment.
`Here we have three important parts in the **task** file, which we explain in order and briefly state their purpose.`

  ```mermaid
graph LR
A[dependency.yml]
```
|Task Name       |Descriptionn                   |                             |
|----------------|-------------------------------|-----------------------------|
|Repo            | `'add repository apt we need`        |                      |
|Apt update      |`"Updating all things in the server"`                        |            
|Packages        |`install some package and remove some package ` |you can see in default file
|dist upgrade    |`upgrading packages to latest version`|                      |
|Configure module|`add some module`                     |kernel modules We need that should be loaded at boot time,bonding=>network bonding , 802.14=>standard for VLANs , /etc/module|
|Configure DNS|`adding your DNS server`                 |/etc/systemd/resolv.conf |
|Configure hosts|`_node must contain entries for the local host_`| /etc/hosts|
|Clean up|`directory`| /openstack /etc/haproxy /etc/keepalived|
|Clean up|`LXC containers`||

  ```mermaid
graph LR
A[ntp.yml]
```
|Task Name       |Descriptionn                   |                             |
|----------------|-------------------------------|-----------------------------|
|Set time zone   | `'Add Your cloud time zone`   |                             |
|Install Chrony  |`"a refrence implemeentaion of NTP"`             |   make sure chrony daemon is run         |
|Configure NTP         |`Network time Protocol for All servers are be at the same time` |/etc/chrony/chrony.conf |



  ```mermaid
graph LR
A[Network Manger.yml]
```
|Task Name       |Descriptionn                   |                             |
|----------------|-------------------------------|-----------------------------|
|Packages        | `'install some package and remove some package `        |you can see in default file            |
|Configure network for nodes  |`"Configure interfaces"`            | /etc/network/interface   
|Ceph  |`Configure network for ceph monitor node , Software defiend storage`            | /etc/network/interface        
|Remove all Netplan And Add Configure We need      | |/etc/netplan





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

```
ansible-playbook -i inventory pre-deploy.yml --tags compute -e 'machine=compute'
```

```
ansible-playbook -i inventory pre-deploy.yml --tags infra -e 'machine=infra'
```

License
-------
BSD

Author Information
------------------
+ Ansible role by [iman darabi]<iman.darabi@gmail.com>
