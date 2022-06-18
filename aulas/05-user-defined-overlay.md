[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-06/aulas/03-service-discovery.md)

# User-defined overlay

Para configurar vamos criar uma rede no docker com o driver overlay:

``` docker network driver -d overlay rede_overlay ```

portanto, se chamarmos o comando ```docker network ls``` veremos a nossa rede criada.
No entanto, neste primeiro momento somente o nós managers vão enxergar essa nova rede overlay.
Os workers conhecerão após receberem uma tarefa.

Em seguida criaremos um serviço utilizando a rede rede_overlay:

``` docker service create --name servico --network rede_overlay --replicas 2 alpine sleep 1d ```

Portanto, se novamente procurarmos pelos containers e seus respectivos nomes, conseguiremos através do terminal de cada nó identificar que estão dentro da rede rede_overlay.

```
docker service ps ID_SERVICO

docker container ls

docker exec -it NOME_CONTAINER sh

docker network ls

docker network inspect

```

Portanto, desta forma, criando a nossa própria rede overlay, conseguimos pingar de um nó para o outro através do nome.


comando:

* __```docker network driver -d overlay NOME_REDE_OVERLAY```__ - cria uma rede docker do tipo overlay.
* __```docker service create --name NOME_SERVICO --network NOME_REDE_OVERLAY```__ - cria um serviço com uma rede overlay previamente criada.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-07/aulas/)
