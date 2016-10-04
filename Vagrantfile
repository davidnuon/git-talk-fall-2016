# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "private_network", ip: "33.33.33.33"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2 git nodejs nodejs-legacy npm
    sudo npm -g install ungit
    sudo service apache2 restart

    mkdir -p /home/vagrant/repos/
    chown -R vagrant:vagrant /home/vagrant/repos/
    ln -s /home/vagrant/repos /var/www/html/repos
    cp /vagrant/demo-files.tar.gz /home/vagrant/
    chown vagrant:vagrant /home/vagrant/demo-files.tar.gz
  SHELL
end
