# Planejamento da startup Orbe

## Organização individual

Participante: Isabela Cruz Simões. Todas as tarefas são atribuídas à mesma participante, separadas por função. Essa adaptação não substitui automaticamente a exigência de grupo: se o professor exigir mais integrantes, a execução individual depende da aceitação dele.

| Função exercida | Responsabilidade |
| --- | --- |
| Produto | Definir público, problema, proposta e prioridades |
| Facilitação do processo | Organizar quadro, acompanhar impedimentos e limitar trabalho em andamento |
| Desenvolvimento | Revisar HTML, CSS e JavaScript; integrar alterações por branches |
| Qualidade e publicação | Validar funcionamento, publicar e registrar evidências |

Não há integrantes fictícios. São responsabilidades acumuladas por uma pessoa, não uma equipe Scrum formal.

## Sprint proposta — 3 dias de trabalho

Objetivo: publicar um site que explique a Orbe e permita experimentar um Kanban local.

- Dia 1: revisar proposta e backlog, criar quadro e integrar estrutura HTML.
- Dia 2: revisar apresentação e comportamento do Kanban; testar armazenamento e navegação.
- Dia 3: corrigir problemas, publicar, revisar resultado e registrar retrospectiva.

Adapte as datas ao seu prazo real. Não registre eventos como realizados antes de executá-los.

## Backlog

| ID | Tarefa | Prioridade | Critério de aceite | Branch | Responsável |
| --- | --- | --- | --- | --- | --- |
| ORB-01 | Definir proposta e plano | Alta | Público, problema, solução e backlog documentados | docs/planejamento | Isabela |
| ORB-02 | Estruturar o site | Alta | Seções da proposta, passos, demo e FAQ presentes; links internos válidos | feat/estrutura | Isabela |
| ORB-03 | Aplicar layout responsivo | Alta | Conteúdo legível em celular e computador, sem rolagem horizontal | feat/visual | Isabela |
| ORB-04 | Implementar Kanban local | Alta | Adicionar, mover, excluir e recarregar tarefas funciona | feat/kanban | Isabela |
| ORB-05 | Validar e corrigir | Alta | Checklist de validação preenchido com resultados reais | fix/revisao | Isabela |
| ORB-06 | Publicar no GitHub Pages | Alta | URL pública abre site com CSS, ícone e JavaScript | docs/entrega | Isabela |

## Kanban do desenvolvimento — GitHub Projects

Crie um projeto com visualização Board chamado “Orbe — Desenvolvimento”. Configure o campo Status com: A fazer, Em andamento, Em revisão e Concluído. Se o modelo inicial tiver nomes diferentes, renomeie ou adicione as opções.

Crie seis issues no repositório usando as tarefas acima. No corpo de cada issue, copie o critério de aceite e indique a branch. Atribua cada issue a belaSimoes e adicione ao projeto. Mova o cartão conforme o trabalho real.

Limite de trabalho em andamento: uma tarefa por vez. Em revisão significa que a implementação existe, mas ainda precisa passar pela conferência. Só conclua após atender o critério de aceite. Não mova tudo para concluído apenas porque recebeu os arquivos.

## Práticas de Scrum adaptadas

- Planejamento: selecionar o objetivo e as tarefas desta sprint.
- Acompanhamento diário individual: registrar o que fez, o próximo passo e impedimentos; não simular reunião de equipe.
- Revisão: demonstrar a versão, executar testes e comparar com os critérios de aceite.
- Retrospectiva: registrar o que funcionou, o que dificultou e uma melhoria para a próxima sprint.

### Registro diário — preencher após trabalhar

Data:
Concluído:
Próximo passo:
Impedimentos:

### Retrospectiva — preencher ao finalizar

O que funcionou:
O que dificultou:
O que mudaria na próxima sprint:

## Definition of Done

Uma tarefa está concluída quando a alteração foi revisada, validada, commitada na branch, integrada à main e atualizada no quadro. Para ORB-06, também é necessário abrir a URL pública e verificar a versão publicada.
