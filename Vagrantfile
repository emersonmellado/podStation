Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 8888, host: 8888

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1536"]
    vb.name = "podStation-vm"    
  end

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y g++
    curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
    apt-get install -y nodejs
    apt-get install -y git
    sudo npm install -g bower

    # su vagrant
    # mkdir /home/vagrant/node_modules
    # cd /var/www/project
    # ln -s /home/vagrant/node_modules/ node_modules
    # npm install karma
  SHELL

  config.vm.provision "shell", run: "always", inline: <<-SHELL
    # ipython notebook --notebook-dir=/vagrant/notebook --no-browser --ip=0.0.0.0 &
  SHELL

end

# Vagrant.configure(2) do |config|
#   config.vm.box = "ubuntu/trusty64"
#   config.vm.synced_folder ".", "/var/www/project"
#   config.vm.provision "shell", inline: <<-SHELL
#     apt-get update
#     apt-get install -y g++
#     curl -sL https://deb.nodesource.com/setup_0.12 | sh
#     apt-get install -y nodejs
#     su vagrant
#     mkdir /home/vagrant/node_modules
#     cd /var/www/project
#     ln -s /home/vagrant/node_modules/ node_modules
#     npm install karma
#   SHELL
# end