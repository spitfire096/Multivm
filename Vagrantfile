Vagrant.configure("2") do |config|
    # Define the first web server (web01) on Ubuntu 20.04
    config.vm.define "web01" do |web01|
      web01.vm.box = "ubuntu/focal64"
      web01.vm.hostname = "web01"
      web01.vm.network "private_network", ip: "192.168.56.10"
    end
  
    # Define the second web server (web02) on Ubuntu 20.04
    config.vm.define "web02" do |web02|
      web02.vm.box = "ubuntu/focal64"
      web02.vm.hostname = "web02"
      web02.vm.network "private_network", ip: "192.168.56.11"
    end
  
    # Define the database server (db01) on CentOS 7
    config.vm.define "db01" do |db01|
      db01.vm.box = "centos/7"
      db01.vm.hostname = "db01"
      db01.vm.network "private_network", ip: "192.168.56.12"
      
      # Provisioning script to set hostname and any other configurations
      db01.vm.provision "shell", inline: <<-SHELL
        yum install -y wget unzip mariadb-server -y
        systemctl start mariadb
        systemctl enable mariadb
        hostnamectl set-hostname db01
      SHELL
    end
  end
  