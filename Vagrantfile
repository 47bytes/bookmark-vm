# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.require_version ">= 1.7"

Vagrant.configure("2") do |config|

  config.ssh.forward_agent = true
  config.vm.box = "debian/jessie64"

  config.vm.hostname = "bookmark.localdomain"

  #config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.network "public_network"
  #config.vm.network :private_network, ip: "192.168.56.10", nic_type: "virtio", :adapter => 2
  #config.vm.network :private_network, ip: "192.168.56.11", nic_type: "virtio", :adapter => 3

  config.vm.provider "virtualbox" do |v|
    v.name = "bookmark.localdomain"
    v.customize ['modifyvm', :id, '--nictype1', 'virtio']
    v.customize ['modifyvm', :id, '--cpus', 1]
  end

  config.vm.provision "ansible_local" do |a|
    a.playbook = "playbook.yml"
    a.verbose = 'vvv'
  end

end
