#  Docker Swarm Cheat Sheet - Os Comandos Utilizados #


Segue a lista com os principais comandos utilizados durante o curso:

* Cluster com o docker swarm
  * __```docker-machine create -d NOME_DRIVER_VM NOME_VM```__ - cria a máquina virtual com o driver escolhido para a virtualização, exemplo: *docker-machine create -d virtualbox vm1*.   
  * __```docker-machine ls```__ - lista as máquinas virtuais instaladas na máquina criadas pela docker-machine.
  * __```docker-machine start NOME_VM```__ - inicia uma máquina virtual parada.
  * __```docker-machine ssh NOME_VM```__ - acessa o terminal da máquina virtual.
  * __```docker swarm init```__ - inicia as configurações de cluster da VM pelo terminal após usar o comando ```docker-machine ssh NOME_VM```.
  * __```docker swarm init --advertise-addr ENDERECO_IP```__ - inicia as configurações de cluster da VM pelo terminal após usar o comando ```docker-machine ssh                                                                        NOME_VM``` com um endereço de IP configurado para identifiação da interface de rede.
  * __```docker info```__ - usado por dentro do terminal da VM traz a informação se está presente em um cluster swarm.

* Responsabilidade dos nós workers
  * __```docker swarm join --token TOKEN ENDERECO_IP```__ - adiciona uma VM como worker de um nó com TOKEN e ENDERECO_IP.
  * __```docker swarm join-token worker```__ - pelo ssh da VM manager é apresentado o comando com token para adicionar workers.
  * __```docker swarm leave```__ - pelo ssh da VM worker é alterado o status do nó de Ready para Down.
  * __```docker node ls```__ - pelo ssh da VM manager é apresentada a lista de nós existentes do cluster swarm.
  * __```docker node inspect VM_WORKER```__ - pelo ssh da VM manager é inspecionado um nó worker existente no cluster swarm.
  * __```docker service create -p 8080:3000 NOME_IMAGEM```__ - pelo ssh da VM manager é criado um serviço dentro de um swarm direcionando a imagem do container para os workers.
  * __```docker service ls```__ - pelo ssh da VM manager é apresentada a lista de serviços existentes do cluster swarm.
  * __```docker service ps ID_SERVICO```__ - pelo ssh da VM manager é apresentado detalhes do serviço ID existente no cluster swarm.
 

* Gerenciando o cluster com managers
  * __```docker swarm leave --force```__ - pelo ssh da VM manager é forçada a saída do cluster swarm, consequentemente toda a configuração se perde, e os workers ficam sem manage.
  * __```docker swarm init --force-new-clust --advertise-addr ENDERECO_IP```__ - pelo ssh da VM manager, força o início de novas configurações de outro cluster ou de backup.
  * __```docker swarm join-token manager```__ - pelo ssh da VM manager exibe o comando para adcionar novos nós managers.
  * __```docker node ls --format {{.Hostname}} {{.ManagerStatus}}```__ - exibe apenas o resultado da coluna de HOSTNAME e MANAGERSTATUS do comando docker node ls.

* Separando as responsabilidades
  * __```docker rm ID_CONTAINER```__ - remove o container com id em questão.


* Serviços globais e replicados
  * __```docker build -f Dockerfile```__ - cria uma imagem a partir de um Dockerfile.
  
* Driver Overlay
  * __```docker login```__ - inicia o processo de login no Docker Hub.
 

* Deploy com Docker Stack
  * __```hostname -i```__ - mostra o ip atribuído ao container pelo docker (funciona apenas dentro do container).

