Vagrant.configure(2) do |config|
  #config.vm.box = "ngyuki/centos-7"
  config.vm.box = "bento/centos-7.1"

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
    sudo yum -y install vim-enhanced mailx nc ansible
  #  sudo yum install --downloadonly munin munin-node munin-cgi httpd net-snmp net-snmp-utils
  #  mkdir /tmp/munin-contrib
  #  wget -q https://github.com/munin-monitoring/contrib/archive/master.tar.gz -O - |
  #    tar xzf - -C /tmp/munin-contrib --strip-components=1
  SHELL

  config.vm.provider :virtualbox do |v|
    v.linked_clone = true
  end
end
