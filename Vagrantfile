# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    
    config.vm.box = "bento/ubuntu-18.04"
    config.vm.network "private_network", ip: "192.168.33.10"
    config.ssh.insert_key = false
    
    config.vm.hostname = "shopware.dev"
    config.vm.provider :virtualbox do |v|
        v.name = "shopware.dev"
        v.memory = "4096"
        v.cpus = 2
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--ioapic", "on"]
    end
    
    config.vm.provision "ansible_local" do |ansible|
        ansible.compatibility_mode = "2.0"
        ansible.playbook = "ansible/playbook.yml"
    end

end
