Vagrant.configure(2) do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.cpus = 1
  end

  config.vm.define "instancec" do |conf_c|
    conf_c.vm.box = "bento/centos-7.3"
    conf_c.vm.hostname = "instancec"
    conf_c.vm.network "private_network", ip: "192.168.10.12"
    conf_c.vm.network "forwarded_port", guest: 8080, host: 8080

    conf_c.vm.provision "ansible" do |ansible|
      ansible.playbook = "bootstrap_hosts.yml"
    end
  end

  config.vm.define "instanceb" do |conf_b|
    conf_b.vm.box = "bento/centos-7.3"
    conf_b.vm.hostname = "instanceb"
    conf_b.vm.network "private_network", ip: "192.168.10.11"

    conf_b.vm.provision "ansible" do |ansible|
      ansible.playbook = "bootstrap_hosts.yml"
      ansible.ask_vault_pass = true
    end
  end

  config.vm.define "instancea" do |conf_a|
    conf_a.vm.box = "bento/centos-7.3"
    conf_a.vm.hostname = "instancea"
    conf_a.vm.network "private_network", ip: "192.168.10.10"

    conf_a.vm.provision "ansible" do |ansible|
      ansible.playbook = "bootstrap_hosts.yml"
    end
  end

end
