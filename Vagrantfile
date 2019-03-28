# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.ssh.insert_key = false
  config.vm.define "appserver" do |appserver|
          appserver.vm.hostname="appserver"
          appserver.vm.network "private_network", ip: "192.168.10.2"
          config.vm.provision "shell" do |s|
          	ssh_pub_key = ""
          	ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
          	s.inline = <<-SHELL
			echo "SSH key provisioning."
          		mkdir -p /root/.ssh/
          		touch /root/.ssh/authorized_keys
          		echo #{ssh_pub_key} >> /root/.ssh/authorized_keys
          		chmod 644 /root/.ssh/authorized_keys
          		chown -R root. /root/.ssh
          		exit 0
          	SHELL
          end
#	  appserver.vm.provision "ansible" do |ansible|
#		    ansible.playbook = "../ansible/playbooks/test.yml"
#          end
 end
end
