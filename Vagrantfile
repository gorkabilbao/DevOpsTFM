Vagrant.configure("2") do |config|

  config.vm.define "WebAppServer" do |vm1|
    vm1.vm.hostname = "WebAppServer"
    vm1.vm.box = "ubuntu/bionic64"
    vm1.vm.network "private_network", ip: "192.168.33.10"

    vm1.vm.provider "virtualbox" do |vb|
      vb.name = "WebAppServer"
      vb.gui = false
      vb.memory= "1024"
    end

    vm1.vm.provision "ansible_local" do |ansible|
      ansible.playbook ="provisioningWebApp/playbook.yml"
    end

    #vm1.vm.provision "shell", run: "always", inline:<<-SHELL
    #  echo "Hello from the WebAppServer"
    #SHELL
  end

  config.vm.define "MySQLDbServer" do |vm2|
    vm2.vm.hostname = "MySQLDbServer"
    vm2.vm.box = "almalinux/8"
    vm2.vm.network "private_network", ip: "192.168.33.20"
    vm2.vm.synced_folder ".", "/vagrant"

    vm2.vm.provider "virtualbox" do |vb|
      vb.name = "MySQLDbServer"
      vb.gui = false
      vb.memory= "1024"
    end

    vm2.vm.provision "ansible_local" do |ansible|
      ansible.playbook ="provisioningMySQL/playbook.yml"
    end
  end

  config.vm.define "JenkinsServer" do |vm3|
    vm3.vm.hostname = "JenkinsServer"
    vm3.vm.box = "ubuntu/bionic64"
    vm3.vm.network "private_network", ip: "192.168.33.30"
    #vm3.vm.synced_fyolder ".", "/vagrant"

    vm3.vm.provider "virtualbox" do |vb|
      vb.name = "JenkinsServer"
      vb.gui = false
      vb.memory= "1024"
    end

    vm3.vm.provision "ansible_local" do |ansible|
      ansible.playbook ="provisioningJenkins/playbook.yml"
    end


  end

end