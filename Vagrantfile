Vagrant.configure("2") do |config|
    config.ssh.insert_key = true

    config.vm.define "dockerimage" do |portainer|
        portainer.vm.box = "ubuntu/xenial64"
        portainer.vm.hostname = "docker-image"
        portainer.vm.network "private_network", ip: "172.28.128.100"
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
        drone.vm.network "private_network", ip: "172.28.128.99"
        drone.vm.provider "virtualbox" do |v|
            v.name = "drone-ci"
            v.memory = 1024
            v.cpus = 1
        end
        drone.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "ansible/drone.yaml"
        end
    end

    config.vm.define "gitlab" do |drone|
        drone.vm.box = "ubuntu/xenial64"
        drone.vm.hostname = "gitlab"
        drone.vm.network "private_network", ip: "172.28.128.98"
        drone.vm.provider "virtualbox" do |v|
            v.name = "gitlab"
            v.memory = 2048
            v.cpus = 1
        end
        drone.vm.provision "ansible_local" do |ansible|
            ansible.playbook = "ansible/gitlab.yaml"
        end
    end
end