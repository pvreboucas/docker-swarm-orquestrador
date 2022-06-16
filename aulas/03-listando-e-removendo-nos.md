[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/01-criando-o-primeiro-worker.md)

# Listando e removendo nós

Para sabermos quais nós existem dentro de um cluster vamos acessar o terminal do nó manager 

```docker-machine ssh vm1``` 

e invocar o comando que lista os nós existentes: 

```docker node ls```

|               ID           |    HOSTNAME  |    STATUS    | AVAILABILITY |   MANAGER STATUS       | ENGINE VERSION  |
| :------------------------: | :----------: | :----------: | :----------: | :--------------------: | :-------------: | 
| eyJhbGciOiJIUzI1NiIsInR5c  * |      vm1     |    Ready     |    Active    |      Leader            |   19.03.3       | 
| eyJzdWIiOiIxMjM0NTY3ODkwI  |      vm2     |    Ready     |    Active    |                        |   19.03.3       | 
| SflKxwRJSMeKKF2QT4fwpMeJf  |      vm3     |    Ready     |    Active    |                        |   19.03.3       | 

*OBS: O * indica que de qual nó foi chamado o comando*
*OBS: nós workers não pode visulizar e alterar estados de configuração*

Caso queiramos remover um nó do cluster swarm, primeiro acessamos o terminal do nó que queremos remover 

```docker-machine ssh vm3```

,invocamos o comando 

```docker swarm leave```

para mudarmos o status do nó worker para Down.

|               ID           |    HOSTNAME  |    STATUS    | AVAILABILITY |   MANAGER STATUS       | ENGINE VERSION  |
| :------------------------: | :----------: | :----------: | :----------: | :--------------------: | :-------------: | 
| eyJhbGciOiJIUzI1NiIsInR5c  * |      vm1     |    Ready     |    Active    |      Leader            |   19.03.3       | 
| eyJzdWIiOiIxMjM0NTY3ODkwI  |      vm2     |    Ready     |    Active    |                        |   19.03.3       | 
| SflKxwRJSMeKKF2QT4fwpMeJf  |      vm3     |    Down     |    Active    |                        |   19.03.3       | 

Por conseguinte, por dentro do nó manager, será possível chamarmos o comando 

```docker node rm SflKxwRJSMeKKF2QT4fwpMeJf```

para remover o nó worker vm3 com status Down.

|               ID           |    HOSTNAME  |    STATUS    | AVAILABILITY |   MANAGER STATUS       | ENGINE VERSION  |
| :------------------------: | :----------: | :----------: | :----------: | :--------------------: | :-------------: | 
| eyJhbGciOiJIUzI1NiIsInR5c  * |      vm1     |    Ready     |    Active    |      Leader            |   19.03.3       | 
| eyJzdWIiOiIxMjM0NTY3ODkwI  |      vm2     |    Ready     |    Active    |                        |   19.03.3       | 


comandos:
* __```docker node ls```__ - pelo ssh da VM manager é apresentada a lista de nós existentes do cluster swarm.
* __```docker swarm leave```__ - pelo ssh da VM worker é alterado o status do nó de Ready para Down.
* __```docker node rm ID_VM```__ - pelo ssh da VM manager é removido um nó do cluster pelo seu ID.


[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/05-subindo-um-servico.md)
