[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-05/aulas/04-servicos-globais.md)

# A rede ingress

A todo esse momento trabalhamos com o docker swarm dentro de uma rede, 
vimos no curso anterior que o docker trabalha com os seguintes tipos de rede:

* __bridge__: permite comunicação entre diferentes contâiners em um mesmo host;
* __host__: habilita a comunicação do contâiner com a máquina host;
* __null__: inexistência de rede;
* __overlay__: rede padrão de um cluster swarm, permite a comunicação de diferentes hosts em um mesmo cluster.

A novidade está no tipo **overlay**, se invocarmos o comando 

```docker network ls```

|   NETWORK ID  |        NAME        |    DRIVER    |    SCOPE    | 
| :-----------: | :----------------: | :----------: | :---------: |  
|       ID      |    bridge          |    bridge    |    local    | 
|       ID      |    docker_gwbridge |    bridge    |    local    | 
|       ID      |    host            |    host      |    local    | 
|   ID_SWARM    |    ingress         |    overlay   |    swarm    | 
|       ID      |    none            |    null      |    local    | 

observaremos o driver Overlay na lista de redes. Por padrão todos os nós do cluster swarm entram nessa rede, 
por mais que os outros nós tenham tipos de rede com IDs diferentes, ao chamarmos o ```docker network ls``` dentro de um nó,
todos eles que estão no mesmo swarm terão sua rede ingress o mesmo ID_SWARM.

Desta forma essa comunicação é mais robusta e direta entre as VMs, e como vantagem ela já é encriptografada.
Se digitarmos o comando ```docker node inspect vm1 --pretty``` notaremos que existe um certificado TLS cadastrado para a comunicação entre as VMs.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-06/aulas/03-service-discovery.md)
