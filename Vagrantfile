# Vagrantfile for the proxy VM

Vagrant.configure("2") do |config|

  config.vm.define "zg-docker-host", primary: true do |dhost|

    dhost.vm.box = "dduportal/boot2docker"
    dhost.vm.box_version = "= 1.5.0"

    dhost.vm.network :private_network, ip: "192.168.100.200"

    dhost.vm.provider "virtualbox" do |v|
      # On VirtualBox, we don't have guest additions or a functional vboxsf
      # in TinyCore Linux, so tell Vagrant that so it can be smarter.
      v.name = "zg-docker-host"
      v.check_guest_additions = false
      v.memory = 2048
    end

    # b2d doesn't support NFS
    dhost.nfs.functional = false

    dhost.vm.network "forwarded_port", guest: 8080, host: 8080
    dhost.vm.network "forwarded_port", guest: 3000, host: 3000
    dhost.vm.network "forwarded_port", guest: 3232, host: 3232
    dhost.vm.network "forwarded_port", guest: 8888, host: 8888

  end

end