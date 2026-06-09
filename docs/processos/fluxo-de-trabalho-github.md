# Fluxo de trabalho com GitHub

Este documento define o padrão da YA LABS para organizar trabalho usando GitHub Issues, GitHub Projects, branches, commits, Pull Requests e releases.

O objetivo é manter tarefas, código, revisão, documentação e histórico conectados dentro do GitHub.

## Conceito principal

- Issue: tarefa, bug, melhoria, documentação ou investigação.
- Project: quadro visual onde as issues são organizadas.
- Branch: ramificação criada para desenvolver uma issue específica.
- Commit: registro pequeno e claro de uma alteração.
- Pull Request: solicitação para revisar e integrar uma branch.
- Release: publicação de uma versão validada.

## GitHub Projects

O GitHub Project deve funcionar como o quadro oficial de acompanhamento do projeto.

Colunas recomendadas:

```text
Backlog
Pendente
Em andamento
Bloqueado
Validação
Concluído
Ideias futuras
```

Uso recomendado:

- `Backlog`: tarefas mapeadas, mas ainda não priorizadas.
- `Pendente`: tarefas priorizadas e prontas para começar.
- `Em andamento`: tarefa sendo desenvolvida em branch própria.
- `Bloqueado`: tarefa que depende de outra entrega ou decisão.
- `Validação`: tarefa implementada e aguardando revisão, teste ou aprovação.
- `Concluído`: tarefa finalizada, revisada e integrada.
- `Ideias futuras`: sugestões que ainda não entraram no planejamento.

## Labels

Cada projeto pode adaptar as labels conforme sua stack, mas a YA LABS deve manter uma taxonomia simples.

Labels de tipo recomendadas:

```text
bug
documentation
feature
refactor
tooling
```

Labels de área recomendadas:

```text
frontend
backend
docs
infra
ui/ux
```

Evite criar labels diferentes para a mesma intenção. Por exemplo, não use `fix` como label se `bug` já representa correção de comportamento incorreto.

## Padrão de issues

Cada tarefa relevante deve virar uma issue separada.

Quando uma funcionalidade exigir front-end e back-end, crie issues separadas para cada parte, salvo quando a alteração for pequena e inevitavelmente conjunta.

Exemplo:

- Backend: criar endpoint de autenticação.
- Frontend: criar tela de login consumindo a API.

### Template de issue

Use a estrutura abaixo como padrão:

```md
## Descrição

Descreva de forma objetiva o que deve ser implementado, corrigido ou documentado.

Explique o contexto da tarefa e o resultado esperado.

## Escopo

- Item principal que precisa ser feito.
- Integração, regra, tela, processo ou documento envolvido.
- Tratamento de erro, estado vazio ou caso especial relevante.
- Ajuste visual, técnico ou documental necessário.

## Critérios de aceite

- O comportamento esperado deve estar funcionando.
- Os principais cenários da tarefa devem estar cobertos.
- Erros ou estados vazios devem ter tratamento claro, quando aplicável.
- A implementação deve respeitar o padrão do projeto.

## Dependências

- Depende da issue #numero.
```

A seção `Dependências` só deve ser usada quando existir bloqueio por outra issue.

## Dependência entre issues

Quando uma issue depender de outra, informe isso na descrição.

Exemplo:

```md
## Dependências

- Depende da issue #12.
```

Enquanto a dependência não for concluída, a issue dependente deve ficar em `Bloqueado`.

## Padrão de branches

Cada issue deve ter sua própria branch.

Padrão geral:

```text
area/tipoNumero-descricao-curta
```

Para documentação, não repita `docs/docs`. Use:

```text
docsNumero-descricao-curta
```

Exemplos:

```text
back/feat006-cria-endpoint-login
front/feat007-cria-tela-login
front/fix028-corrige-validacao-formulario
docs031-documenta-fluxo-github
```

Áreas comuns:

```text
front
back
docs
infra
```

Tipos comuns:

```text
feat
fix
refactor
chore
docs
```

Regras:

- Use o número da issue na branch.
- Use descrição curta em kebab-case.
- Não use acentos, espaços ou caracteres especiais.
- Não trabalhe em duas issues diferentes na mesma branch.
- Não misture front-end e back-end na mesma branch sem necessidade real.

## Branches de lote documental

Para documentação, alterações pequenas e relacionadas podem ser agrupadas em uma única issue, branch e Pull Request quando fizerem parte do mesmo objetivo.

Esse fluxo serve para reduzir cerimônia operacional em trabalhos documentais como planejamento inicial, mapa do problema, matriz de alternativas, escopo inicial, riscos, decisões e próximos passos.

Use branch individual quando:

- a documentação tiver objetivo próprio e independente;
- a alteração for crítica, extensa ou de maior impacto;
- o documento precisar de revisão, validação ou aprovação separada;
- o tema não fizer parte do mesmo planejamento ou contexto.

Use branch de lote documental quando:

- os documentos forem pequenos e relacionados;
- todos fizerem parte da mesma intenção de trabalho;
- a revisão puder acontecer no mesmo Pull Request;
- a issue principal tiver escopo fechado e critérios de aceite claros.

A branch de lote deve ter começo, fim e objetivo claro. Ela não deve virar uma branch fixa permanente de documentação.

Exemplo de branch:

```text
docs042-planejamento-inicial-yahub
```

Para organizar o lote, use uma issue principal com checklist quando os documentos forem simples e tiverem baixo acoplamento decisório.

Exemplo:

```md
- [ ] Mapa do problema
- [ ] Matriz de alternativas
- [ ] Escopo inicial
- [ ] Riscos e decisões
- [ ] Próximos passos
```

Use subissues quando houver entregas documentais relacionadas, mas com dependências, responsáveis, validações ou discussões próprias.

Mesmo em lote documental, preserve a rastreabilidade:

```text
Issue principal -> Branch de lote -> Commit -> Pull Request -> Merge -> Validação
```

## Padrão de commits

As mensagens de commit devem seguir o formato:

```text
area/tipo: descrição curta
```

Exemplos:

```text
front/feat: adiciona tela de login
back/fix: corrige retorno de autenticação inválida
infra/chore: ajusta workflow de deploy
docs: documenta fluxo de trabalho com GitHub
```

Regras:

- A área deve indicar onde a alteração principal aconteceu.
- O tipo deve indicar a natureza da mudança.
- Para alterações apenas de documentação, use `docs: descrição curta`.
- A descrição deve ser curta, clara e em português.
- Use letras minúsculas no prefixo.
- Evite mensagens genéricas como `ajustes`, `teste`, `alterações` ou `update`.

## Fluxo de desenvolvimento

1. Criar ou identificar a issue.
2. Adicionar a issue ao GitHub Project.
3. Classificar com labels de área e tipo.
4. Criar branch própria a partir da issue.
5. Desenvolver apenas o escopo da issue na branch.
6. Fazer commits seguindo o padrão do projeto.
7. Abrir Pull Request.
8. Vincular o PR à issue usando `Closes #numero`.
9. Mover a issue para `Validação`.
10. Revisar e testar.
11. Fazer merge na branch de desenvolvimento do projeto.
12. Validar a integração.
13. Preparar release quando houver versão pronta para publicação.

## Padrão de Pull Requests

O Pull Request deve explicar o que foi feito e deixar claro o impacto da alteração.

Título recomendado:

```text
Tipo: descrição curta da tarefa ISSUE #XX (PR #YY)
```

Exemplos:

```text
Feature: adiciona autenticação por e-mail ISSUE #6 (PR #33)
Fix: corrige validação do formulário de login ISSUE #36 (PR #37)
Docs: atualiza fluxo de trabalho com GitHub ISSUE #40 (PR #41)
```

O trecho `ISSUE #XX (PR #YY)` facilita a rastreabilidade na lista de Pull Requests.

Como o número do PR só existe depois da criação do Pull Request, crie o PR primeiro com a issue no título e edite o título em seguida para adicionar `(PR #YY)`.

Mesmo com a issue no título, mantenha `Closes #numero` no corpo do PR. É essa referência que garante o fechamento automático da issue quando o PR for mergeado.

### Template de Pull Request

Use a estrutura abaixo:

```md
## Contexto

Explique o objetivo do PR e qual problema ele resolve.

Closes #numero

## O que mudou

- Alteração principal feita no projeto.
- Serviço, componente, tela, endpoint ou documentação criada.
- Regra de negócio, tratamento ou integração ajustada.

## Contrato do endpoint

Use esta seção quando o PR alterar ou criar contrato de API.

Endpoint:

GET /rota/exemplo

Response:

{
  "id": "123",
  "name": "Exemplo"
}

## Observações

- Pontos importantes para revisão.
- Limitações conhecidas.
- Testes feitos.
- Warnings existentes que não foram causados pelo PR.
```

Se o PR não alterar API, remova a seção `Contrato do endpoint`.

## Integração entre front-end e back-end

Quando o back-end criar ou alterar uma API, o contrato deve ser documentado na issue, no Pull Request ou na pasta `docs` do projeto.

O contrato deve informar pelo menos:

- endpoint;
- método HTTP;
- parâmetros principais;
- exemplo de response;
- estados de sucesso, erro e vazio, quando existirem.

O front-end pode começar com mock enquanto o back-end ainda não terminou.

Depois que o back-end finalizar, o front-end deve trocar o mock pela API real.

## Fluxo de release

Quando a branch de desenvolvimento estiver validada e pronta para virar uma versão publicada, prepare a release em uma branch própria criada a partir da branch principal.

Padrão:

```text
release/x.y.z
```

Exemplos:

```text
release/1.0.0
release/1.1.0
release/1.1.1
```

Passo a passo recomendado:

1. Garantir que a branch de desenvolvimento foi validada.
2. Atualizar a branch principal local com a versão remota.
3. Criar `release/x.y.z` a partir da branch principal.
4. Fazer merge da branch de desenvolvimento na branch de release.
5. Resolver conflitos, se existirem.
6. Rodar as validações necessárias do projeto.
7. Abrir Pull Request de `release/x.y.z` para a branch principal.
8. Revisar o PR e confirmar que ele contém apenas o conteúdo esperado da release.
9. Fazer merge da branch de release na branch principal.
10. Atualizar a branch principal local.
11. Criar a tag da versão a partir da branch principal.
12. Publicar a tag no GitHub.
13. Sincronizar a branch de desenvolvimento com a branch principal, quando necessário.

## PR de release

Título recomendado:

```text
Release: publica versão x.y.z
```

Descrição recomendada:

```md
## Contexto

Publica a versão x.y.z da aplicação.

Esta release consolida as alterações validadas na branch `release/x.y.z`.

## O que mudou

- Lista resumida das principais entregas técnicas.
- Lista resumida das principais correções.
- Ajustes de documentação ou fluxo, quando existirem.

## PRs e commits incluídos

- #numero área/tipo: descrição curta
- área/tipo: descrição curta

## Validações

- Front-end lint executado
- Front-end build executado
- Back-end build executado

## Observações

- A tag `vx.y.z` deve ser criada somente depois do merge na branch principal.
```

## Tags

A tag da versão deve ser criada somente depois que a release estiver integrada na branch principal.

Não crie tag diretamente na branch de desenvolvimento, porque a tag precisa apontar para o commit que realmente representa a versão publicada.

Não mova uma tag já publicada sem alinhamento explícito do time. Mover tag exige reescrever referência publicada e pode confundir quem já baixou a versão anterior.

## Orientação da IA

Quando a IA for usada para implementar, revisar ou documentar algo, ela deve reforçar:

- criação ou identificação da issue relacionada;
- uso de branch própria para cada issue;
- uso de branch de lote documental quando uma issue principal agrupar documentos pequenos e relacionados;
- separação entre tarefas de front-end, back-end, infraestrutura e documentação;
- commits no padrão do projeto;
- Pull Requests com contexto, mudanças, observações e vínculo com a issue;
- documentação de contratos de API quando houver integração entre front-end e back-end.

Ao classificar uma demanda documental, a IA deve identificar se a solicitação é uma alteração isolada ou um lote documental.

Quando os documentos forem pequenos e fizerem parte do mesmo objetivo, a IA deve sugerir agrupamento em issue principal com checklist ou subissues, evitando criar uma branch por documento sem necessidade.

Quando os temas forem independentes, críticos ou de maior impacto, a IA deve manter issues, branches e Pull Requests separados.

Antes de alterar arquivos, a IA deve validar:

- branch atual;
- tipo da alteração solicitada;
- área afetada;
- issue relacionada, quando aplicável;
- compatibilidade com o fluxo documentado;
- risco de mexer em branch principal, branch de desenvolvimento, branch de release ou branch incompatível.

Se a solicitação estiver fora do fluxo documentado, a IA deve avisar o usuário e pedir confirmação explícita ou registrar a exceção autorizada.

## Regra principal

Não trabalhe duas issues diferentes na mesma branch.

Cada issue deve ter sua própria branch. Em documentação, uma issue principal pode usar branch de lote quando agrupar documentos pequenos e relacionados dentro de um objetivo claro.

Esse fluxo mantém o histórico limpo, facilita revisão, reduz conflitos e deixa claro o caminho:

```text
Issue -> Branch -> Commit -> Pull Request -> Merge -> Validação -> Release
```
