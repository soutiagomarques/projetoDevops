
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.define "mysql" do |m|
     m.vm.network "private_network", ip: "172.17.177.40"
  end

  config.vm.provider "virtualbox" do |v|
	v.memory = 1024
  end

  config.vm.provision "shell",
  inline: "echo ********** INSTALANDO ANSIBLE NA VM **********"
  # Instalando o NPM and NodeJs na VM
  config.vm.provision "shell",
  inline: "sudo apt-get update && \
              apt-get install -y software-properties-common && \
              apt-add-repository ppa:ansible/ansible && \
              apt-get install -y ansible "

  config.vm.provision "shell",
  inline: "echo ********** INSTALANDO NODEJS E NPM **********"
  # Instalando o NPM and NodeJs na VM
  config.vm.provision "shell",
  inline: "curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - &&  \
              apt-get install -y curl && \
              curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash - && \
              apt-get install -y nodejs "


  config.vm.provision "shell",
  inline: "echo ********** INSTALANDO YARN **********"
  # Instalando o Yarn na VM
  config.vm.provision "shell",
  inline: "apt-get update &&  \
             curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - && \
             echo 'deb https://dl.yarnpkg.com/debian/ stable main' | sudo tee /etc/apt/sources.list.d/yarn.list && \
             apt-get update && \
             sudo apt-get install -y yarn "

  #roda o arquivo playbook a partir da Vm
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "provisioning.yml"
  end 

  # Configurando porta de acesso ao MYSQL
  config.vm.network "forwarded_port", guest: 3306, host: 2020

  # Configurando porta de acesso ao serviço de Usuario
  # config.vm.network "forwarded_port", guest: 8080, host: 8089

  # Configurando porta de acesso ao serviço de Filmes
  # config.vm.network "forwarded_port", guest: 8080, host: 8089

end
