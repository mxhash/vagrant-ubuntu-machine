# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.box_check_update = true


  config.vm.hostname = "ws-mhein-ubuntu"

  config.vm.provider :parallels do |p, override|
    p.name = "ws-mhein-ubuntu"

    # Set power consumption mode to "Better Performance"
    p.optimize_power_consumption = false

    p.memory = 2048
    p.cpus = 2
  end

  config.vm.provider :vmware_workstation do |v, override|
    v.vmx["memsize"] = "1024"
    v.vmx["numvcpus"] = "1"
  end

  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "2048"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  end

  if File.exists?(".Vagrantfile.local") then
    eval(IO.read(".Vagrantfile.local"), binding)
  end
end
