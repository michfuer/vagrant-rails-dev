# -*- mode: ruby -*-
# vi: set ft=ruby :

# Notes::
#   Puppet for configuration.

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Ubuntu 14.04 LTS
  config.vm.box = 'ubuntu/trusty64'
  config.vm.box_url = 'https://vagrantcloud.com/ubuntu/trusty64'

  # This will likely have to be more specific for each host
  config.vm.provision 'puppet' do |puppet|
    puppet.module_path = 'modules'
  end

  config.vm.define 'dev' do |dev|
    dev.vm.hostname = 'dev'
    dev.vm.network "private_network", ip: "192.168.227.6"

    # Need to add the appropriate folders to access htdocs, etc.
    dev.vm.synced_folder 'site-root', '/app/rails', type: 'nfs'
  end

  config.vm.provider 'virtualbox' do |vb|
    # Specify the amount of memory in MB
    vb.memory = 1024
    # Specify the number of CPUs
    vb.cpus = 2
  end
end
