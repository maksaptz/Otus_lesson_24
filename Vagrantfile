# -*- mode: ruby -*-
# vim: set ft=ruby :
#Path to HDD on host

Vagrant.configure(2) do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 512 
    v.cpus = 1
  end

  config.vm.define "inetRouter" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "inetRouter"
    host.vm.network "private_network",
                     ip: "192.168.255.1",
		     netmask: "255.255.255.252",
                     virtualbox__intnet: "router-net",
                     adapter: 2
    host.vm.network "private_network",
                     ip: "0.0.0.0",
                     virtualbox__intnet: "router-net",
                     adapter: 3
    host.vm.network "private_network",
                     ip: "192.168.50.10",
                     adapter: 4
  end

  config.vm.define "centralRouter" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "centralRouter"
    host.vm.network "private_network",
                     ip: "192.168.255.2",
                     netmask: "255.255.255.252",
                     virtualbox__intnet: "router-net",
                     adapter: 2 
    host.vm.network "private_network",
                     ip: "0.0.0.0",
                     virtualbox__intnet: "router-net",
                     adapter: 3 
    host.vm.network "private_network",
                     ip: "192.168.50.11",
                     adapter: 4
  end

#  config.vm.define "office1Router" do |host|
#    host.vm.box = "debian/bullseye64"
#    host.vm.box_version = "11.20230615.1"
#    host.vm.hostname = "office1Router"
#    host.vm.network "private_network",
#                     ip: "192.168.255.10",
#                     netmask: "255.255.255.252",
#                     adapter: 2,
#                     virtualbox__intnet: "office1-central"
#    host.vm.network "private_network", 
#                     ip: "192.168.50.12",
#                     adapter: 3
#  end

  config.vm.define "testClient1" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "testClient1"
    host.vm.network "private_network",
                     ip: "0.0.0.0",
                     virtualbox__intnet: "testLAN",
                     adapter: 2
    host.vm.network "private_network",
                     ip: "192.168.50.13",
                     adapter: 3
  end

  config.vm.define "testClient2" do |host|
    host.vm.box = "ubuntu/focal64"
    host.vm.box_version = "20230922.0.0"
    host.vm.hostname = "testClient2"
    host.vm.network "private_network",
                     ip: "0.0.0.0",
                     virtualbox__intnet: "testLAN",
                     adapter: 2
    host.vm.network "private_network",
                     ip: "192.168.50.14",
                     adapter: 3
  end

  config.vm.define "testServer1" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "testServer1"
    host.vm.network "private_network",
                     ip: "0.0.0.0",
                     virtualbox__intnet: "testLAN",
                     adapter: 2
    host.vm.network "private_network",
                     ip: "192.168.50.15",
                     adapter: 3
  end

  config.vm.define "testServer2" do |host|
    host.vm.box = "ubuntu/focal64"
    host.vm.box_version = "20230922.0.0"
    host.vm.hostname = "testServer2"
    host.vm.network "private_network",
                     ip: "0.0.0.0",
                     virtualbox__intnet: "testLAN",
                     adapter: 2
    host.vm.network "private_network",
                     ip: "192.168.50.16",
                     adapter: 3

    host.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/play.yml"
      ansible.inventory_path = "ansible/hosts"
      ansible.host_key_checking = "false"
      ansible.limit = "all"
    end

  end

end
