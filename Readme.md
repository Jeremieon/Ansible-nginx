##Deploying and configuring Nginx with Ansible

1. Setup Docker Enviroments (master,nodes)
2. Dockerfile for Ansible Master
3. Start Docker enviroment docker-compose up -d
4. docker exec -it ansible-master bash
5. ssh-keygen -t rsa -b 2048
6. sshpass -p "root" ssh-copy-id -o StrictHostKeyChecking=no root@node1
7. sshpass -p "root" ssh-copy-id -o StrictHostKeyChecking=no root@node2
8. you need to make sure that the SSH server (openssh-server) is installed and running on both node1 and node2.
   i. docker exec -it node1 bash
   ii. apt-get update
   iii. apt-get install -y openssh-server
   iv. service ssh start
   v. service ssh status
   vi. nano /etc/ssh/sshd_config
   vii. PermitRootLogin yes | PasswordAuthentication yes
   viii. service ssh start
   ix. passwd root
   x. ChallengeResponseAuthentication no
9. add nginx-playbook.yml and inventory in /ansible directory
10. run ansible-playbook -i inventory nginx-playbook.yml
