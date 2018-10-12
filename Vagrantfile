# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
    vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
  end

  config.vm.define "centos" do |centos|
    centos.vm.box = "puppetlabs/centos-7.0-64-puppet"
    #centos.vm.network "forwarded_port", guest: 3000, host: 3000, protocol: "tcp"
    # http://postgrest.org/en/v5.1/install.html#build-from-source
    centos.vm.provision "shell", inline: <<-SHELL
      # system deps
      sudo yum -y install emacs man git
      sudo yum -y install postgresql-devel zlib-devel gmp-devel
      sudo yum -y install install perl make automake gcc gmp-devel libffi zlib xz tar git gnupg
      # git clone git@github.com:leondutoit/postgrest.git
      # git co get-read-write-transaction
      # /vagrant/stack-1.7.1-linux-x86_64/stack build --allow-different-user --install-ghc --copy-bins --local-bin-path /usr/local/bin
    SHELL
  end

end
