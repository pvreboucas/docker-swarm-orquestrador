[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/05-criando-mais-managers.md)

# Algoritmo de consenso RAFT

Cabe a pergunta: Como que o docker swarm determina qual nó manager Reachable será o novo Leader?

Para isso o docker swarm usa o algoritmo de consenso RAFT, funciona como uma forma de eleição entre os nós, 
isso é determinado pelos critérios de cada nó, é eleito o que pode suportar mais nós em caso de falhas.

Fórmula do RAFT:

N = número de managers
Suporta (N-1)/2 falhas
Deve ter no mínimo (N/2)+1 de quórum

*OBS: A empresa que mantém o docker recomenda para um desempenho melhor do RAFT o uso de 3, 5 ou 7 managers
para que seja possível entrar em consenso sem aumentar a quantidade de candidatos*

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/tree/aula-04/aulas)
