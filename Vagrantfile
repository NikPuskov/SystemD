# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

Vagrant.configure("2") do |config|
  

  config.vm.box = "ubuntu/jammy64"
  config.vm.box_check_update = false
  config.vm.network "public_network"
  config.vm.provider "virtualbox" do |vb|
  
     vb.gui = false
  
     vb.memory = "8192"
     vb.cpus = "4"
     vb.name = "systemd"
  end
   
  #config.vm.provision "shell", inline: <<-SHELL
      #apt update
      #apt -y full-upgrade
      #reboot           
  #SHELL
end
