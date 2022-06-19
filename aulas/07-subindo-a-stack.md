[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-07/aulas/02-definindo-o-arquivo-de-composicao.md)

# Subindo a stack

Com o arquivo [docker-compose.yml](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-07/docker-compose.yml) criado vamos criar e copiá-lo para um nó manager para usá-lo.

```cat > docker-compose.yml```

Em seguida faremos o deploy desse serviço, que usa um conjunto de arquivos, para fazer deploy de um conjunto ou pilha de arquivos com docker-compose, usamos o comando:

```docker stack deploy --compose-file docker-compose.yml vote```

Portanto após a conclusão do processamento podemos chamar o comando abaixo para listarmos quantos serviços há na stack:

```docker stack ls```

|  NAME  |  SERVICES | ORCHESTRATOR |
| :----: | :-------: | :----------: |
|  vote  |     6     |    Swarm     | 

Por conseguinte se listarmos os serviços 

```docker service ls```

veremos que aos poucos são feitas as replicas das tarefas para os nós.

Para uma [visualização gráfica da stack](https://github.com/dockersamples/docker-swarm-visualizer) acesse o IP local com a porta :8080 [192.168.0.2:8080](http://192.168.0.2:8080) para este exemplo.

Para a visualização da aplicação do resultado votação acesse o IP local com a porta :5001 [192.168.0.2:5001](http://192.168.0.2:5001).

Para a visualização da aplicação de votação acesse o IP local com a porta :5000 [192.168.0.2:5000](http://192.168.0.2:5000).

Caso queira remover toda a stack basta chamar o comando:

```docker stack rm vote```



comando:

* __```docker stack deploy --compose-file docker-compose.yml NOME_STACK```__ - cria uma stack de arquivos a partir de um compositor docker-compose.yml.
* __```docker stack ls```__ - apresenta a lista de stack de serviços.
* __```docker stack rm NOME_STACK```__ - remove a stack de serviços. 

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/)
