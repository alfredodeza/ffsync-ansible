

Vagrant.configure("2") do |config|

  config.vm.box     = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"


  # This is only necessary if your CPU does not support VT-x or you run virtualbox
  # inside virtualbox
  # config.vm.customize ["modifyvm", :id, "--vtxvpid", "off"]

  # Forward Nginx
  config.vm.network :forwarded_port, guest: 80, host: 8000 # Nginx
  config.vm.network :private_network, ip: "192.168.111.199"

  # You can adjust this to the amount of CPUs your system has available
  config.vm.provider :vritualbox do |vb|
      vb.config.vm.customize ["modifyvm", :id, "--memory", "512"]
      vb.customize ["modifyvm", :id, "--cpus", "4"]
  end

  config.vm.provision :ansible do |ansible|
    # point Vagrant at the location of your playbook you want to run
    ansible.playbook = "playbooks/setup-devserver.yml"
    ansible.inventory_file = "playbooks/hosts"
    ansible.verbose = true

    # the Vagrant VM will be put in this host group change this should
    # match the host group in your playbook you want to test
    # If this doesn't match the action (e.g. you are running web-servers')
    # it will skip it
    ansible.hosts = "dev-server"
  end
end
