
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.define "projDevops" do |m|
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

  # # Install Java Open JRE or JDK
  # config.vm.provision "shell",
  # inline: "apt-get update &&  \
  #             apt-get install -y default-jre && \
  #             apt-get install -y default-jdk"

  # # Instalando o Jenkins na VM
  # config.vm.provision "shell",
  # inline: "wget -q -O - https://pkg.jenkins.io/debian/jenkins-ci.org.key | sudo apt-key add - && \
  #             sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list' && \
  #             apt-get update && \
  #             apt-get install -y jenkins"

  #roda o arquivo playbook a partir da VM
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning.yml"
  end 

end
