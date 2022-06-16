[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/03-como-fazer-backup-do-swarm.md)

# Criando mais Managers

Podemos criar mais de um manager no nosso swarm. Para isso digitamos no terminal do nó manager vm1 o comando:

```docker swarm join-token manager```

o comando de retorno é semelhante ao comando de adicionar um worker, a diferença está no sufixo do token para distinguir a designação do nó.
Com a adição de novos nós managers, ao listarmos os nós com ```docker node ls``` veremos três nós managers, sendo um deles o Leader e os outros dois Reachable.

Portanto, se nosso nó manager Leader parar de funcionar ele recebe o ManagerStatus de Unreachable, 
por conseguinte um dos outros dois nós Reachable é designado como Leader.

comandos:

* __```docker swarm join-token manager```__ - pelo ssh da VM manager exibe o comando para adcionar novos nós managers.
* __```docker node ls --format {{.ManagerStatus}}```__ - exibe apenas o resultado da coluna de ManagerStatus do comando docker node ls.


[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/07-algoritmo-de-consenso-raft.md)
