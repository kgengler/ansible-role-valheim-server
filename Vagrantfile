$script = <<-SCRIPT
apt-get update
apt-get upgrade -y
apt-get install -y python3-pip
python3 -m pip install --upgrade ansible paramiko
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.network "forwarded_port", guest: 2456, host: 2456
  config.vm.network "forwarded_port", guest: 2457, host: 2457
  config.vm.network "forwarded_port", guest: 2458, host: 2458

  config.vm.provision "shell", inline: $script
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.playbook_command = "ANSIBLE_ROLES_PATH=/ ansible-playbook"
  end

  config.vm.provider "virtualbox" do |v|
    v.cpus = 2
    v.memory = 4096
  end

  config.vm.provider "hyperv" do |h|
    h.cpus = 2
    h.memory = 4096
  end
end
