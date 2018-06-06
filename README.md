Ansible-mesos - Ansible Playbook for Mesos
=============
The ansible-mesos role supports the installation and configuration of a mesos cluster with options for master, slave or a master-slave setup. It is restricted to ubuntu environment.

Installation
-----------

Dependencies
------------
1. Java
2. Zookeeper
    - https://github.com/vakees1424/Ansible-zookeeper


Requirements
------------
Ansible version at least 2.0

Vault file creation process
------------
Move to the below folder and `remove the existing main.yml file`
>$cd Ansible-mesos/vars/

Now run the below mentioned command and create a password for the vault file

>$ansible-vault create main.yml 

Enter the below values in the vault file
```
---
ansible_connection: ssh
ansible_ssh_user: XXXX #user name of the host machine which should have sudo permission
ansible_ssh_pass: YYYY #Password for the username
ansible_sudo_pass: YYYY #Password for the username --> this will be used for sudo permissions
```
How to add the details in inventory
------------
```
[master]
Please add the hosts that you want to create them as mesos-master
[slave]
Please add the hosts that you want to create them as mesos-salves

```
Example:
```
[master]
ec2-xx-xxx-xx-xxx.us-west-2.compute.amazonaws.com
ec2-xx-xxx-xx-xxx.us-west-2.compute.amazonaws.com


[slave]
ec2-yy-yyy-yy-yyy.us-west-2.compute.amazonaws.com
ec2-yy-yyy-yyy-yyy.us-west-2.compute.amazonaws.com

```
>**please add the hostname in both([master] and [slave])if you want them to be master as well as slave**

How to run 
------------
```ansible-playbook -i inventory -K all.yml --ask-vault ```

Author Information
------------------
[vakees](https://github.com/vakees1424)
