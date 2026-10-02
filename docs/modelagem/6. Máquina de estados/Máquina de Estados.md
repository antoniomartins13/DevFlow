@startuml
hide empty description
skinparam shadowing false
top to bottom direction
title DevFlow — Estados da tarefa

state "Em especificação" as Especificacao
state "Em planejamento" as Planejamento
state "Aguardando aprovação\nPlano e base — CP1" as Aprovacao
state "Pronta para execução" as Pronta
state "Em desenvolvimento" as Desenvolvimento
state "Em verificação" as Verificacao
state "Em revisão independente" as Revisao
state "Em correção" as Correcao
state "Aguardando validação humana" as Validacao
state "Pronta para decisão de merge" as ProntaMerge
state "Concluída" as Concluida
state "Encerrada sem entrega" as Encerrada

[*] --> Especificacao : demanda registrada

Especificacao --> Planejamento : especificação finalizada\n[critérios aprovados quando exigidos]
Planejamento --> Aprovacao : plano e base apresentados

Aprovacao --> Planejamento : ajustes solicitados
Aprovacao --> Encerrada : plano rejeitado
Aprovacao --> Pronta : CP1 aprovado\n[autorização válida]

Pronta --> Desenvolvimento : execução admitida\n[dependências e limites atendidos]
Desenvolvimento --> Verificacao : implementação finalizada

Verificacao --> Revisao : verificações aprovadas\n[evidências válidas para o commit]
Verificacao --> Correcao : teste falhou ou diff fora do escopo

Revisao --> Correcao : achados exigem correção
Correcao --> Verificacao : correção finalizada\n[dentro do plano autorizado]

Revisao --> Validacao : revisão concluída\n[sem bloqueantes, roteiro revisado e ambiente pronto]

Validacao --> Correcao : falha ou regressão confirmada
Validacao --> ProntaMerge : validação aprovada\n[decisão válida para a versão]

ProntaMerge --> Concluida : merge realizado por humano\n[revisão humana aprovada, CI verde e gates válidos]

Concluida --> [*]
Encerrada --> [*]

legend bottom
  Setas: evento [condição necessária].
  Ausência de resposta não significa aprovação.
  Correções passam novamente por testes e revisão.
endlegend
@enduml
