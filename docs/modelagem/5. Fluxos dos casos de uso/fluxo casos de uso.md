# Fluxos de Casos de Uso

## UC-01 — Preparar demanda e especificação

Fluxo principal:

1. A equipe informa o problema, o objetivo e o projeto envolvido.
2. O DevFlow registra escopo, restrições e dependências.
3. A equipe, com apoio de IA quando necessário, prepara a especificação e os critérios de aceite.
4. O DevFlow identifica informações faltantes e solicita esclarecimentos.
5. A especificação é registrada e encaminhada para planejamento.
Alternativas:

- Informação insuficiente: a tarefa aguarda esclarecimento.
- Dependência pendente: bloqueia a parte dependente; partes independentes podem avançar se autorizadas.
- Demanda proposta pela IA: fica registrada como proposta, sem autorização automática.
Resultado: especificação pronta para planejar.

## UC-02 — Aprovar plano e execução

Fluxo principal:

1. Em tarefas médias ou grandes, o responsável aprova os critérios.
2. O planejador prepara o plano, impacto, verificações e modelagem ou protótipo quando necessário.
3. O DevFlow apresenta um pacote objetivo para decisão.
4. O responsável aprova o plano e a base no CP1.
5. O DevFlow verifica e registra a autorização.
Alternativas:

- Ajustes solicitados: o plano é revisado e reapresentado.
- Rejeição: a implementação não começa.
- Alteração do plano ou da base: a autorização é reavaliada.
- Ausência de resposta: a tarefa continua aguardando.
Resultado: execução autorizada para o plano e a base identificados.

## UC-03 — Desenvolver e verificar a alteração

Fluxo principal:

1. O DevFlow verifica autorização, dependências, recursos e limites.
2. Prepara ou retoma o worktree e a branch da tarefa.
3. O executor recebe o contexto necessário e implementa a alteração.
4. O DevFlow verifica o escopo e executa os testes obrigatórios.
5. Registra diff, commit, resultados e roteiro de validação.
6. Prepara o MR em draft conforme a etapa autorizada e encaminha para revisão.
Alternativas:

- Limite atingido: a execução é adiada.
- Teste falha ou alteração sai do escopo: o avanço é bloqueado para correção.
- Interrupção: o estado é preservado para retomada.
- Falha na publicação: o GitLab é consultado antes da repetição, evitando MR duplicado.
Resultado: alteração verificada e disponível para revisão.

## UC-04 — Revisar a alteração

Fluxo principal:

1. Um segundo contexto de IA recebe especificação, diff e evidências.
2. O revisor verifica atendimento aos requisitos, correção, riscos e efeitos indiretos.
3. Confere testes removidos ou enfraquecidos e a cobertura do roteiro de validação.
4. Acrescenta evidências de navegador e comparação arquitetural quando pertinentes.
5. Registra o parecer e os achados vinculados ao commit.
6. Sem pendências bloqueantes, encaminha para validação.
Alternativas:

- Problema encontrado: retorna ao UC-03, seguido de novos testes e revisão.
- Evidência insuficiente: registra a lacuna e bloqueia a conclusão.
- Commit alterado: reavalia o parecer.
- Correção exige mudança de plano: retorna ao UC-02.
Resultado: parecer independente; o merge continua humano.

## UC-05 — Validar entrega com roteiro de testes

Fluxo principal:

1. O DevFlow apresenta versão, ambiente, pré-condições e dados de teste.
2. O validador executa os cenários humanos requeridos.
3. Verifica funcionalidade, casos de borda e regressões indiretas pertinentes.
4. Registra resultados observados e evidências.
5. O responsável registra a decisão do checkpoint.
6. Com os demais gates cumpridos, a entrega fica disponível para decisão humana de merge.
Alternativas:

- Falha ou regressão: retorna ao UC-03.
- Ambiente indisponível ou roteiro incompleto: validação bloqueada.
- Cenário obrigatório não executado: validação pendente.
- Novo commit: resultados e aprovações afetados são reavaliados.
Resultado: validação registrada para a versão testada.

## UC-06 — Acompanhar tarefas e resultados

Fluxo principal:

1. O responsável consulta uma tarefa ou abre uma notificação.
2. O DevFlow apresenta estado, bloqueios, dependências e decisões pendentes.
3. Disponibiliza plano, MR, testes, parecer e informações de consumo.
4. Informa o próximo passo e quem precisa agir.
Alternativas:

- Integração indisponível: mostra o último estado conhecido, indicando a limitação.
- Acesso sem permissão: a consulta é negada.
- Notificação repetida: não duplica efeitos nem libera etapas.
Resultado: responsável informado sobre o andamento.

## UC-07 — Configurar e controlar as execuções

Fluxo principal:

1. O responsável seleciona o projeto ou configuração.
2. Define repositórios, verificações, executores por etapa e limites.
3. O DevFlow valida permissões, consistência e compatibilidade.
4. Mudanças sujeitas ao fluxo de aprovação passam por MR e testes.
5. A configuração aprovada é registrada e aplicada às execuções pertinentes.
Alternativas:

- Configuração inválida: mantém a configuração anterior.
- Mudança afeta tarefa em andamento: reavalia compatibilidade e autorizações.
- Limite atingido: bloqueia novas execuções afetadas.
- Testes falham ou falta aprovação: a mudança não é adotada.
Resultado: operação com configuração válida e rastreável.

## UC-08 — Avaliar melhorias e novos modelos

Fluxo principal:

1. Um gargalo, ideia ou descoberta é registrado.
2. O pesquisador propõe uma hipótese e uma comparação com métricas e limites.
3. O responsável autoriza o experimento.
4. O experimento compara a configuração atual com a candidata.
5. Um avaliador independente confere ganhos, regressões, consumo e limitações.
6. O responsável recebe a recomendação e decide.
7. Uma adoção aprovada ocorre por MR, inicialmente em um conjunto limitado de tarefas.
Alternativas:

- Sem necessidade ou compatibilidade: proposta rejeitada.
- Sem orçamento ou autorização: experimento adiado.
- Ganho insuficiente ou inconclusivo: mantém a configuração atual.
- Piora após adoção: aplica o retorno autorizado e reavalia.
Resultado: decisão fundamentada, inclusive quando a melhor escolha é manter ou simplificar o que já existe.
