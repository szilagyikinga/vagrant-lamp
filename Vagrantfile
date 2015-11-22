# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.provider :virtualbox do |v|
    v.customize [
      "modifyvm", :id,
      "--memory", 1024,
      "--cpuexecutioncap", "50",
      "--cpus", 2,
    ]
  end

  config.vm.box = "ubuntu/trusty64"
  config.vm.network :private_network, ip: "192.168.33.99"
  config.ssh.forward_agent = true
  
  config.vm.provision :ansible do |ansible|
    ansible.playbook = 'playbook.yml'
  end
  config.vm.synced_folder "./web", "/vagrant", type: "nfs"
end
