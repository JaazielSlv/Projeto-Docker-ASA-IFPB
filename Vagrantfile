# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|


  config.vm.box = "debian/bookworm64" 
  config.vm.hostname = "jaaziel.lucas" 

  # Desativa a verificação por atualizações
  config.vm.box_check_update = false

  config.vm.network "private_network", ip: "192.168.56.155" # 
  config.vm.provider "virtualbox" do |vb|


    # Define a quantidade de memória RAM da VM.
    vb.memory = "1024"

    # Desabilita a verificação dos 'guest additions' do VirtualBox.
    vb.check_guest_additions = false 
  end

  # Desativa a inserção automática de chave SSH padrão do Vagrant.
  config.ssh.insert_key = false 

  # Provisiona a máquina com Ansible.
  # Esta é a parte que executa nosso playbook para instalar tudo.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook_ansible.yml" 
  end

end
