# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "admin" , primary: true do |admin|
    admin.vm.box = "centos-6.4-x86_64"
    admin.vm.box_url = "https://dl.dropboxusercontent.com/u/97268835/boxes/centos-6.4-x86_64.box"

    admin.vm.hostname = "admin.example.com"
    # admin.vm.network :forwarded_port, guest: 80, host: 8888 ,auto_correct: true
    # admin.vm.network :forwarded_port, guest: 7001, host: 7001, auto_correct: false
    admin.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
  
    admin.vm.network :private_network, ip: "192.168.50.20"
  
    # admin.vm.network :public_network
    # admin.ssh.forward_agent = true
    # admin.vm.synced_folder "../data", "/vagrant_data"
  
    admin.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      # vb.customize ["modifyvm", :id, "--name", "admin"]
    end
  
    admin.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    
    admin.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "site.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
  
      puppet.facter = {
        "environment" => "development",
        "vm_type"     => "vagrant",
      }
      
    end
  
  end
  
  config.vm.define "node1" do |node1|

    node1.vm.box = "centos-6.4-x86_64"
    node1.vm.box_url = "https://dl.dropboxusercontent.com/u/97268835/boxes/centos-6.4-x86_64.box"
  
    node1.vm.hostname = "node1.example.com"
    #node1.vm.network :forwarded_port, guest: 8002, host: 8002, auto_correct: true
  
    node1.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
  
    node1.vm.network :private_network, ip: "192.168.50.100"
  
    # node1.vm.network :public_network
    # node1.ssh.forward_agent = true
    # node1.vm.synced_folder "../data", "/vagrant_data"
  
    node1.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1532"]
      # vb.customize ["modifyvm", :id, "--name", "node1"]
    end
  
    node1.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    
    node1.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "node.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
  
      puppet.facter = {
        "environment" => "development",
        "vm_type"     => "vagrant",
      }
      
    end

  end

  config.vm.define "node2" do |node2|

    node2.vm.box = "centos-6.4-x86_64"
    node2.vm.box_url = "https://dl.dropboxusercontent.com/u/97268835/boxes/centos-6.4-x86_64.box"

    node2.vm.hostname = "node2.example.com"
    #node2.vm.network :forwarded_port, guest: 8001, host: 8001
  
    node2.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]
  
    node2.vm.network :private_network, ip: "192.168.50.200", auto_correct: true
  
    # node2.vm.network :public_network
    # node2.ssh.forward_agent = true
    # node2.vm.synced_folder "../data", "/vagrant_data"
  
    node2.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "1532"]
      # vb.customize ["modifyvm", :id, "--name", "node2"]
    end
  
    node2.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml"
    
    node2.vm.provision :puppet do |puppet|
      puppet.manifests_path    = "puppet/manifests"
      puppet.module_path       = "puppet/modules"
      puppet.manifest_file     = "node.pp"
      puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"
  
      puppet.facter = {
        "environment" => "development",
        "vm_type"     => "vagrant",
      }
      
    end

  end

  config.vm.define "xe11gps6" do |xe11gps6|


    xe11gps6.vm.box = "centos-6.4-x86_64"
    xe11gps6.vm.box_url = "https://dl.dropboxusercontent.com/u/97268835/boxes/centos-6.4-x86_64.box"
    xe11gps6.vm.hostname = "xe11g.example.com"
    xe11gps6.vm.network "private_network", ip: "192.168.50.5"
    # xe11gps6.vm.network "forwarded_port", guest:22, host: 2200, auto_correct: true
    # xe11gps6.vm.network "forwarded_port", guest: 8080, host: 8080
    # xe11g.vm.network "forwarded_port", guest: 1521, host: 1521

    xe11gps6.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]

    xe11gps6.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "512"]
    end
    
    xe11gps6.vm.provision :puppet do |puppet|
      puppet.manifests_path = "puppet/manifests"
      puppet.module_path = "puppet/modules"
      puppet.manifest_file  = "site_xe11g.pp"
      puppet.options = "--verbose"
    end

  end


end
