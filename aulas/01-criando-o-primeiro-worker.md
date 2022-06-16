[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-01/aulas/10-criando-um-cluster.md)

# Criando o primeiro Worker

Os Workers tem como responsabilidade carregar os contâineres, por sua vez estes são coordenados pelo nó manager.

Para tanto vamos criar outras máquinas virtuais para designá-las como workers do manager vm1 criado na aula anterior.

```docker-machine create -d virtualbox vm2 | docker-machine create -d virtualbox vm3```

Por conseguinte entramos no terminal de cada máquina virtual ``` docker-machine ssh vm2 | docker-machine ssh vm3 ``` 
e digitaremos o comando apresentado na criação do nó manager:

```docker swarm join --token TOKEN 192.168.0.2:2377 ```


*OBS: porta 2377: porta padrão que o docker usa para comunicação entre swarms*

Caso percamos qual comando usar para adicionar um worker a um nó manager, acessamos o nó manager com ```docker-machine ssh vm1``` e chamamos o comando:

```docker swarm join-token worker```

comandos:
* __```docker swarm join --token TOKEN ENDERECO_IP```__ - adiciona uma VM como worker de um nó com TOKEN e ENDERECO_IP.
* __```docker swarm join-token worker```__ - pelo ssh da VM manager é apresentado o comando com token para adicionar workers.


[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/03-listando-e-removendo-nos.md)
