# -*- mode: ruby -*-
# vi: set ft=ruby :

# Basic Config.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
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
    echo "Installing base packages"
    apt-get update
    apt-get install -y \
      git \
      zsh
  SHELL

  config.vm.provision "shell", privileged: false, inline:
  <<-SHELL
    echo "Cloning Oh My Zsh from the git repo" 
    git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
    echo "Copying the default .zshrc config file"
    cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
    echo "Changing the Oh_My_zsh theme"
    sed -i 's/robbyrussell/agnoster/g' ~/.zshrc
  SHELL
  
  config.vm.provision "shell", inline:
  <<-SHELL
    echo "Changing the vagrant user's shell to use zsh"
    chsh -s /bin/zsh vagrant
  SHELL
############################################################
end
