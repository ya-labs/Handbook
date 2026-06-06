# Uso de IA

Este guia define como a YA LABS usa assistentes de IA em tarefas de desenvolvimento, documentação e organização de projetos.

IA deve acelerar o trabalho sem quebrar rastreabilidade, contexto ou responsabilidade técnica.

## Princípios

- A IA deve consultar o repositório antes de assumir arquitetura, stack ou padrão.
- Mudanças relevantes devem ter issue, branch, commit e Pull Request.
- A IA deve respeitar o padrão local do projeto.
- Código gerado deve ser legível, simples e pronto para manutenção.
- Documentação gerada deve preservar fatos reais do projeto.
- O time continua responsável por revisar, validar e aprovar mudanças.

## Quando usar IA

Use IA para:

- escrever ou revisar documentação;
- preparar descrição de issues;
- preparar descrição de PRs;
- investigar bugs;
- explicar código existente;
- sugerir refatorações pequenas;
- gerar base inicial de arquivos repetitivos;
- revisar clareza, riscos e critérios de aceite.

## Quando ter cuidado

Tenha cuidado quando a tarefa envolver:

- alterações grandes de arquitetura;
- contratos de API ainda não definidos;
- dados sensíveis;
- regras de negócio críticas;
- mudanças em branch protegida;
- migrações, deploy ou comandos destrutivos.

Nesses casos, a IA deve ajudar a planejar e validar, mas a decisão precisa ser explícita do time.

## Padrão esperado de resposta

Em contexto de projeto, a IA deve:

- responder em português do Brasil;
- ser direta e prática;
- explicar rapidamente o motivo técnico das decisões;
- evitar resposta genérica;
- entregar código completo quando a tarefa pedir implementação;
- sugerir mensagem de commit ao alterar arquivos;
- informar validações feitas e limitações conhecidas.

## Rastreabilidade

Toda mudança relevante deve se conectar ao fluxo:

```text
Issue -> Branch -> Commit -> Pull Request -> Merge -> Validação
```

Se a IA identificar que não existe issue ou que a branch atual não combina com a mudança, deve avisar antes de editar ou registrar a exceção quando o usuário pedir para prosseguir.

## Limite saudável

IA não substitui revisão técnica.

O uso correto é tratar a IA como uma parceira de execução e análise, não como fonte automática de verdade.

