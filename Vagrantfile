# -*- mode: ruby -*-
# vi: set ft=ruby :

hosts = {
  "Centos-7" => "192.168.56.105",
}

Vagrant.configure("2") do |config|
	hosts.each do |name, ip|
    		config.vm.define name do |machine|
		machine.vm.box = "centos/7"
		machine.vm.hostname = "%s" % name
      		machine.vm.network :private_network, ip: ip
      		machine.vm.network :private_network, ip: ip
      		machine.vm.provider "virtualbox" do |v|
          		v.name = name
          		v.customize ["modifyvm", :id, "--memory", 1024, "--cpus", 1]
			v.name = "%s" % name
			end	
  		machine.vm.provision "shell", inline: <<-SHELL
    		 systemctl stop firewalld && systemctl disable firewalld
		 setenforce 0 && sed -i 's/SELINUX=enforcing/SELINUX=disabled/g' /etc/selinux/config
   		SHELL
		end
         end
end
