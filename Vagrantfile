# -*- mode: ruby -*- 
# vi: set ft=ruby : vsa
Vagrant.configure(2) do |config| 
 config.vm.box = "centos/7" 
 config.vm.provider "virtualbox" do |v| 
 v.memory = 1024 
 v.cpus = 2 
 end 
 config.vm.define "pam" do |pam| 
 pam.vm.network "private_network", ip: "192.168.57.10" 
 pam.vm.hostname = "pam" 
 end 
 config.vm.provision "shell", inline: <<-SHELL
          #Разрешаем подключение пользователей по SSH с использованием пароля
          sed -i 's/^PasswordAuthentication.*$/PasswordAuthentication yes/' /etc/ssh/sshd_config
          #Перезапуск службы SSHD
          systemctl restart sshd.service
  	  SHELL
 config.vm.provision "ansible" do |ansible|
 ansible.playbook = "pam.yml"
 ansible.become = "true"
 end
end
