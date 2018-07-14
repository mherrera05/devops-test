Vagrant.configure("2") do |config|
    config.ssh.insert_key = true

    config.vm.define "portainer" do |portainer|
        portainer.vm.box = "ubuntu/xenial64"
        portainer.vm.hostname = "docker-image"
        portainer.vm.network "private_network", type: "dhcp"
        portainer.vm.provider "virtualbox" do |v|
            v.name = "docker-image"
            v.memory = 1024
            v.cpus = 1
        end
        portainer.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "ansible/portainer.yaml"
        end
    end

    config.vm.define "drone" do |drone|
        drone.vm.box = "ubuntu/xenial64"
        drone.vm.hostname = "drone-ci"
        drone.vm.network "private_network", type: "dhcp"
        drone.vm.provider "virtualbox" do |v|
            v.name = "drone-ci"
            v.memory = 1024
            v.cpus = 1
        end
        drone.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "ansible/drone.yaml"
        end
    end
end