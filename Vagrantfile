
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.define "mysql" do |m|
     m.vm.network "private_network", ip: "172.17.177.40"
  end

  config.vm.provider "virtualbox" do |v|
	v.memory = 1024
  end

  # Instalando o NPM and NodeJs na VM
  config.vm.provision "shell",
  inline: "apt-get update &&  \
              curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash - && \
              sudo apt-get install -y nodejs"

  # Instalando o Yarn na VM
  config.vm.provision "shell",
  inline: "apt-get update &&  \
             curl -sL https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add - && \
             echo 'deb https://dl.yarnpkg.com/debian/ stable main' | sudo tee /etc/apt/sources.list.d/yarn.list && \
             apt-get update && sudo apt install yarn "

  #roda o arquivo playbook a partir da VM
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning.yml"
  end 

end
