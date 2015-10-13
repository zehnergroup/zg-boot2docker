# Vagrantfile for the proxy VM

Vagrant.configure("2") do |config|

  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end

  config.vm.define "zg-docker-host", primary: true do |dhost|

    dhost.vm.box = "ailispaw/rancheros-lite"

    dhost.vm.network :private_network, ip: "192.168.100.200"

    dhost.vm.provider "virtualbox" do |v|
      v.name = "zg-docker-host"
      v.memory = 2048
    end

    # dhost.vm.network "forwarded_port", guest: 8080, host: 8080
    # dhost.vm.network "forwarded_port", guest: 3000, host: 3000
    # dhost.vm.network "forwarded_port", guest: 3232, host: 3232
    # dhost.vm.network "forwarded_port", guest: 8888, host: 8888
    # dhost.vm.network "forwarded_port", guest: 8003, host: 8003

  end

end
