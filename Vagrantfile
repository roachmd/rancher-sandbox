# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'fileutils'
require 'open-uri'
require 'tempfile'

Vagrant.require_version ">= 1.8.5"

# Global Variables 
 $vm_box = "bento/ubuntu-16.04"
 $vm_box_master_memory = "4096"
 $vm_box_master_cpus = 4
 #Nodes
 $rancher01 = "10.10.10.100"

Vagrant.configure(2) do |config|
  config.vm.box = $vm_box

  config.vm.define vm_name = "rancher01" do |rancher01|
    rancher01.vm.box = $vm_box
    rancher01.vm.network "private_network", ip: $rancher01
    rancher01.vm.hostname = "rancher01..local"
    rancher01.vm.provision "shell", path: "installDocker.sh"
    rancher01.vm.provision "shell", path: "installRancher.sh", args: [$rancher01]

   rancher01.vm.provider :virtualbox do |vm|
     vm.memory = $vm_box_master_memory
     vm.cpus = $vm_box_master_cpus
   end #end rancher01 provider
  end #end define rancher01
end #end configure
