require 'rbconfig'
require 'yaml'

inventory = YAML.load_file("inventory-test.yml")

Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"

  inventory["all"]["hosts"].each do |host_name, attributes|
    config.vm.define host_name do |machine|
      machine.vm.network "private_network", ip: attributes["ansible_host"]
      machine.vm.provider "virtualbox" do |vbox|
        vbox.memory = "1024"
        vbox.cpus = "1"
        vbox.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        vbox.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
      end
    end

    config.vm.provision "shell", inline: <<-SHELL
        apt-get -yqq update
    SHELL
  end
end
