# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  ENV['ANSIBLE_ROLES_PATH'] =  "#{File.dirname(__FILE__)}/../"

  # VirtualBox.
  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.cpus = 1
  end

  # Disable basic file sync.
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Ansible.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vagrant.yml"
    ansible.raw_arguments = ["--diff"]
    ansible.sudo = true
  end

  # Ubuntu Trusty (14.04 LTS)
  config.vm.define "trusty" do |trusty|
    trusty.vm.hostname = "trusty"
    trusty.vm.box = "ubuntu/trusty64"
  end

  # Ubuntu Precise (16.04 LTS)
  config.vm.define "xenial" do |xenial|
    xenial.vm.hostname = "xenial"
    xenial.vm.box = "ubuntu/xenial64"

    # Python isn't present on Ubuntu 16.04
    xenial.vm.provision "shell", inline: "sudo apt-get install -y python"
  end

  # Debian Wheezy
  config.vm.define "wheezy" do |wheezy|
    wheezy.vm.hostname = "wheezy"
    wheezy.vm.box = "debian/wheezy64"
  end

  # Debian Jessie
  config.vm.define "jessie", primary: true do |jessie|
    jessie.vm.hostname = "jessie"
    jessie.vm.box = "debian/jessie64"
  end
end
