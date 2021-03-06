#  Docker Swarm Cheat Sheet - Os Comandos Utilizados #


Segue a lista com os principais comandos utilizados durante o curso:

* Cluster com o docker swarm
  * __```docker-machine create -d NOME_DRIVER_VM NOME_VM```__ - cria a máquina virtual com o driver escolhido para a virtualização, exemplo: *docker-machine create -d virtualbox vm1*.   
  * __```docker-machine ls```__ - lista as máquinas virtuais instaladas na máquina criadas pela docker-machine.
   
  | NAME         |    ACTIVE    |    DRIVER    |    STATE     |     URL                |     SWARM    |     DOCKER   |       ERRORS |
  | :----------: | :----------: | :----------: | :----------: | :--------------------: | :----------: | :----------: | :----------: |
  | vm1          |      -       |  virtualbox  |   Running    | tcp://192.168.0.2:2376 |              |   v19.03.3   |              |
  
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
   
  |               ID           |    HOSTNAME  |    STATUS    | AVAILABILITY |   MANAGER STATUS       | ENGINE VERSION  |
  | :------------------------: | :----------: | :----------: | :----------: | :--------------------: | :-------------: | 
  | eyJhbGciOiJIUzI1NiIsInR5c  * |      vm1     |    Ready     |    Active    |      Leader            |   19.03.3       | 
  | eyJzdWIiOiIxMjM0NTY3ODkwI  |      vm2     |    Ready     |    Active    |                        |   19.03.3       | 
  | SflKxwRJSMeKKF2QT4fwpMeJf  |      vm3     |    Ready     |    Active    |                        |   19.03.3       | 
  
  * __```docker node inspect VM_WORKER```__ - pelo ssh da VM manager é inspecionado um nó worker existente no cluster swarm.
  * __```docker service create -p 8080:3000 NOME_IMAGEM```__ - pelo ssh da VM manager é criado um serviço dentro de um swarm direcionando a imagem do container para os workers.
  * __```docker service ls```__ - pelo ssh da VM manager é apresentada a lista de serviços existentes do cluster swarm.

  |      ID       |            NAME            |        MODE       |   REPLICAS   |           IMAGES             |        PORTS        |
  | :-----------: | :------------------------: | :---------------: | :----------: |  :-------------------------: | :-----------------: |
  | ulaxnhi770p4  |      exciting_portrais     |    replicated     |      1/1     | aluracursos/barbearia:latest |  \*:8080->3000/tcp  |

  * __```docker service ps ID_SERVICO```__ - pelo ssh da VM manager é apresentado detalhes do serviço ID existente no cluster swarm.
  
  |      ID       |            NAME            |              IMAGE              |   NODE   |   DESIRED STATE   |     CURRENT STATE          |   ERROR  |  PORTS   | 
  | :-----------: | :------------------------: | :-----------------------------: | :------: | :---------------: | :------------------------: | :------- | :------: |
  | x06k7hbl96lz  |     objective.allen.1      |  aluracursos/barbearia:latest   |    vm3   |    Running        |  Running 6 minutes ago     |          |          |
  | n27sa3uw017c  |     \_objective.allen.1    |  aluracursos/barbearia:latest   |    vm2   |    Shutdown       |  Failed about a second ago |          |          |

* Gerenciando o cluster com managers
  * __```docker swarm leave --force```__ - pelo ssh da VM manager é forçada a saída do cluster swarm, consequentemente toda a configuração se perde, e os workers ficam sem manage.
  * __```docker swarm init --force-new-clust --advertise-addr ENDERECO_IP```__ - pelo ssh da VM manager, força o início de novas configurações de outro cluster ou de backup.
  * __```docker swarm join-token manager```__ - pelo ssh da VM manager exibe o comando para adcionar novos nós managers.
  * __```docker node ls --format {{.Hostname}} {{.ManagerStatus}}```__ - exibe apenas o resultado da coluna de HOSTNAME e MANAGERSTATUS do comando docker node ls.

* Separando as responsabilidades
  * __```docker node demote VM_MANAGER```__ - pelo ssh da VM de um manager, rebaixa um nó manager para worker.
  * __```docker node rm VM_MANAGER```__ - pelo ssh da VM de um manager, apaga um nó worker do cluster.
  * __```docker service rm $(docker service ls -q)```__ - pelo ssh da VM de um nó manager, apaga-se todos os serviços de um cluster.
  * __```docker node update --availability drain VM```__ - pelo ssh da VM de um nó manager, atualiza a o Availability de Active para Drain para impedir que o nó execute tarefas.
  * __```docker service update --constraint-add node.role==worker ID_SERVICE```__ - pelo ssh de uma VM manager é restringido um serviço para que apenas nós workers o executem.
  * __```docker service update --constraint-rm node.role==worker ID_SERVICE```__ - pelo ssh de uma VM manager é removida a restrição de um serviço de executar tarefas apenas em nós workers.
  * __[Outras Restrições](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-04/aulas/README.md)__


* Serviços globais e replicados
  * __``` docker service update --replicas QUANTIDADE ID_SERVICO ```__ - pelo ssh de um manager, atualiza a quantidade de tarefas de um serviço a serem balanceadas entre os workers.
  * __``` docker service scale ID_SERVICO=QUANTIDADE ```__ - pelo ssh de um manager, atualiza a quantidade de tarefas de um serviço a serem balanceadas entre os workers.
  * __```docker service create -p 8080:3000 --mode global NOME_IMAGEM```__ - pelo ssh da VM manager é criado um serviço, em modo global, dentro de um swarm direcionando a imagem do container para os workers.
  
* Driver Overlay
  * __```docker service create --name NOME_SERVICO```__ - pelo ssh da VM manager é criado um serviço dentro de um swarm indicando um nome para este.
  * __```docker network driver -d overlay NOME_REDE_OVERLAY```__ - cria uma rede docker do tipo overlay.
  * __```docker service create --name NOME_SERVICO --network NOME_REDE_OVERLAY```__ - cria um serviço com uma rede overlay previamente criada.
  * __```docker network create -d overlay --attachable NOME_REDE_OVERLAY```__ - cria uma rede docker do tipo overlay com parâmetro attachable, esse parâmetro permite que containers em um mesmo host de um cluster consigam se comunicar. Permite que serviços e containers "standalone" se comuniquem na mesma rede. 
 

* Deploy com Docker Stack
  * __[docker-compose.yml](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-07/docker-compose.yml)__ - arquivo de composição de serviços usado através do comando docker-compose em um nó manager.
  * __```docker stack deploy --compose-file docker-compose.yml NOME_STACK```__ - cria uma stack de arquivos a partir de um compositor docker-compose.yml.
  * __```docker stack ls```__ - apresenta a lista de stack de serviços. 
  
  |  NAME  |  SERVICES | ORCHESTRATOR |
  | :----: | :-------: | :----------: |
  |  vote  |     6     |    Swarm     | 
  
  * __```docker stack rm NOME_STACK```__ - remove a stack de serviços. 

