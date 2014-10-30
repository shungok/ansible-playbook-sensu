# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "centos65-x86_64-20140116"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

  config.vm.define :smonitor do |host|
    host.vm.hostname = "smonitor"
    host.vm.network "private_network", ip: "192.168.33.11"
  end

  config.vm.define :sagent do |host|
    host.vm.hostname = "sagent"
    host.vm.network "private_network", ip: "192.168.33.12"
  end

end
