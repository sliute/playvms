# playvms
Two Vagrant-powered VMs (Fedora 26 and Ubuntu 17.10) to play with.

## Usage
1. Clone and run `vagrant up`.
2. The Ubuntu VM will quack, because 17.10 no longer has 'ifup' and 'ifdown' enabled by default (all hail 'netplan'!).
3. Therefore, quickfix: `vagrant ssh ubuntu`, run `sudo apt-get install ifupdown`, then `exit` and `vagrant reload ubuntu`.
4. Copy files into the VMs 'vagrant' folders via 'rsync' from the two aptly named directories on your local machine.
