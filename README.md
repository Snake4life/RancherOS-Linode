# RancherOS OVH installer


## Installation steps

Boot OVH VM into Rescue Mode first, connect via ssh and run the script

```
sysctl net.ipv6.conf.eth0.disable_ipv6=1
apt-get -qq update
apt-get -qq install ca-certificates
apt-get -qq install parted
wget -q https://raw.githubusercontent.com/Snake4life/RancherOS-OVH/master/install.sh
chmod +x install.sh
# create or fetch your own cloud-config.yml file
./install.sh -c cloud-config.yml -d /dev/sdb -v X.X.X
```

## Command line arguments

Optionally, you can specify the following commandline arguments to the `install.sh` script:

* `-c`: pass a cloud-config YAML file to the installer
  * Example: `-c cloud-config.yml`
  * Default: generates an empty cloud-config to use for the installation
* `-d`: disk device to install to - warning: will be wiped!
  * Example: `-d /dev/sda`
  * Default: attempts to auto-detect a disk device (either /dev/sda or /dev/vda)
* `-v`: RancherOS release version to install
  * Example: `-v 0.4.2`
  * Default: the current RancherOS release (fetched from the [release list](https://releases.rancher.com/os/releases.yml))

## Authors

* Robbert Klarenbeek, <robbertkl@renbeek.nl> - main install script
* Snake4life - OVH mod

## License

This repo is published under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
