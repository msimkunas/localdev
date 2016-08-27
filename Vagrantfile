# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.synced_folder "./data", "/vagrant", type: "rsync", owner: "vagrant", group: "vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "docker"

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y vim tmux git silversearcher-ag ranger
      git clone --recursive https://github.com/msimkunas/dotfiles.git ~/.dotfiles
      bash ~/.dotfiles/install.sh -u vagrant -c
  SHELL
end
