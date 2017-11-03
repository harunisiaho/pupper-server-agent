Vagrant.configure("2") do |config|
   config.vm.define "puppet-master" do |puppet|
        
        puppet.vm.box = "bento/centos-7.4"
        puppet.vm.network "public_network", ip: "192.168.50.4", bridge: "en0: Wi-Fi (AirPort)"
        
        puppet.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/puppet-master-deploy.yml"
            ansible.limit = "all"
        end
        
        puppet.vm.provider "virtualbox" do |vb|
             vb.name = "puppet-master"
             vb.memory = 3072
             vb.cpus = 2
             puppet.vm.hostname = "puppet-master.sysadminonline.net"
        end
  end

  config.vm.define "puppet-agent" do |agent|
        agent.vm.box = "bento/centos-7.4"
        agent.vm.network "public_network", ip: "192.168.50.5", bridge: "en0: Wi-Fi (AirPort)"

        agent.vm.provision "ansible" do |ansible|
            ansible.playbook = "ansible/puppet-agent-deploy.yml"
            ansible.limit = "all"
        end

        agent.vm.provider "virtualbox" do |vb|
           vb.name = "puppet-agent" 
           vb.memory = 512
           vb.cpus = 2
           agent.vm.hostname = "puppet-agent.sysadminonline.net"
        end
    end
end
