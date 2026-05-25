vagrant up d13-swarm-manager1 d13-swarm-manager2 d13-swarm-manager3 d13-swarm-worker1 d13-swarm-worker2
 
 
./venv/bin/ansible-playbook playbooks/augusto/d13-swarm-manager1.yml
./venv/bin/ansible-playbook playbooks/augusto/d13-swarm-manager2.yml
./venv/bin/ansible-playbook playbooks/augusto/d13-swarm-manager3.yml
./venv/bin/ansible-playbook playbooks/augusto/d13-swarm-worker1.yml
./venv/bin/ansible-playbook playbooks/augusto/d13-swarm-worker2.yml


vagrant ssh d13-swarm-manager1
docker swarm init --advertise-addr 192.168.8.95
docker node ls

docker swarm join-token worker 
OU
docker swarm join-token manager

Insera todos;

docker node ls

Criar: portainer.yml

version: '3.9'

services:

  portainer:
    image: portainer/portainer-ce:latest

    ports:
      - "9000:9000"

    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data

    deploy:

      replicas: 1

      placement:
        constraints:
          - node.labels.portainer == true

volumes:
  portainer_data:
  
  
docker node update --label-add portainer=true d13-swarm-manager1
docker stack deploy -c portainer.yml portainer

  
http://192.168.8.95:9000

Montar inicialmente: d13-swarm-manager1 e d13-swarm-worker1

Depois rodar o playbook adicionando: d13-swarm-manager2 e demais

 
 
