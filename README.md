# Vagrant
Steps:
1. Install Vagrant and your choice of Provider (Hypervisor) to create VMs
2. Then run vagrant up to spin up 3 virtual machines (2 Web servers and One Load Balancer).
3. Hit the loadbalancer IP and it should alternate between both webservers

# Docker
Steps:
1. You need to create ssh key pair with `have-a-key.sh` file. so run `chmod +x have-a-key.sh`.
2. Then run `./have-a-key.sh`.
3. This will create two files called `id_rsa` and `id_rsa.pub`.
4. To have Containers, install docker.
5. Then run `docker-compose up -d` It will give you 3 Containers running (2 Web Servers and One Load Balancer)  
6. SSH into docker container using private key
