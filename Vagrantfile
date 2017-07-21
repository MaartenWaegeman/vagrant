SERVER_NAME = 'MadeenServer'

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.define SERVER_NAME do |node|
    node.vm.hostname = SERVER_NAME
    node.vm.network "public_network"
    node.vm.provider "virtualbox" do |vb|
        vb.name   = SERVER_NAME
        vb.memory = 512
        vb.cpus   = 2
    end

    node.vm.provision "ansible_local" do |ansible|
      ansible.playbook       = "/vagrant/ansible/site.yml"
      ansible.inventory_path = "/vagrant/ansible/hosts"
      ansible.limit          = "webservers"
    end
  end

  # Share an additional folder to the guest VM. Thed: first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  #config.vm.synced_folder "nginxconfig", "/etc/nginx/"
  # config.vm.synced_folder ".", "/vagrant", disabled: true
end
