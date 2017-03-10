$inlprv=<<SCRIPT
route delete default
[ -z "$1" ] || route add default $1
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.guest = :openbsd
  config.ssh.shell = "ksh -l"
  config.ssh.username = "root"
  config.ssh.password = "vagrant"
  config.vm.box = "obsd60"
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.define "tenant1.21" do |v|
    v.vm.network :private_network, ip: "10.20.20.21"
    v.vm.hostname = "tenant1"
    v.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 128]
    end
    v.vm.provision "shell", inline: $inlprv, args: "10.20.20.254"
  end
  config.vm.define "tenant2.41" do |v|
    v.vm.network :private_network, ip: "10.40.40.52"
    v.vm.hostname = "tenant2"
    v.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 128]
    end
    v.vm.provision "shell", inline: $inlprv, args: "10.40.40.254"
  end
  config.vm.define "rdomain-gw-left", primary: true do |v|
    v.vm.network :private_network, ip: "10.20.20.254"
    v.vm.network :private_network, ip: "10.40.40.254"
    v.vm.network :private_network, ip: "10.0.123.254"
    v.vm.hostname = "rdomain-gw-left"
    v.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 256]
      vb.gui = true;
    end
    v.vm.provision "shell", inline: $inlprv
  end
  config.vm.define "rdomain-gw-right" do |v|
    v.vm.network :private_network, ip: "10.0.123.253"
    v.vm.network :private_network, ip: "172.19.82.254"
    v.vm.hostname = "rdomain-gw-right"
    v.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 128]
    end
    v.vm.provision "shell", inline: $inlprv
  end
  config.vm.define "inetsrv" do |v|
    v.vm.network :private_network, ip: "172.19.82.10"
    v.vm.hostname = "inetsrv"
    v.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", 128]
    end
    v.vm.provision "shell", inline: $inlprv, args: "172.19.82.254"
  end
end
