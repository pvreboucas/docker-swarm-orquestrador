[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-05/aulas/01-servicos-replicados.md)

# Serviços Globais

Outro tipo de serviço são os globais, com eles designamos tarefas tanto para managers como workers.

Se quisermos criar um serviço novo, nós colocamos a flag --mode global para que este seja replicado dentre os nós

``` docker service create -p 8080:3000 --mode global aluracursos/barbearia ```

``` docker service ls ```

|      ID       |            NAME            |        MODE       |   REPLICAS   |           IMAGES             |        PORTS        |
| :-----------: | :------------------------: | :---------------: | :----------: |  :-------------------------: | :-----------------: |
| mh3mricgt2p0  |      musing_mendel         |       global      |      5/5     | aluracursos/barbearia:latest |  \*:8080->3000/tcp  |


[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-06/aulas)
