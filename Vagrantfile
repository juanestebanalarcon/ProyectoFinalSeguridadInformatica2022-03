Vagrant.configure("2") do |config|
    config.vm.define :vmftp do |vmftp|
    vmftp.vm.box = "kalilinux/rolling"
    vmftp.vm.network :private_network, ip: "192.168.50.2"
    vmftp.vm.hostname = "vmftp"
    end
    
    config.vm.define :vmhttp do |vmhttp|
    vmhttp.vm.box = "kalilinux/rolling"
    vmhttp.vm.network :private_network, ip: "192.168.50.3"
    vmhttp.vm.hostname = "vmhttp"
    end
    
    config.vm.define :firewall do |firewall|
    firewall.vm.box = "kalilinux/rolling"
    firewall.vm.network :public_network, ip: "192.168.1.100"
    firewall.vm.network :private_network, ip: "192.168.50.4"
    firewall.vm.network :"forwarded_port", guest: 80, host: 5000,auto_correct: true
    firewall.vm.hostname = "firewall"
    end
    
    end