# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  #Set up the node/s first
  config.vm.define "node" do |node|
    node.vm.provision "shell", inline: "echo Node, checking in"
    node.vm.box = "bento/centos-7.3"
    node.vm.network "private_network", ip: "192.168.56.31"
  end

  #The master machine will have ansible and  be used to configure the other nodes
  #This is a windows specific issue as ansible cannot be run locally
  config.vm.define "master", primary: true do |subconfig|
    subconfig.vm.box = "bento/centos-7.3"
    subconfig.vm.network "private_network", ip: "192.168.56.30"
    subconfig.vm.provider :virtualbox do |vb|
      vb.memory = "1024"
    end

    #subconfig.vm.provision "ansible_local" do |ansible|
    #  ansible.playbook = "provisioning/playbook.yml"
    #end

  end

end
