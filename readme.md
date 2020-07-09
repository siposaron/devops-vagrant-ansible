# Vagrant with Ansible


## Description

This is a basic setup of vagrant project with ansible and shell script provisioning.


## Requirements

* Vagrant: v2.2.9
* Virtual box: v6.1

On macOS you can install simply via homebrew:
`brew cask install virtualbox`
`brew cask install vagrant`
`brew cask install virtualbox-extension-pack`


## Run

1. Start vagrant: `vagrant up`
2. Provision with ansible:
   1. `vagrant ssh ansible` >> log into the ansible named box
   2. `ssh apache` >> from the ansible machine connect to apache machine and accept its access key (otherwise ansible commands won't run) & `exit` to ansible box
   3. `ssh node` >> from the ansible machine connect to node box and accept its access key (otherwise ansible commands won't run) & `exit` to ansible box
   4. `cd /vagrant` >> switch to the shared vagrant directory
   5. `ansible-playbook -i hosts.yml playbook.yml` >> provision the apache box with apache2 from the ansible box (don't stop provisioning process, it will hang at the last task starting node as it is not run in a bg process)
3. Check apache response in local browser by simply typing the IP address of the apache box `192.168.33.11` >> should display a simple bionic message (index.html)
4. Check nodejs Hello world example by accessing `192.168.33.12:3000` in browser