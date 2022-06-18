[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-06/aulas)

# Deploy com Docker Stack

# Para saber mais: Volumes no Swarm

Por padrão, tanto o **Docker** no modo standalone quanto o **Docker Swarm**, partilham apenas de um driver **local** para uso de volumes. 
Isso quer dizer que o **Docker Swarm** não possui, até então, solução nativa para distribuir volumes entre os nós.

Então, no exemplo do vídeo anterior, ao definirmos o volume para cada serviço, criamos um volume local dentro de cada nó que for executar a tarefa.
Logo, os volumes **não** são compartilhados entre os diferentes nós do cluster.

Existem soluções que não são nativas do Docker Swarm para utilizar volumes distribuídos entre nós,
que podem ser consultadas na [Docker Store](https://store.docker.com/search?category=volume&q=&type=plugin).

# O que aprendemos?

Nesta aula, aprendemos:

* O **docker-compose.yml** também pode ser utilizado para serviços de um swarm
* Novas instruções a partir da versão 3, como **deploy** e suas instruções internas
* Uma **stack** é uma pilha de serviços trabalhando em conjunto
* Como criar e remover nossa própria **stack** utilizando o comando ```docker stack```

[PRÓXIMO >>](https://github.com/pvreboucas/docker-swarm-orquestrador/)
