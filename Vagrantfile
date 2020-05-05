# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX = "gdams/solaris11.3"
Vagrant.configure("2") do |config|
  config.vm.define "server" do |subconfig|
    subconfig.vm.box = BOX
    subconfig.vm.box_version = "1.0.0"
    subconfig.vm.network "public_network", use_dhcp_assigned_default_route: true
    subconfig.vm.hostname = "server-jovanny"
    subconfig.vm.provision "shell", inline: <<-SHELL
	      echo Soy el servidor
        pkg install pkg:/service/network/dns/bind
        mkdir /var/named/
    SHELL
  end

  config.vm.define "client" do |subconfig|
    subconfig.vm.box = BOX
    subconfig.vm.box_version = "1.0.0"
    subconfig.vm.hostname = "client-jovanny"
    subconfig.vm.network "public_network", use_dhcp_assigned_default_route: true
    subconfig.vm.provision "shell", inline: <<-SHELL
        echo Soy el cliente
        pkg install service/network/dns/bind
    SHELL
  end
end
