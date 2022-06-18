[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/07-algoritmo-de-consenso-raft.md)

# Readicionando um manager

Por quanto, agora que existe mais de um manager, como conseguimos orquestrar ou balancear as designações de tarefas para os nós e evitar que os managers executem tarefas?

Primeiro vamos ajustar nossos nós managers. A vm1 agora tem o status manager de Unreachable, por isso vamos rebaixá-la para um worker com o comando:

```docker node demote vm1```

Em seguida a removemos do cluster:

```docker node rm vm1```

Em seguida adicionamos novamente a vm1 como um nó manager do cluster.

```docker swarm join-token manager```

```docker swarm join --token TOKEN ENDERECO_IP```

comandos:

* __```docker node demote VM_MANAGER```__ - pelo ssh da VM de um manager, rebaixa um nó manager para worker.
* __```docker node rm VM_MANAGER```__ - pelo ssh da VM de um manager, apaga um nó worker do cluster.



[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-04/aulas/03-restringindo-nos.md)
