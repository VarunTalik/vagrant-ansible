Vagrant.configure("2") do |config|

  # Define the three machines
  config.vm.define "webserver1" do |machine1|
    machine1.vm.box = "ubuntu/bionic64"
    machine1.vm.network "private_network", ip: "192.168.10.10"
    machine1.vm.provision "file", source: "ansible/apache/apache-playbook.yml", destination: "/tmp/playbook.yml"
    machine1.vm.provision "file", source: "ansible/apache/index.php", destination: "/tmp/index.php"
    machine1.vm.provision "shell",
      inline: "apt-get update -y && apt-get install ansible -y"
    machine1.vm.provision "shell",
      inline: "ansible-playbook /tmp/playbook.yml"
  end

  config.vm.define "webserver2" do |machine2|
    machine2.vm.box = "ubuntu/bionic64"
    machine2.vm.network "private_network", ip: "192.168.10.11"
    machine2.vm.provision "file", source: "ansible/apache/apache-playbook.yml", destination: "/tmp/playbook.yml"
    machine2.vm.provision "file", source: "ansible/apache/index.php", destination: "/tmp/index.php"
    machine2.vm.provision "shell",
      inline: "apt-get update -y && apt-get install ansible -y"
    machine2.vm.provision "shell",
      inline: "ansible-playbook /tmp/playbook.yml"
  end

  config.vm.define "loadbalancer" do |machine3|
    machine3.vm.box = "ubuntu/bionic64"
    machine3.vm.network "private_network", ip: "192.168.10.12"
    machine3.vm.provision "file", source: "ansible/haproxy/haproxy-playbook.yml", destination: "/tmp/playbook.yml"
    machine3.vm.provision "file", source: "ansible/haproxy/haproxy.cfg", destination: "/tmp/haproxy.cfg"
    machine3.vm.provision "shell",
      inline: "apt-get update -y && apt-get install ansible -y"
    machine3.vm.provision "shell",
      inline: "ansible-playbook /tmp/playbook.yml"
  end

  # Allow SSH from the host machine to each of the machines
  config.vm.provision "shell", inline: "echo '192.168.10.10 webserver1' >> /etc/hosts"
  config.vm.provision "shell", inline: "echo '192.168.10.11 webserver2' >> /etc/hosts"
  config.vm.provision "shell", inline: "echo '192.168.10.12 loadbalancer' >> /etc/hosts"

end