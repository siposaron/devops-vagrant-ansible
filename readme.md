# Vagrant with Ansible


## Description

This is a basic setup of vagrant project with ansible and shell script provisioning.


## Requirements

* Vagrant: v2.2.9
* Virtual box: v6.1


## Run

1. Start vagrant: `vagrant up`
2. Provision with ansible:
   1. `vagrant ssh ansible` >> log into the ansible named box
   2. `ssh apache` >> from the ansible machine connect to apache machine and accept its public key (otherwise ansible commands won't run)
   3. `exit` >> leave the apache box, get back into ansible box
   4. `cd /vagrant` >> switch to the shared vagrant directory
   5. `ansible-playbook -i hosts.yml playbook.yml` >> provision the apache box with apache2 from the ansible box
3. Check apache response in local browser by simply typing the IP address of the apache box `192.168.33.11` >> should display a simple bionic message (index.html)