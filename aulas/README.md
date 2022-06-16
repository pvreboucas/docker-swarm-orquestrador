[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador)

# Para saber mais: Cloud e Docker Machine

Durante o curso, utilizaremos a Docker Machine apenas para criarmos nosso ambiente com diversas máquinas isoladas e iniciarmos nosso cluster.

Porém, a Docker Machine também é muito utilizada com provedores de serviço em nuvem, como a AWS! Podemos definir nossas credenciais, e, utilizando o driver amazonec2, temos a possibilidade de criar diversas máquinas nos servidores da Amazon!

Caso tenha interesse, mais informações podem ser obtidas na [documentação oficial](https://docs.docker.com/machine/examples/aws/).


# O que aprendemos?

Nesta aula, aprendemos:

* O **Docker Swarm** é um *orquestrador*
* O **Docker Swarm** é capaz de alocar e reiniciar containers de maneira automática
* Como criar máquinas já provisionadas para utilizar o Docker com a **Docker Machine** utilizando comando ```docker-machine create```
* Um *cluster* é um conjunto de máquinas dividindo poder computacional
* Como criar um cluster utilizando o **Docker Swarm** utilizando o comando ```docker swarm init```

[PRÓXIMO >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-02/aulas)
