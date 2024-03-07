Vagrant.configure("2") do |config|
    config.vm.synced_folder "~/data", "/home/vagrant/data", disabled: false
    config.ssh.username = "vagrant"
    config.ssh.password = "vagrant"
    config.vm.network "public_network", type: "dhcp"
    config.vm.provision "shell", path: "provision.sh"
    config.vm.define "test-vm" do |box|
      box.vm.box = "generic/fedora38"
      box.vm.box_version = "4.3.12"
      box.vm.host_name = "fedora"
      if Vagrant.has_plugin?("vagrant-vbguest") then
          config.vbguest.auto_update = true
      box.vm.provider "virtualbox" do |v|
        v.memory = "2048"
        v.cpus = "2"
     end
    end
  end
 end
