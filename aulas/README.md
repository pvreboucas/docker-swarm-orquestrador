[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-04/aulas)

# Para saber mais: service scale

Vamos supor que temos um serviço com id ci10k3u7q6ti. Como podemos escalar esse serviço para ter 5 réplicas?

Aprendemos uma das possibilidades de alterar o número de réplicas de um serviço utilizando o comando ```docker service update --replicas 5 ci10k3u7q6ti```,
mas esse não é o único meio!

Para isso também temos o comando ```docker service scale```. Utilizando o id, podemos atualizar com o comando:

```
docker service scale ci10k3u7q6ti=5
```

Nesse caso, definimos 5 réplicas para o serviço. Os dois comandos produzem o mesmo resultado, o segundo é apenas uma forma resumida do primeiro comando.

# O que aprendemos?

Nesta aula, aprendemos:

* Serviços replicados rodam em um ou mais nós do swarm
* Serviços globais rodam em todos os nós do swarm
* Nós **managers** por padrão trabalham como **workers**
* Serviços como monitoramento e segurança são bons exemplos de serviços globais
* Como definir o modo que o serviço será criado utilizando a flag ```--mode``` no momento da criação do serviço

[PRÓXIMO >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-06/aulas)
