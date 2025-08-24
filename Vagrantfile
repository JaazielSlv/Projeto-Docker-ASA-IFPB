# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Define a imagem (Box) do sistema operacional.
  config.vm.box = "debian/bookworm64"

  # Define o nome da máquina virtual (hostname).
  config.vm.hostname = "jaaziel.lucas"

  # Desativa a verificação por atualizações da imagem base (Box).
  config.vm.box_check_update = false

  # Configura a rede privada da máquina virtual.
  config.vm.network "private_network", ip: "192.168.56.155"

  # Configura o provedor da virtualização (VirtualBox).
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.check_guest_additions = false
  end

  # Desativa a inserção automática de chave SSH padrão do Vagrant.
  config.ssh.insert_key = false

  # Passo 1: Instala o Ansible usando o apt do Debian.
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y ansible
  SHELL

  # Passo 2: Roda o playbook do Ansible que já está na máquina.
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "/vagrant/playbook_ansible.yml"
  end

end # <--- Esta é a linha que estava faltando.
