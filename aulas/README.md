[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-03/aulas)

# Para saber mais: Outras restrições

No último vídeo vimos como podemos adicionar restrições a um serviço utilizando o comando:

```
docker service update --constraint-add
```

Utilizamos o comando acima para restringir serviços a funcionarem apenas em nós *managers* ou *workers*.

Porém, também podemos impor outros tipos de restrições, como id, hostname e o próprio role. Vamos ver alguns exemplos!

Caso quiséssemos restringir o serviço de id ci10k3u7q6ti para funcionar apenas em um nó com id t76gee19fjs8, poderíamos utilizar o comando:

```
docker service update --constraint-add node.id==t76gee19fjs8 ci10k3u7q6ti
```

Se o objetivo fosse fazer o serviço rodar apenas em nossa vm4 por exemplo, uma possibilidade seria utilizar:

```
docker service update --constraint-add node.hostname==vm4 ci10k3u7q6ti
```

Por fim, podemos também remover restrições criadas utilizando o comando de atualização passando a flag --constraint-rm. Para remover as duas restrições anteriores:

```
docker service update --constraint-rm node.id==t76gee19fjs8 ci10k3u7q6ti

docker service update --constraint-rm node.hostname==vm4 ci10k3u7q6ti

```

Após esse momento, quaisquer novas réplicas criadas para esse serviço poderão ser alocadas sem restrição alguma!

# O que aprendemos?

Nesta aula, aprendemos:

* Como readicionar um **manager** posterior a uma falha
* Restringir nós de executarem quaisquer serviços utilizando o *docker node update --availability drain*
* Restringir serviços de serem executados em determinados nós utilizando o *docker service update --constraint-add*



[PRÓXIMO >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-05/aulas)
