Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.ssh.insert_key = true
    config.vm.hostname = "docker-swarm"
    config.vm.network "private_network", type: "dhcp"

    config.vm.provider "virtualbox" do |v|
        v.name = "docker-swarm"
        v.memory = 1024
        v.cpus = 1
    end

    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "inc/tasks.yml"
    end
end