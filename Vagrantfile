Vagrant.configure("2") do |config|
  config.vm.box = "bento/fedora-26"

  config.vm.define "lpic_fedora" do |lf|
    lf.vm.network "private_network", ip: "192.168.120.99", netmask: "255.255.255.0"
    lf.vm.hostname = "fedora.lpic"
    lf.ssh.port = 2224
    lf.vm.network "forwarded_port", guest: 22, host: lf.ssh.port
    lf.vm.synced_folder "./payload", "/vagrant", type: "rsync",
        rsync__exclude: ".git/",
        rsync__args: ["--verbose", "--rsync-path='sudo rsync'", "--archive", "--delete", "-z"]
  end
end
