Vagrant.configure("2") do |config|  
#  config.vm.provider "virtualbox"
  config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.define "host1" do |host1|
    host1.vm.box = "generic/ubuntu2004"
    host1.vm.hostname = "host1"
    host1.vm.network :private_network, ip: "192.168.20.10"
  end

  config.vm.define "host2" do |host2|
    host2.vm.box = "generic/ubuntu2004"
    host2.vm.hostname = "centos8"
    host2.vm.network :private_network, ip: "192.168.20.11"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo systemctl disable systemd-resolved
    sudo rm -rf /etc/run/systemd/resolve/stub-resolv.conf /etc/resolv.conf
    sudo echo "nameserver  8.8.8.8" > /etc/resolv.conf
  SHELL

end
