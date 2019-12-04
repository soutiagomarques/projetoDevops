
Vagrant.configure("2") do |config|

  config.vm.box = "hashicorp/bionic64"

    # Configurando Ip da VM
    config.vm.network 'private_network', ip: '192.168.50.4'

    # Instalando o Ansible na VM
    config.vm.provision "shell",
    inline: "apt-get update &&  \
               apt-get install -y software-properties-common && \
               apt-add-repository --yes --update ppa:ansible/ansible && \
               apt-get install -y ansible "

    # copia a pasta ansible para a VM
    config.vm.synced_folder "./ansible/", "/ansible/"

    #roda o arquivo playbook a partir da Vm
    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
    end

    
  # Configurando porta de acesso ao Jenkins
  # config.vm.network "forwarded_port", guest: 8080, host: 8089

  # Configurando porta de acesso ao serviço de Usuario
  # config.vm.network "forwarded_port", guest: 8080, host: 8089

  # Configurando porta de acesso ao serviço de Filmes
  # config.vm.network "forwarded_port", guest: 8080, host: 8089

end
