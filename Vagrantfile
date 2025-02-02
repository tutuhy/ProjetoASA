Vagrant.configure("2") do |config|
  
  config.vm.box = "debian/bookworm64"
  config.vbguest.auto_update = false

  # Configuração da VM
  config.vm.hostname = "rodrigo-arthur"
  config.vm.network "private_network", ip: "192.168.57.10"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  # Adicionar 3 discos adicionais de 10GB
  (0..2).each do |i|
    config.vm.disk :disk, size: "10GB", name: "disk-#{i}"
  end
  # Provisionamento com Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.playbook ="playbook.yml"
  end
end