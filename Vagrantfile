# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"
  config.vm.network "private_network", ip: "55.55.55.101"
  config.vm.synced_folder ".", "/home/vagrant/shared/"

  # Customize the VirtualBox instance
  config.vm.provider :virtualbox do |provider|
    provider.customize ["modifyvm", :id, "--memory", "4096"]
    provider.destroy_unused_network_interfaces = true
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update     
    sudo apt-get install -y wget
    sudo apt-get install -y curl
    sudo apt-get install -y vim
    sudo apt-get install -y git    
    sudo apt-get install -y build-essential
     
    #
    # Installs Python pip for python 2 and 3
    #
    sudo wget https://bootstrap.pypa.io/get-pip.py
    sudo python2 get-pip.py
    sudo python3 get-pip.py

    #
    # Install Python Machine Learning: scikit-learn
    #
    sudo apt-get install -y python-numpy python-scipy python-matplotlib ipython ipython-notebook python-pandas python-sympy python-nose python-scikits-learn
    sudo apt-get install -y build-essential python3-dev python3-setuptools python3-numpy python3-scipy libatlas-dev libatlas3gf-base
    sudo pip3 install -U scikit-learn
  SHELL

end
