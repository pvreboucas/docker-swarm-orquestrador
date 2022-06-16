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
  * __```docker run NOME_DA_IMAGEM```__ - cria um container com a respectiva imagem passada como parâmetro.
 

* Gerenciando o cluster com managers
  * __```docker start ID_CONTAINER```__ - inicia o container com id em questão.


* Separando as responsabilidades
  * __```docker rm ID_CONTAINER```__ - remove o container com id em questão.


* Serviços globais e replicados
  * __```docker build -f Dockerfile```__ - cria uma imagem a partir de um Dockerfile.
  
* Driver Overlay
  * __```docker login```__ - inicia o processo de login no Docker Hub.
 

* Deploy com Docker Stack
  * __```hostname -i```__ - mostra o ip atribuído ao container pelo docker (funciona apenas dentro do container).

