[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-04/aulas/05-restringindo-servicos.md)

# Serviços Replicados

Que tipos de serviços vamos querer rodar nos nós managers?
Serviços de monitoramento, segurança, configuração, etc.
Veremos quais são os tipos de serviços que o docker swarm disponibiliza.

Por exemplo vamos ver um tipo de serviço aplicado abaixo:

```docker service ls```

|      ID       |            NAME            |        MODE       |   REPLICAS   |           IMAGES             |        PORTS        |
| :-----------: | :------------------------: | :---------------: | :----------: |  :-------------------------: | :-----------------: |
| ulaxnhi770p4  |      exciting_portrais     |    replicated     |      1/1     | aluracursos/barbearia:latest |  \*:8080->3000/tcp  |

Se inspecinarmos o serviço com:

```docker service ps ulaxnhi770p4```

serão listadas as tarefas sendo executadas nesse serviço:

|      ID       |            NAME            |              IMAGE              |     NODE     |     DESIRED STATE       |     CURRENT STATE       |   ERROR  |  PORTS   | 
| :-----------: | :------------------------: | :-----------------------------: | :----------: |  :--------------------: | :---------------------: | :------- | :------: |
| x06k7hbl96lz  |     exciting_portrais.1    |  aluracursos/barbearia:latest   |      vm5     |        Running          |  Running 6 minutes ago  |          |          |


Se observamos, somente um nó está recebendo a designação de uma tarefa, portanto vamos copiar essa tarefa para que outros nós as recebam para balancearmos a carga:

``` docker service update --replicas 4 ulaxnhi770p4 ```

```docker service ps ulaxnhi770p4```


|      ID       |            NAME            |              IMAGE              |     NODE     |     DESIRED STATE       |     CURRENT STATE       |   ERROR  |  PORTS   | 
| :-----------: | :------------------------: | :-----------------------------: | :----------: |  :--------------------: | :---------------------: | :------- | :------: |
| x06k7hbl96lz  |     exciting_portrais.1    |  aluracursos/barbearia:latest   |      vm5     |        Running          |  Running 6 minutes ago  |          |          |
|    ID_VM3     |     exciting_portrais.2    |  aluracursos/barbearia:latest   |      vm3     |        Running          |  Running 1 minutes ago  |          |          |
|    ID_VM4     |     exciting_portrais.3    |  aluracursos/barbearia:latest   |      vm4     |        Running          |  Running 1 minutes ago  |          |          |
| x06k7hbl96lz  |     exciting_portrais.4    |  aluracursos/barbearia:latest   |      vm5     |        Running          |  Running 1 minutes ago  |          |          |

Perceba que por falta de workers habilitados, a vm5 recebeu 2 tarefas do serviço.

comandos:

* __``` docker service update --replicas 4 ID_SERVICO ```__ - pelo ssh de um manager, atualiza a quantidade de tarefas de um serviço a serem balanceadas entre os workers.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-05/aulas/04-servicos-globais.md)
