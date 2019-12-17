# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  
   #Creating Proxy Server
  config.vm.define "proxy" do |proxy|
    proxy.vm.box = 'centos/7'
    proxy.vm.hostname = "proxy.vagrant.local"
    proxy.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

   #Inline Shell Provision
   proxy.vm.provision "shell",
   inline: "sudo yum update;"

   
    #Configuring Memory and CPUS
    proxy.vm.provider :virtualbox do |v|
      v.memory = 512
      v.cpus = 2
    end
  end

  #Creating App 
   config.vm.define "app" do |app|
    app.vm.box = "ubuntu/trusty64"
    app.vm.hostname = "app.vagrant.local"
    app.vm.network "forwarded_port", guest: 80, host: 8081, host_ip: "127.0.0.1"

    #Inline Shell Provisioning
    app.vm.provision "shell",
      inline: "sudo apt-get update"

    #Configuring Memory and CPUS
    app.vm.provider :virtualbox do |v|
      v.memory = 512
      v.cpus = 2
    end
  end
end