knife-zero example with Vagrant
===============================

# Demo

* Up two VMs in private_network
* Run build-essential cookbook to these VMs with knife-zero.

# Requirements

Tested with:

* Yosemite 10.10.5
* Vagrant 1.7.4
* VirtualBox 5.0.0
* ruby 2.2.3
* chef 12.4.1
* knife-zero 1.7.1
* berkshelf 3.3.0
* direnv 2.6.0
* CentOS 7.1(VM on VirtualBox)

# Usage

```bash
% git clone git@github.com:kwhrtsk/knife_zero_example.git
% cd knife_zero_example
% direnv allow
% vagrant up
% bundle install --path=vendor/bundle --binstubs
% ./bin/berks vendor cookbooks
% ./bin/knife zero bootstrap $VAGRANT_HOST001
% ./bin/knife zero bootstrap $VAGRANT_HOST002
% ./bin/knife exec -E "search(:node, 'hostname:host001'){|n| n.normal['chef_ip'] = ENV['VAGRANT_HOST001']; n.save}"
% ./bin/knife exec -E "search(:node, 'hostname:host002'){|n| n.normal['chef_ip'] = ENV['VAGRANT_HOST002']; n.save}"
% ./bin/knife node run_list set host001.example build-essential
% ./bin/knife node run_list set host002.example build-essential
% ./bin/knife zero converge 'name:*.example' -a chef_ip
```

# More info

In Japanese: http://blog.chopschips.net/blog/2015/08/25/vagrant-knife-zero-best-practice/
