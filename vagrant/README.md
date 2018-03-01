# NOTES

* Go here: https://github.com/rancher/os/releases, find version, download checksums.txt.  Find your version's rancheros.iso's md5 checksum in that file.
* Here I'm using 1.2.0:

```
$ export RANCHEROS_VERSION=1.2.0
$ export RANCHEROS_MD5_ISO_CHECKSUM=1fb7678b59d159161b2c672ba0e80214
$ packer validate rancheros-vagrant.json
$ packer build rancheros-vagrant.json
$ vagrant box add rancheros-1.2.0-x64 ./output/vagrant/x86_64/prod/1.2.0/rancheros_virtualbox.box
```

* futzing to get vagrant working: https://github.com/ailispaw/rancheros-iso-box/issues/2
* relatedly: https://github.com/ailispaw/rancheros-iso-box

* If you're running Vagrant 1.9.4, it comes installed hopelessly broken.  To fix, see https://github.com/hashicorp/vagrant/issues/8519:

```
$ vagrant plugin install vagrant-share --plugin-version 1.1.8
```

No idea why the version, why vagrant comes installed without being able to do vagrant --help.

* better Vagrantfile: https://github.com/rancher/os-vagrant

* when creating a new cluster in rancher, with a rancheros node in vbox, be sure to use the vboxnet0 interface (eth1) IP address, e.g.,
192.168.56.102+).  Set user name to rancher and specify the correct private ip.  Choose this node for etcd and management.

* to register vagrant node with rancher, in rancher, go to "Nodes".  Add node, choose custom.  scroll to the
bottom.  Select "Run a docker container on one or more nodes to register them."  copy the command "docker run...".
then vagrant ssh into the box and run it (with sudo).  You'll see "1 new node has registered" in rancher

