Vagrant.configure(2) do |config|
  config.vm.box = "chef/centos-7.1"

  config.vm.define :host001 do |host|
    host.vm.hostname = "host001.example"
    host.vm.network "private_network", ip: ENV['VAGRANT_HOST001']
  end

  config.vm.define :host002 do |host|
    host.vm.hostname = "host002.example"
    host.vm.network "private_network", ip: ENV['VAGRANT_HOST002']
  end

  # VMにログインする鍵を固定
  config.ssh.insert_key = false
end
