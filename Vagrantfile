# -*- mode: ruby -*-
# vi: set ft=ruby :

# Check vagrant version
Vagrant.require_version '>= 1.8.0'

Vagrant.configure(2) do |config|
  if Vagrant.has_plugin?('vagrant-vbguest')
    config.vbguest.auto_update = true
  else
    raise("Install vagrant plugin 'vagrant-vbguest' before continuing.")
  end

  config.trigger.before :up do |trigger|
    trigger.run = { path: 'add_box.sh', args: ARGV[1] }
  end

  config.ssh.username = 'IEUser'
  config.ssh.password = 'Passw0rd!'
  config.ssh.insert_key = false

  boxes = [
    'ie11-win7',
    'ie11-win81',
    'msedge-win10'
  ]

  # Configure VM's
  boxes.each do |box|
    config.vm.define box, autostart: false do |config|
      # Set hostname
      config.vm.hostname = box

      # Set box
      config.vm.box = box

      # Set VirtualBox settings
      config.vm.provider 'virtualbox' do |v|
        v.customize ['modifyvm', :id, '--memory', 2048]
        v.customize ['modifyvm', :id, '--cpus', 2]
        v.gui = true
      end

      # Disable shared folder
      config.vm.synced_folder '.', '/vagrant', disabled: true
    end
  end
end
