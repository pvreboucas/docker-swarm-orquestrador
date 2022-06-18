[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-04/aulas/03-restringindo-nos.md)

# Restringindo Serviços

A melhor forma é restringir para quais nós o serviço será restrido a ser executado, como?

com o comando:

```docker service update --constraint-add node.role==worker ulaxnhi770p4```

Desta maneira adicionamos uma restrição ao serviço para que rode somente em nós workers.

``` docker service ps ulaxnhi770p4 ```

|      ID       |            NAME            |              IMAGE              |     NODE     |     DESIRED STATE       |     CURRENT STATE          |   ERROR  |  PORTS   | 
| :-----------: | :------------------------: | :-----------------------------: | :----------: |  :--------------------: | :------------------------: | :------- | :------: |
| rgvsSMeKF2QT  |     objective.allen.1      |  aluracursos/barbearia:latest   |      vm5     |        Running          |  Running 2 minutes ago     |          |          |
| x06k7hbl96lz  |     objective.allen.1      |  aluracursos/barbearia:latest   |      vm3     |        Shutdown         |  Failed about a second ago |          |          |
| n27sa3uw017c  |     \_objective.allen.1    |  aluracursos/barbearia:latest   |      vm2     |        Shutdown         |  Failed about a minute ago |          |       

comandos:

* __```docker service update --constraint-add node.role==worker ID_SERVICE```__ - pelo ssh de uma VM manager é restringido um serviço para que apenas nós workers o executem.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-05/aulas)
