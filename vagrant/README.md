# NOTES

* Go here: https://github.com/rancher/os/releases, find version, download checksums.txt.  Find your version's rancheros.iso's md5 checksum in that file.
* Here I'm using 1.2.0:

```
$ export RANCHEROS_VERSION=1.2.0
$ export RANCHEROS_MD5_ISO_CHECKSUM=1fb7678b59d159161b2c672ba0e80214
$ packer verify rancheros-vagrant.json
$ packer build rancheros-vagrant.json
```

* futzing to get vagrant working: https://github.com/ailispaw/rancheros-iso-box/issues/2
* relatedly: https://github.com/ailispaw/rancheros-iso-box

* If you're running Vagrant 1.9.4, it comes installed hopelessly broken.  To fix, see https://github.com/hashicorp/vagrant/issues/8519:

```
$ vagrant plugin install vagrant-share --plugin-version 1.1.8
```

No idea why the version, why vagrant comes installed without being able to do vagrant --help.

* better Vagrantfile: https://github.com/rancher/os-vagrant
