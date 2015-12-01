# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'ubuntu/trusty64'

  config.vm.synced_folder './workspace', '/home/vagrant/workspace'
  config.vm.provision 'file', source: '~/.gitconfig', destination: '.gitconfig'

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
  end

  config.vbguest.auto_update = true 

  config.vm.provider :virtualbox do |vb|
    vb.gui = true 
    vb.customize ['modifyvm', :id, '--name', 'vagrant-sandbox']
    vb.customize ['modifyvm', :id, '--memory', '2048']
    vb.customize ['modifyvm', :id, '--cpus', '2']
  end
end
