[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/03-listando-e-removendo-nos.md)

# Subindo um Serviço

Chegou a hora de subir um container em um nó worker do nosso swarm, por isso vamos acessar um dos nossos workers ```docker-machine ssh vm2``` 
e criar nosso container usando os comandos aprendidos no [curso anterior](https://github.com/pvreboucas/docker/blob/main/Docker%20Cheat%20Sheet%20-%20Os%20Comandos%20Utilizados.md).

No entanto, a partir de agora não basta configurar as portas de comunicação do container com a vm pelo parâmetro *-p 8080:3000*, 
é necessário configurarmos a rede pelo nó manager do swarm, que é responsável pelo balanceamento de carga.

Portanto, através do nó manager vamos inspecionar o nó worker em que criamos o container:

```docker node inspect vm2```

Ao observamos na chave Status achamos o endereço IP em ADDR, a exemplo 192.168.0.2. Através deste endereço de IP conseguimos acessar a aplicação pelo browser digitando o IP e a porta exposta pelo container: 192.168.0.2:8080.
Mas ainda não há um balanceamento de carga, desta forma o nó manager não está fazendo seu trabalho.

Portanto vamos acessar o nó manager ```docker-machine ssh vm1``` e criar não um container, e sim um serviço que cria as imagens do contâineres nos nós workers.

```docker service create -p 8080:3000 aluracursos/barbearia```

Agora temos o balanceamento de carga? Não necessariamente, ainda é preciso fazer mais algumas configurações na próxima aula.

comandos:
* __```docker node inspect VM_WORKER```__ - pelo ssh da VM manager é inspecionado um nó worker existente no cluster swarm.
* __```docker service create -p 8080:3000 NOME_IMAGEM```__ - pelo ssh da VM manager é criado um serviço dentro de um swarm direcionando a imagem do container para os workers.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/07-tarefas-e-o-routing-mesh.md)
