# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"
Vagrant.require_version ">= 2.2.0"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_guest = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  unless Vagrant.has_plugin?("vagrant-hostmanager")
    raise 'plugin vagrant-hostmanager is not installed!'
  end

  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end

  config.vm.define "server-01" do |vmconfig|
    vmconfig.vm.hostname = "server-01"
    vmconfig.vm.box = "debian/stretch64"
    vmconfig.vm.provider :virtualbox do |vb|
#      vb.gui = true
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.customize ["modifyvm", :id, "--paravirtprovider", "default"]
    end
    # vmconfig.vm.provider "parallels" do |v, override|
    #   override.vm.box = "parallels/centos-6.7"
    # end
    # vmconfig.vm.provider "aws" do |v, override|
    #   override.vm.box = "server-01"
    # end
    vmconfig.hostmanager.aliases = %w(server-01.local)
     vmconfig.vm.network :private_network, ip: '172.28.128.101'
#    vmconfig.vm.network :private_network, type: "dhcp"
#    vmconfig.vm.network :public_network, type: "dhcp"
#    vmconfig.vm.network "forwarded_port", guest: 80, host: 8000
#     Run Ansible from the Vagrant Host
    config.vm.provision "ansible_local" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/server-01.yml"
      # ansible.playbook = "ansible/ansible-gitlab.yml"
      # ansible.galaxy_role_file = "ansible/requirements.yml"
      # ansible.galaxy_roles_path = "/etc/ansible/roles"
      ansible.raw_arguments = ["--connection=paramiko"]
      # ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
    end
  end

  config.vm.define "server-02" do |vmconfig|
    vmconfig.vm.hostname = "server-02"
    vmconfig.vm.box = "debian/stretch64"
    vmconfig.vm.provider :virtualbox do |vb|
#      vb.gui = true
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.customize ["modifyvm", :id, "--paravirtprovider", "default"]
    end
    # vmconfig.vm.provider "parallels" do |v, override|
    #   override.vm.box = "parallels/centos-6.7"
    # end
    # vmconfig.vm.provider "aws" do |v, override|
    #   override.vm.box = "server-02"
    # end
    vmconfig.hostmanager.aliases = %w(server-02)
    vmconfig.vm.network :private_network, ip: '172.28.128.102'
#    vmconfig.vm.network :private_network, type: "dhcp"
#    vmconfig.vm.network :public_network, type: "dhcp"
#    vmconfig.vm.network "forwarded_port", guest: 80, host: 8001
#     Run Ansible from the Vagrant Host
    config.vm.provision "ansible_local" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/server-02.yml"
      ansible.raw_arguments = ["--connection=paramiko"]
    end
  end

  config.vm.define "server-03" do |vmconfig|
    vmconfig.vm.hostname = "server-03"
    vmconfig.vm.box = "debian/stretch64"
    vmconfig.vm.provider :virtualbox do |vb|
      vb.gui = true
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--cpuexecutioncap", "100"]
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      vb.customize ["modifyvm", :id, "--paravirtprovider", "default"]
    end
    # vmconfig.vm.provider "parallels" do |v, override|
    #   override.vm.box = "parallels/centos-6.7"
    # end
    # vmconfig.vm.provider "aws" do |v, override|
    #   override.vm.box = "server-02"
    # end
    vmconfig.hostmanager.aliases = %w(server-03)
    vmconfig.vm.network :private_network, ip: '172.28.128.103'
#    vmconfig.vm.network :private_network, type: "dhcp"
#    vmconfig.vm.network :public_network, type: "dhcp"
#    vmconfig.vm.network "forwarded_port", guest: 80, host: 8001
#     Run Ansible from the Vagrant Host
    config.vm.provision "ansible_local" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "ansible/server-03.yml"
      ansible.raw_arguments = ["--connection=paramiko"]
    end
  end

end
