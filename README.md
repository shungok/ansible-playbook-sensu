# ansible playbook for sensu monitor and agent

## Dependency

* CentOS 6.5 vagrant box file : 
  [centos65-x86_64-20140116.box](https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box, "centos65-x86_64-20140116.box")


## Way to setup

```
<<<<<<< HEAD
=======
% vagrant ssh-config smonitor > ssh_config
% vagrant ssh-config sagent  >> ssh_config
>>>>>>> first commit.
% vagrant up
% ansible-playbook site.yml
```

## Variables for your setting

``` Vagrantfile
…
host.vm.hostname = "smonitor"
host.vm.network "private_network", ip: "192.168.33.11"
…
host.vm.hostname = "sagent"
host.vm.network "private_network", ip: "192.168.33.12"
…

```

``` group_vars/all.yml
rabbitmq_ip: 192.168.33.11
rabbitmq_port: 5671
rabbitmq_sensu_user: sensu
rabbitmq_sensu_pass: sensu
rabbitmq_sensu_vhost: /sensu

sensu_api_ip: 192.168.33.11
sensu_api_port: 4567
sensu_api_user: admin
sensu_api_pass: secret

uchiwa_port: 3000
uchiwa_user: uchiwa
uchiwa_pass: uchiwa

sensu_client_name: sensu_agent_node
sensu_client_ip: 192.168.33.12
sensu_subscription_group: testgroup
```

## Description

```
% vagrant status
Current machine states:

smonitor                  running (virtualbox)
sagent                    running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.
```

"smonitor" is sensu monitor host (server, api, dashboard).  smonitor needs roles as following.

* redis
* rabbitmq
* sensu/common
* sensu/monitor

"sagent" is sensu agent host (client). sagent needs roles as following.

* sensu/common
* sensu/agent
