[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/05-subindo-um-servico.md)

# Tarefas e o Routing Mesh

Como vimos na aula anterior foi criado um serviço dentro do swarm e agora precisamos designar qual container vai executar as tarefas que o cluster será demandado.
Mas antes vamos observar as informações do serviço criado pelo comando:

```docker service ls```

|      ID       |            NAME            |        MODE       |   REPLICAS   |           IMAGES             |        PORTS        |
| :-----------: | :------------------------: | :---------------: | :----------: |  :-------------------------: | :-----------------: |
| ulaxnhi770p4  |      exciting_portrais     |    replicated     |      1/1     | aluracursos/barbearia:latest |  \*:8080->3000/tcp  |

É possível observar que ele replicou a imagem do projeto somente uma vez, que expôs a porta 8080 do serviço para apontar para a 3000 dos containers pelo protocolo tcp.
Como foi replicado apenas uma vez a execução dessa imagem, como que podemos ver para qual worker replicado? Usando o comando:

``` docker service ps ulaxnhi770p4 ```

|      ID       |            NAME            |              IMAGE              |     NODE     |     DESIRED STATE       |     CURRENT STATE       |   ERROR  |  PORTS   | 
| :-----------: | :------------------------: | :-----------------------------: | :----------: |  :--------------------: | :---------------------: | :------- | :------: |
| x06k7hbl96lz  |     exciting_portrais.1    |  aluracursos/barbearia:latest   |      vm2     |        Running          |  Running 6 minutes ago  |          |          |

Observamos que há uma imagem rodando no container hospedado no nó worker vm2, e se colocarmos no browser do navegador o IP tanto do nó worker quanto do nó manager conseguiremos acessar a aplicação,
Lembre que um nó worker não tem como trabalhar com designação de tarefas (routing mesh), portanto se apagarmos manualmente o container no nó worker vm2 oque acontecerá? 
O nó manager vai replicar o serviço para outro nó worker, a exemplo a vm3 se a recriarmos.

|      ID       |            NAME            |              IMAGE              |     NODE     |     DESIRED STATE       |     CURRENT STATE          |   ERROR  |  PORTS   | 
| :-----------: | :------------------------: | :-----------------------------: | :----------: |  :--------------------: | :------------------------: | :------- | :------: |
| 1739zecv7baa  |     exciting_portrais.1    |  aluracursos/barbearia:latest   |      vm3     |        Running          |  Running 2 seconds ago     |          |          |
| x06k7hbl96lz  |     exciting_portrais.1    |  aluracursos/barbearia:latest   |      vm2     |        Shutdown         |  Failed about a second ago |          |          |          |


mas e o que mais o manager pode fazer? Veremos na próxima aula.

comandos:
* __```docker service ls```__ - pelo ssh da VM manager é apresentada a lista de serviços existentes do cluster swarm.
* __```docker service ps ID_SERVICO```__ - pelo ssh da VM manager é apresentado detalhes do serviço ID existente no cluster swarm.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-03/aulas)
