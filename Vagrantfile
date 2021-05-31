Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/focal64"
  config.ssh.insert_key = false

  config.vm.network "private_network", ip: "192.168.3.11"
  # config.vm.synced_folder "../data", "/vagrant_data"

  # --- VirtualBox ---
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--ostype", "Ubuntu_64"]
    vb.memory = "2048"
  end

  # --- docker ---
  config.vm.provision :docker

  # --- shell provision ---
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
      sudo timedatectl set-timezone Asia/Tokyo
      sudo apt-get update
      echo 'cd /vagrant' >> /home/vagrant/.profile
  SHELL
  config.vm.provision :docker_compose
end
