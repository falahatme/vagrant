IMAGE_2004 = "bento/ubuntu-20.04"
IMAGE_2204 = "bento/ubuntu-22.04"

#ENV['VAGRANT_NO_PARALLEL'] = 'no'

Vagrant.configure(2) do |config|

  config.vm.boot_timeout = 6000
 # config.vm.provision "shell", path: "bootstrap.sh"

  MasterNode = 3
  (1..MasterNode).each do |masternode_id|
    config.vm.define "masternode#{masternode_id}" do |masternode_vm|
      masternode_vm.vm.box = IMAGE_2204
      masternode_vm.vm.hostname = "masternode#{masternode_id}.falahat.com"
      masternode_vm.vm.network "private_network", ip: "192.168.62.11#{masternode_id}"
      masternode_vm.vm.provider "virtualbox" do |v|
        v.name = "masternode#{masternode_id}"
        v.memory = 1024
        v.cpus = 2
      end
      masternode_vm.vm.provision "shell", path: "bootstrap.sh"
    end
  end


  WorkerNode = 3
  (1..WorkerNode).each do |workernode_id|
    config.vm.define "workernode#{workernode_id}" do |workernode_vm|
      workernode_vm.vm.box = IMAGE_2204
      workernode_vm.vm.hostname = "workernode#{workernode_id}.falahat.com"
      workernode_vm.vm.network "private_network", ip: "192.168.62.12#{workernode_id}"
      workernode_vm.vm.provider "virtualbox" do |v|
        v.name = "workernode#{workernode_id}"
        v.memory = 2048
        v.cpus = 2
      end
      workernode_vm.vm.provision "shell", path: "bootstrap.sh"
    end
  end


  LoadBalancer = 2
  (1..LoadBalancer).each do |loadbalancer_id|
    config.vm.define "loadbalancer#{loadbalancer_id}" do |loadbalancer_vm|
      loadbalancer_vm.vm.box = IMAGE_2204
      loadbalancer_vm.vm.hostname = "loadbalancer#{loadbalancer_id}.falahat.com"
      loadbalancer_vm.vm.network "private_network", ip: "192.168.62.13#{loadbalancer_id}"
      loadbalancer_vm.vm.provider "virtualbox" do |v|
        v.name = "loadbalancer#{loadbalancer_id}"
        v.memory = 1024
        v.cpus = 2
      end
      loadbalancer_vm.vm.provision "shell", path: "bootstrap.sh"
    end
  end



end