[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-01/aulas/07-Usando-o-docker-swarm.md)

# Criando um Cluster

Para criarmos um cluster swarm precisamos configurar a rede, primeiro vamos entrar no terminal da máquina virtual ```docker-machine ssh vm1```, em seguida usaremos o comando ```docker swarm init``` para iniciarmos o cluster.

De início será apresentado um error, pois a VM não vai reconhecer o IP, por isso vamos adicionar um parâmetro no comando para definir a interface de rede que tem o endereço de IP da máquina física: ```docker swarm init --advertise-addr 192.168.0.2```

Agora o cluster será iniciado, e na descrição é apresentado o ID de identificação e um TOKEN deste nó do cluster. Por ser o primeiro nó, este será designado como o nó *manager*, ou gerenciador.

``` Swarm initialized: current node (ID) is now a manager. ```

``` 
To add a worker to this swarm, run the following command: 

docker swarm join --token TOKEN 192.168.0.2:2376 
```

comandos:

* __```docker swarm init```__ - inicia as configurações de cluster da VM pelo terminal após usar o comando ```docker-machine ssh NOME_VM```.
* __```docker swarm init --advertise-addr ENDERECO_IP```__ - inicia as configurações de cluster da VM pelo terminal após usar o comando ```docker-machine ssh NOME_VM``` com um endereço de IP configurado para identifiação da interface de rede.
* __```docker info```__ - usado por dentro do terminal da VM traz a informação se está presente em um cluster swarm.


[PRÓXIMO >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-02/aulas)
