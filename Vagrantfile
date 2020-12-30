
$ctlscript = <<CTLSCRIPT
sudo apt update -y
sudo apt install nano -y
sudo apt install ansible -y
#sudo cp /home/vagrant/hostname /etc/hostname
#sudo cp /home/vagrant/hosts /etc/hosts
CTLSCRIPT

$targetscript = <<TARGETSCRIPT
sudo apt update -y
sudo apt install nano -y
#sudo cp /home/vagrant/hostname /etc/hostname
#sudo cp /home/vagrant/hosts /etc/hosts
TARGETSCRIPT

Vagrant.configure("2") do |config|
 
  config.vm.box = "ubuntu/trusty64"

  config.vm.define "ansiblecontroller" do |ansiblecontroller|
  ansiblecontroller.vm.network "private_network", ip: "192.168.10.2"
  ansiblecontroller.vm.synced_folder "./ansiblecontroller/home", "/home/vagrant"
  ansiblecontroller.vm.provision "shell",
   inline: $ctlscript
  end

  config.vm.define "target1" do |target1|
  target1.vm.network "private_network", ip: "192.168.10.3"
  target1.vm.synced_folder ".\\target1\\home", "/home/vagrant"
  target1.vm.provision "shell",
   inline: $targetscript
  end

  config.vm.define "target2" do |target2|
  target2.vm.network "private_network", ip: "192.168.10.4"
  target2.vm.synced_folder ".\\target2\\home", "/home/vagrant"
  target2.vm.provision "shell",
   inline: $targetscript
  end

end
