# -*- mode: ruby -*-
# vi: set ft=ruby :

# Project-specific variables. Modify this when porting to other projects.
PROJECT = "ansible-workspace"
HOSTS_IP = "192.168.200.2"
MAX_VM_MEMORY = "1024"

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"


Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.hostname = PROJECT

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network :private_network, ip: HOSTS_IP

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/var/www/current", :nfs => true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  config.vm.provider :virtualbox do |vb|
    # Use VBoxManage to customize the VM. For example to change memory:
    vb.customize ["modifyvm", :id, "--name", PROJECT,  "--memory", MAX_VM_MEMORY]
  end

  # When troubleshooting, change from true to ansible.verbose = "vvvv"
  # config.vm.provision "ansible" do |ansible|
  #   ansible.sudo = true
  #   ansible.verbose = true
  #   ansible.playbook = "ansible/playbooks/workstation.yml"
  #   ansible.extra_vars = {
  #     env: "local",
  #   }
  #   ansible.limit = 'all'
  # end
end
