Vagrant.configure("2") do |config|

  config.vm.box     = 'puppetlabs/ubuntu-14.04-64-nocm'

  #network
  config.vm.network "private_network", ip: "192.168.33.10"
  
  #shared
  #config.vm.synced_folder "/home/mitch/prog", "/projects", type: 'nfs'

  #virtualbox
  if defined? VagrantVbguest
    config.vbguest.auto_update = true
  end
  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.manifest_file  = "init.pp"
    puppet.module_path = "modules"
    puppet.options = "--verbose --debug"
    #puppet.options = "--verbose --noop"
  end
end
