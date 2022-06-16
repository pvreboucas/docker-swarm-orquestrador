[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/01-o-papel-do-manager.md)

# Como fazer backup do Swarm

Dentro do nó manager podemos realizar o backup de todos os conteúdos, inclusive os logs, para outro diretório.
Encontramos, localmente, esses arquivos no diretório /var/lib/docker/swarm.
Portanto, de forma simplória, há a possibilidade de copiar o diretório, com super usuário, para um outro diretório:

``` sudo cp -r /var/lib/docker/swarm/ backup/ ```

*OBS: você pode optar por outras estratégias de backup deste diretório*

Para recuperar o diretório, com esta abordagem de backup, chamamos o comando:

```sudo cp -r backup/* /var/lib/docker/swarm/ ```

Até aí nenhum comando docker, mas, se apenas copiarmos os arquivo para a pasta original não será o suficiente, temos que forçar as novas configurações, 
assim conseguimos recuperar o controle dos estados de configuração dos nós workers:

``` docker swarm init --force-new-clust --advertise-addr 192.168.0.2 ```

comandos:

* __```docker swarm init --force-new-clust --advertise-addr ENDERECO_IP```__ - pelo ssh da VM manager, força o início de novas configurações de outro cluster ou de backup.

[PRÓXIMA AULA>>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/05-criando-mais-managers.md)
