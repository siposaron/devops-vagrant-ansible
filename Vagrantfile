# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "hashicorp/bionic64"
    ansible.vm.network "private_network", ip: "192.168.33.10"
    ansible.vm.hostname = "ansible"
    ansible.vm.synced_folder "./ansible", "/vagrant"
    ansible.vm.provider "virtualbox" do |vb|
      vb.name = "ansible"
      vb.memory = "1024"
    end
    ansible.vm.provision :shell, path: "bootstrap_ansible.sh"
  end

  config.vm.define "apache" do |apache|
    apache.vm.box = "hashicorp/bionic64"
    apache.vm.network "private_network", ip: "192.168.33.11"
    apache.vm.hostname = "apache"
    apache.vm.synced_folder "./html", "/vagrant/html"
    apache.vm.provider "virtualbox" do |vb|
      vb.name = "apache"
      vb.memory = "1024"
    end
    # use the shell script provisioner if you do not want ansible
    # apache.vm.provision :shell, path: "bootstrap_apache.sh"
  end

  config.vm.define "node" do |node|
    node.vm.box = "generic/alpine312"  #cgops/alpine-3.12
    node.vm.network "private_network", ip: "192.168.33.12"
    node.vm.hostname = "node"
    node.vm.synced_folder "./js", "/vagrant/js", type: "nfs"
    node.vm.provider "virtualbox" do |vb|
      vb.name = "node"
      vb.memory = "256"
    end
    node.vm.provision :shell, path: "bootstrap_node.sh"
  end
end
