# encoding: utf-8
# -*- mode: ruby -*-
# vim: set ft=ruby :

VAGRANT_BOX = 'bento/fedora-26'
VM_NAME = 'fedora'

Vagrant.configure("2") do |config|
  config.vm.box = VAGRANT_BOX

  config.vm.define VM_NAME do |f|
    f.vm.network "private_network", ip: "192.168.120.99", netmask: "255.255.255.0"
    f.vm.hostname = "fedora.lpic"
    f.ssh.port = 2224
    f.vm.network "forwarded_port", guest: 22, host: f.ssh.port
    f.vm.synced_folder "./fedora_synced_folder", "/vagrant", type: "rsync",
        rsync__exclude: ".git/",
        rsync__args: ["--verbose", "--rsync-path='sudo rsync'", "--archive", "--delete", "-z"]
    f.vm.provision "shell", path: "./_vagrant/salt/install"
  end
end
