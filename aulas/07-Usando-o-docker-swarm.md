[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-01/aulas)

# Usando o Docker Swarm

O Docker Swarm trabalha com o conceito de enxame de contâiners organizados em clusters. 
Cada cluster de contâiner é hospedado em uma máquina virtual - usando um Driver de VM, exemplo VirtualBox - e controlado por uma **docker-machine**.
Essa docker-machine virtualiza o ambiente de um sistema operacional para demais configurações.

![01](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-01/aulas/imagens/docker-machine.png)


* __```docker-machine create -d NOME_DRIVER_VM NOME_VM```__ - cria a máquina virtual com o driver escolhido para a virtualização, exemplo: *docker-machine create -d virtualbox vm1*.   
* __```docker-machine ls```__ - lista as máquinas virtuais instaladas na máquina criadas pela docker-machine.

| NAME         |    ACTIVE    |    DRIVER    |    STATE     |     URL                |     SWARM    |     DOCKER   |       ERRORS |
| :----------: | :----------: | :----------: | :----------: | :--------------------: | :----------: | :----------: | :----------: |
| vm1          |      -       |  virtualbox  |   Running    | tcp://192.168.0.2:2376 |              |   v19.03.3   |              |

* __```docker-machine start NOME_VM```__ - inicia uma máquina virtual parada.
* __```docker-machine ssh NOME_VM```__ - acessa o terminal da máquina virtual.


[PRÓXIMO]()
