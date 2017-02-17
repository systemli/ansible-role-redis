# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = [
  { :name => :trusty, :box => 'ubuntu/trusty64' },
  { :name => :xenial, :box => 'ubuntu/xenial64' },
  { :name => :wheezy, :box => 'debian/wheezy64' },
  { :name => :jessie, :box => 'debian/jessie64' },
]

Vagrant.configure("2") do |config|
  ENV['ANSIBLE_ROLES_PATH'] =  "#{File.dirname(__FILE__)}/../"

  boxes.each do |opts|
    config.vm.define opts[:name] do |boxconfig|
      boxconfig.vm.hostname = opts[:name].to_s
      boxconfig.vm.box = opts[:box]

      boxconfig.vm.synced_folder ".", "/vagrant", disabled: true

      boxconfig.vm.provider :virtualbox do |v|
        v.memory = 512
        v.cpus = 1
      end

      if opts[:name].to_s =~ /xenial/
        # Python isn't present on Ubuntu 16.04
        boxconfig.vm.provision "shell", inline: "sudo apt-get install -y python 2>/dev/null 1>/dev/null"
      end

      # Ansible.
      boxconfig.vm.provision "ansible" do |ansible|
        ansible.playbook = "vagrant.yml"
        ansible.raw_arguments = ["--diff"]
        ansible.sudo = true
      end
    end
  end
end
