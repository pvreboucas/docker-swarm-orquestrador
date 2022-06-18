[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-04/aulas/01-readicionando-um-manager.md)

# Registringindo Nós

Por conseguinte, como restringir que os tarefas sejam executadas dentro dos nós managers?

Para tanto, se achar necessários recriar o serviço, removeremos todos os serviços em execução para reconfigurá-los:

```docker service rm $(docker service ls -q)```

No entanto, se você já estiver com os cinco nós(3 manager - 1 Leader e 2 Reachable - e 2 workers) não será necessário remover.

Com esse cenário organizado vamos atualizar a Availability do nó, essa coluna determina se o nó executará ou não uma tarefa, mudamos o valor de Active para Drain:

```docker node update --availability drain vm2```

```docker node ls```

|               ID             |    HOSTNAME  |    STATUS    | AVAILABILITY |   MANAGER STATUS       | ENGINE VERSION  |
| :--------------------------: | :----------: | :----------: | :----------: | :--------------------: | :-------------: | 
| eyJhbGciOiJIUzI1NiIsInR5c  * |      vm1     |    Ready     |    Active    |      Leader            |   19.03.3       | 
| eyJzdWIiOiIxMjM0NTY3ODkwI    |      vm2     |    Ready     |    Drain     |      Reachable         |   19.03.3       | 
| SflKxwRJSMeKKF2QT4fwpMeJf    |      vm3     |    Ready     |    Active    |      Reachable         |   19.03.3       | 
| ABFEzdWIiOixMjM0NTY3ilghw    |      vm4     |    Ready     |    Active    |                        |   19.03.3       | 
| YDaxdrgvsSMeKF2QT4fwegjdg    |      vm5     |    Ready     |    Active    |                        |   19.03.3       | 

Desta maneira a tarefa não será mais executada na vm2, mas ela poderá ser redirecionada para outro nó, inclusive um nó manager:

``` docker service ps ulaxnhi770p4 ```

|      ID       |            NAME            |              IMAGE              |     NODE     |     DESIRED STATE       |     CURRENT STATE          |   ERROR  |  PORTS   | 
| :-----------: | :------------------------: | :-----------------------------: | :----------: |  :--------------------: | :------------------------: | :------- | :------: |
| x06k7hbl96lz  |     objective.allen.1      |  aluracursos/barbearia:latest   |      vm3     |        Running          |  Running 6 minutes ago     |          |          |
| n27sa3uw017c  |     \_objective.allen.1    |  aluracursos/barbearia:latest   |      vm2     |        Shutdown         |  Failed about a second ago |          |          |

No entanto, desta forma o nó não executa nenhuma tarefa, mas o manager precisa executar tarefas administrativas, então qual melhor maneira de restringir?

comando:

* __```docker service rm $(docker service ls -q)```__ - pelo ssh da VM de um nó manager, apaga-se todos os serviços de um cluster. O -q retorna somente o campo ID.
* __```docker node update --availability drain VM```__ - pelo ssh da VM de um nó manager, atualiza a o Availability de Active para Drain para impedir que o nó execute tarefas.


[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-04/aulas/05-restringindo-servicos.md)
