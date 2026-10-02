# Escopo

| Área | O que o DevFlow deve oferecer |
| --- | --- |
| Demanda e planejamento | Organizar tarefas, especificações, critérios de aceite, dependências e planos para aprovação. |
| Desenvolvimento | Executar tarefas autorizadas em worktrees isolados, usando as CLIs e os agentes disponíveis. |
| Verificação e revisão | Rodar os testes do projeto, aproveitar evidências válidas do CI e realizar revisão independente, incluindo alertas sobre testes enfraquecidos. |
| Validação humana | Entregar roteiro com funcionalidade, casos de borda e possíveis regressões, indicando ações e resultados esperados. |
| Acompanhamento | Integrar Trello, GitLab e Mattermost; registrar estado, decisões, resultados e pendências. |
| Controle operacional | Aplicar permissões, gates e limites de consumo; tratar falhas, retomadas e repetições sem duplicar ações. |
| Melhoria contínua | Investigar gargalos, ferramentas e novos modelos; comparar resultados antes de propor adoção por MR aprovado por você. |

## Fronteiras

As fronteiras também estão definidas:

- O runner determinístico controla o fluxo e as autorizações.
- Você mantém os checkpoints aprovados; o merge permanece humano.
- Melhorias e atualizações não são adotadas automaticamente.
- O DevFlow não substitui as aplicações, o Trello, o GitLab ou as suítes dos projetos.
- n8n, Orca, Flowise, CrewAI, LangGraph e Ruflo ficam fora do escopo; gstack fica para avaliação após o MVP.

O sucesso será medido por intervenções humanas por entrega aceita, consumo total por entrega correta e acerto na primeira tentativa, incluindo falhas e retrabalho. Uma melhoria pode ser simplesmente remover uma etapa ou ferramenta.
