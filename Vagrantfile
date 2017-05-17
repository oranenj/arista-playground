# -*- mode: ruby -*-
# vi: set ft=ruby :

default_box = mybox = 'vEOS'

Vagrant.configure(2) do |config|

  config.vm.define 'spine01' do |spine01|
    spine01.vm.box = mybox
    spine01.vm.network 'private_network',
                       virtualbox__intnet: 's01l03',
                       ip: '169.254.1.11', auto_config: false
    spine01.vm.network 'private_network',
                       virtualbox__intnet: 's01l04',
                       ip: '169.254.1.11', auto_config: false
    spine01.vm.network 'private_network',
                       virtualbox__intnet: 's01s02',
                       ip: '169.254.1.11', auto_config: false

    spine01.vm.provision 'shell', inline: <<-SHELL
      echo done
    SHELL
  end

  config.vm.define 'spine02' do |spine02|
    spine02.vm.box = default_box
    spine02.vm.network 'private_network',
                       virtualbox__intnet: 's02l03',
                       ip: '169.254.1.11', auto_config: false
    spine02.vm.network 'private_network',
                       virtualbox__intnet: 's02l04',
                       ip: '169.254.1.11', auto_config: false
    spine02.vm.network 'private_network',
                       virtualbox__intnet: 's01s02',
                       ip: '169.254.1.11', auto_config: false
  end
  config.vm.define 'leaf03' do |leaf03|
    leaf03.vm.box = default_box
    leaf03.vm.network 'private_network',
                       virtualbox__intnet: 's01l03',
                       ip: '169.254.1.11', auto_config: false
    leaf03.vm.network 'private_network',
                       virtualbox__intnet: 's02l03',
                       ip: '169.254.1.11', auto_config: false
    leaf03.vm.network 'private_network',
                       virtualbox__intnet: 'l03l04',
                       ip: '169.254.1.11', auto_config: false
  end

  config.vm.define 'leaf04' do |leaf04|
    leaf04.vm.box = default_box
    leaf04.vm.network 'private_network',
                       virtualbox__intnet: 's01l04',
                       ip: '169.254.1.11', auto_config: false
    leaf04.vm.network 'private_network',
                       virtualbox__intnet: 's02l04',
                       ip: '169.254.1.11', auto_config: false
    leaf04.vm.network 'private_network',
                       virtualbox__intnet: 'l03l04',
                       ip: '169.254.1.11', auto_config: false
  end
  config.vm.provision 'ansible' do |a|
    a.playbook = "provisioning/base.yaml"
    a.raw_arguments = ['-D']
  end
end
