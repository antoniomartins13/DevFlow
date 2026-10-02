# DevFlow — Diagramas de atividade v0.2

Modelo planejado baseado nos oito casos de uso e nas decisões aprovadas. Cada arquivo pode ser aberto separadamente em um renderizador PlantUML. O UC-08 contém dois diagramas para separar comparação de adoção e observação.

| Arquivo | Objetivo |
| --- | --- |
| UC-01-Demanda-Especificacao.puml | Preparar demanda e especificação |
| UC-02-Aprovar-Plano-Execucao.puml | Aprovar critérios quando exigidos e plano/base no CP1 |
| UC-03-Desenvolver-Verificar.puml | Executar tarefa isolada e verificar alteração |
| UC-04-Revisar-Alteracao.puml | Revisar em contexto independente e encaminhar correções |
| UC-05-Validar-Entrega.puml | Validar com roteiro e decisão vinculada à versão |
| UC-06-Acompanhar-Tarefas.puml | Consultar andamento, resultados e pendências |
| UC-07-Configurar-Execucoes.puml | Validar e aplicar configurações autorizadas |
| UC-08-Avaliar-Melhorias.puml | Comparar candidatos e decidir adoção com evidências |

## Como ler

- Raias identificam quem executa cada ação. DevFlow inclui o runner determinístico.
- Losangos representam decisões/condições. Sim/Não identifica o caminho escolhido.
- A atividade final encerra esta execução do caso de uso. Em um caminho de bloqueio, a tarefa continua pendente e pode ser retomada; não significa entrega aprovada.
- Retornos ao UC-03 exigem execução/correção autorizada, novas verificações e revisão do commit afetado. Alteração de escopo/plano exige UC-01/UC-02.
- Casos UC-01 a UC-05 se encadeiam conforme seus gates. Acompanhar e configurar não são etapas obrigatórias repetidas em cada tarefa; UC-08 é trilha separada.
- Decisões e evidências identificam a versão correspondente. Repetições e retomadas reconciliam efeitos externos antes de agir novamente.

## Escopo

No permanente, CP1 aprova plano/base e a integração Mattermost pode fornecer callbacks autorizados. Na Entrega -1, admissão ocorre por movimento humano para a lista Trello Pronto para IA, com limite diário persistente. O protótipo abre MR em draft após testes, aciona revisão por segundo contexto e envia notificações por webhook sem botões. Não incorpora contêiner, SQLite ou Budget Manager.

Browser Use e Archify fornecem evidências quando pertinentes; Stirling PDF é ferramenta auxiliar sob demanda. Nenhuma ferramenta concede aprovação ou dirige os estados. Merge permanece humano e exige revisão humana, CI verde e gates válidos. Estes diagramas não implementam deploy nem ativam pesquisa recorrente.

As fontes PlantUML foram conferidas estruturalmente e comparadas com os fluxos documentados. Não foram compiladas ou renderizadas neste ambiente, que não dispõe de PlantUML/Graphviz. A visualização final depende do renderizador utilizado.
