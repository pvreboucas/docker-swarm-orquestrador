[<< AULA ANTERIOR](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-02/aulas/07-tarefas-e-o-routing-mesh.md)

Se tentarmos usar o comando ```docker swarm leave``` por dentro do nó manager nós receberemos uma mensagem de aviso para não fazermos isso,
mas se mesmo quisermos tirar o manager do cluster swarm usamos o parâmetro ``` docker swarm leave --force```. E quais serão as consequências?

* Não conseguiremos mais ajustarmos a configuração do nosso cluster swarm
* Os nós workers continuarão funcionando, mas não seus estados não estarão mais acessíveis

comandos:
 * __```docker swarm leave --force```__ - pelo ssh da VM manager é forçada a saída do cluster swarm, consequentemente toda a configuração se perde, e os workers ficam sem manage.

[PRÓXIMA AULA >>](https://github.com/pvreboucas/docker-swarm-orquestrador/blob/aula-03/aulas/03-como-fazer-backup-do-swarm.md)
