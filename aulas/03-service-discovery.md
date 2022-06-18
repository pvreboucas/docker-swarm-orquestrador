[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-06/aulas/01-a-rede-ingress.md)

# Service discovery

O que mais que o driver overlay pode fazer de interessante? Um conceito bem famoso no dia de hoje, bem moderno, é um cara chamado Service Discovery, o que é o Service Discovery? Se formos traduzir literalmente é descobrir um serviço, mas é descobrir esse serviço a partir do nome dele.

Ou seja, não precisamos ficar chamando um serviço ou outro pelo IP dele e sim chamar ele simplesmente pelo nome, que é uma maneira bem mais prática de conseguirmos comunicar diferentes serviços.

Então, se dermos um ```docker network ls``` aqui, como é que será que esse driver overlay permite buscarmos as informações que o comando traz? 

Como exemplo vamos criar um serviço replicado entre dois nós:

```
docker service create --name servico --replicas 2 alpine sleep 1d
```

agora com o comando abaixo descobriremos quais nós foram designados para o serviço:

```docker service ps ID_SERVICO```

com os nós identificados vamos chamar o comando seguinte em cada um deles 

```docker container ls```

por ele achamos o nome do contâiner. Por fim, com o nome do contâiner vamos acessar o terminal de cada um:

```docker exec -it NOME_CONTAINER sh```

 faremos a comunicação de um com o outro através do IP com ping,
 e quem se encarregará de identificá-los na rede será o **Service Discovery**.
 No entanto se usarmos o nome do contâiner receberemos um bad request.
 Mas há como configurar para que o Service Discovery nos ajude.

comando:
* __```docker service create --name NOME_SERVICO```__ - pelo ssh da VM manager é criado um serviço dentro de um swarm indicando um nome para este.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-06/aulas/05-user-defined-overlay.md)
