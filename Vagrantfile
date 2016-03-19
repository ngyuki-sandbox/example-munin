Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.1"
  #config.ssh.insert_key = false
  #config.ssh.forward_agent = true

  config.vm.define "web" do |config|
    config.vm.hostname = "web"
    config.vm.network "private_network", ip: "192.168.33.10", virtualbox__intnet: "munin"
  end

  config.vm.define "munin" do |config|
    config.vm.hostname = "munin"
    config.vm.network "forwarded_port", guest: 80, host: 1234
    config.vm.network "private_network", ip: "192.168.33.11", virtualbox__intnet: "munin"
  end

  config.vm.provision "shell", inline: <<-SHELL
    sudo yum -y install vim-enhanced mailx nc rsync epel-release
    sudo yum -y install ansible httpd munin munin-node munin-cgi net-snmp net-snmp-utils
    cp -v /vagrant/hosts.ini /home/vagrant/
    chmod -v -x /home/vagrant/hosts.ini
  SHELL

  config.vm.provider :virtualbox do |v|
    v.linked_clone = true
  end
end
