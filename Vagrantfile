# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  boxes = [
    {
      :name => "ie10",
      :box => "modernIE/w8-ie10"
    },
    {
      :name => "ie11",
      :box => "modernIE/w8.1-ie11"
    },
    {
      :name => "edge",
      :box => "modernIE/w10-edge"
    }
  ]

  # Configure VM's
  boxes.each do |opts|
    config.vm.define opts[:name], autostart: false do |config|

      # Set hostname
      config.vm.hostname = opts[:name]

      # Set box
      config.vm.box = opts[:box]

      # Set virtualbox settings
      config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", 2048]
        v.customize ["modifyvm", :id, "--cpus", 2]
        v.gui = true
      end

      # Disable shared folder
      config.vm.synced_folder ".", "/vagrant", disabled: true

      # Add private network
      if Vagrant.has_plugin?("vagrant-auto_network")
        config.vm.network :private_network, :ip => "0.0.0.0", :auto_network => true
      else
        warn "The recommeded plugin 'vagrant-auto_network' is currently not installed. You can install it by executing: 'vagrant plugin install vagrant-auto_network'"
      end

      # Configure hostmanager
      if Vagrant.has_plugin?("vagrant-hostmanager")
        config.hostmanager.enabled = true
        config.hostmanager.manage_host = true
        config.hostmanager.ignore_private_ip = false
        config.hostmanager.include_offline = false
      else
        warn "The recommeded plugin 'vagrant-hostmanager' is currently not installed. You can install it by executing: 'vagrant plugin install vagrant-hostmanager'"
      end
    end
  end

end
