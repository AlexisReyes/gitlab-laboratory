# -*- mode: ruby -*-
# vi: set ft=ruby :
# encoding: UTF-8

CORE = 1
MEMORY = 1024
CB_USER = "developer"
UBUNTU  = "ubuntu/jammy64"

Vagrant.configure("2") do |config|

    config.vm.define "gitlab" do |gitlab|

        gitlab.vm.box    = UBUNTU

        gitlab.vm.provider "virtualbox" do |vb| 
            vb.memory = MEMORY * 4
            vb.cpus   = CORE * 2
        end

        gitlab.vm.provision "ansible" do |ansible|
            ansible.raw_arguments = ["-e", "gitlab=true"]
            ansible.playbook = "provision.yml"
        end

        config.vm.network "private_network", ip: "192.168.56.10"
    end

    config.vm.define "app" do |app|

        app.vm.box    = UBUNTU

        app.vm.provider "virtualbox" do |vb| 
            vb.memory = MEMORY * 4
            vb.cpus   = CORE * 2
        end

        app.vm.provision "ansible" do |ansible|
            ansible.playbook = "provision.yml"
        end

        app.vm.network "private_network", ip: "192.168.56.11"
    end
end
