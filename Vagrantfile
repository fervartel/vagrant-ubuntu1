# -*- mode: ruby -*-
# vi: set ft=ruby :

# Basic Config.
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.hostname = "ubuntu1"
  #config.vm.network "private_network", type: "dhcp"  
  config.vm.network "private_network", ip: "10.0.0.3"  

# VirtualBox specific:
  config.vm.provider "virtualbox" do |vb|
	vb.name = "vagrant-ubuntu1"
  end
    
############################################################
  # Oh My ZSH Install section
  config.vm.provision "shell", inline:
  <<-SHELL
    echo "INSTALLING BASE PACKAGES"
    apt-get update
    apt-get install -y \
      git \
      zsh
  SHELL

  config.vm.provision "shell", privileged: false, inline:
  <<-SHELL
    echo "CLONING OH MY ZSH FROM THE GIT REPO" 
    git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
    echo "COPYING DEFAULT .zshrc CONFIG FILE"
    cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
    echo "CHANGING THE OH_MY_ZSH THEME"
    sed -i 's/ZSH_THEME="robbyrussell"/ZSH_THEME="agnoster"/' ~/.zshrc
  SHELL
  
  config.vm.provision "shell", inline:
  <<-SHELL
    echo "CHANGING THE VAGRANT USER'S SHELL TO USE ZSH"
    chsh -s /bin/zsh vagrant
  SHELL
############################################################
end
