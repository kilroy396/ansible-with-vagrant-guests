# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configuration.
  #config.vm.box = "geerlingguy/centos7"
  #config.vm.box = "centos/7"
  config.vm.box = "kilroy396/centos7-h"
  #config.vm.box = "ubuntu/trusty64"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.linked_clone = true
  end

  # Some server 1.
  config.vm.define "server1" do |app|
    app.vm.hostname = "server1.dev"
    app.vm.network :private_network, ip: "192.168.60.4"
  end
  
  # Some server 2.
  config.vm.define "server2" do |app|
    app.vm.hostname = "server2.dev"
    app.vm.network :private_network, ip: "192.168.60.5"
  end
  
  # Some server 3.
  config.vm.define "server3" do |db|
    db.vm.hostname = "server3.dev"
    db.vm.network :private_network, ip: "192.168.60.6"
  end
end