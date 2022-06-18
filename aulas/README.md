[<< ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-05/aulas)

# Driver Overlay

# Para saber mais: Containers e Overlay

Por mais que o driver *overlay* seja responsável por comunicar múltiplos hosts em uma mesma rede,
também podemos conectar containers em escopo local criados com o comando *docker container run* em redes criadas com esse driver.

Para isso, basta no momento da criação da rede utilizarmos a flag *--attachable*:

```
docker network create -d overlay --attachable my_overlay
```

Com o comando acima, conseguiremos conectar tanto serviços como containers __"standalone"__ em nossa rede *my_overlay*.

# O que aprendemos?

Nesta aula, aprendemos:

* A rede **ingress** é a padrão criada junto com nosso swarm
* O driver **overlay** é utilizado para a comunicação entre nós em diferentes hosts
* Como criar nossas próprias redes com o driver **overlay** utilizando o comando ```docker network create -d overlay```
* Redes overlays criadas manualmente (*User-Defined Overlay*) permitem a comunicação entre serviços por seus nomes (*Service Discovery*)
* As redes criadas com o driver **overlay** são listadas de maneira *lazy* para **workers**

[PRÓXIMO >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-07/aulas)
