BOX_NAME = "ubuntu/xenial64"
NODE_COUNT = 2

Vagrant.configure("2") do |config|

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end

    config.vm.define "k8s-master" do |master|
        master.vm.box = BOX_NAME
        master.vm.network "private_network", ip: "10.0.0.10"
        master.vm.hostname = "k8s-master"
        master.vm.network :forwarded_port, guest: 5000, host: 1234
    end

    (1..NODE_COUNT).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = BOX_NAME
            node.vm.network "private_network", ip: "10.0.0.#{i + 10}"
            node.vm.hostname = "node-#{i}"
        end
    end
end
