# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/trusty64"
  # config.vm.box_check_update = false

  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # config.vm.network "private_network", ip: "192.168.33.10"

   

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.  
    config.vm.provision "shell", inline: <<-SHELL
     apt-get update ; apt-get upgrade -y
    SHELL

     N = 4 
      (1..4).each do |i|
         config.vm.define "node-#{i}" do |node|
         node.vm.hostname = "node-#{i}"
         node.vm.network "public_network" , bridge: "(VAGRANT_INTERFACE')"
#Run ansible
     if i == N
      node.vm.provision:ansible do |ansible|
       ansible.limit = "all"
       ansible.playbook = "playbook.yml"
       ansible.sudo = true
      end  
     end 
   end
  end
 end
