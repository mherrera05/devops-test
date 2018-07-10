  
$script = <<SCRIPT
# TODO: Put your install script here.
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    #config.vm.provision "shell", privileged: false, path: "vagrant-bootstrap2.sh"
    config.vm.provision "shell", privileged: true, inline: $script
    # Just in case you need to run a database server, web server, etc.
    #config.vm.network "forwarded_port", guest: 8080, host: 8080
    #config.vm.network "forwarded_port", guest: 5000, host: 5000
    #config.vm.network "forwarded_port", guest: 35357, host: 35357

    # Mem/cpu config example.
    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
    end

    config.provision "ansible" do |ansible|
        ansible.playbook = "provision/algo"
    end
end