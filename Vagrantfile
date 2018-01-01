# encoding: utf-8
# -*- mode: ruby -*-
# vim: set ft=ruby :

VAGRANTBOX1 = 'bento/fedora-26'
VAGRANTBOX2 = 'bento/ubuntu-17.10'
VM1NAME = 'fedora'
VM2NAME = 'ubuntu'

Vagrant.configure("2") do |config|
  config.vm.define VM1NAME do |fedora|
    fedora.vm.box = VAGRANTBOX1
    fedora.vm.network "private_network", ip: "192.168.120.2", netmask: "255.255.255.0"
    fedora.vm.hostname = VM1NAME + ".lpic"
    fedora.ssh.port = 2240
    fedora.vm.network "forwarded_port", guest: 22, host: fedora.ssh.port
    fedora.vm.synced_folder "./fedora_synced_folder", "/vagrant", type: "rsync",
        rsync__exclude: ".git/",
        rsync__args: ["--verbose", "--rsync-path='sudo rsync'", "--archive", "--delete", "-z"]
    fedora.vm.provision "shell", path: "./_vagrant/salt/install_fedora.sh"
  end

  config.vm.define VM2NAME do |ubuntu|
    ubuntu.vm.box = VAGRANTBOX2
    ubuntu.vm.network "private_network", ip: "192.168.120.3", netmask: "255.255.255.0"
    ubuntu.vm.hostname = VM2NAME + ".lpic"
    ubuntu.ssh.port = 2241
    ubuntu.vm.network "forwarded_port", guest: 22, host: ubuntu.ssh.port
    ubuntu.vm.synced_folder "./ubuntu_synced_folder", "/vagrant", type: "rsync",
        rsync__exclude: ".git/",
        rsync__args: ["--verbose", "--rsync-path='sudo rsync'", "--archive", "--delete", "-z"]
    ubuntu.vm.provision "shell", path: "./_vagrant/salt/install_ubuntu.sh"
  end
end
