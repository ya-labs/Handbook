# Documentação técnica

Este guia define como a YA LABS organiza documentação técnica nos projetos.

O objetivo é manter documentos úteis para desenvolvimento real, sem transformar a documentação em burocracia difícil de manter.

## Princípios

- Documente decisões e contratos que ajudam outra pessoa a continuar o trabalho.
- Escreva em português claro, com acentos e UTF-8.
- Use Markdown simples.
- Prefira exemplos reais do projeto.
- Não invente arquitetura, endpoint ou fluxo que ainda não existe.
- Atualize a documentação quando uma mudança alterar comportamento, contrato ou processo.

## O que documentar no projeto

Cada projeto deve manter sua própria documentação específica.

Exemplos:

- visão geral do produto;
- stack;
- arquitetura real;
- contratos de API;
- variáveis de ambiente;
- setup local;
- deploy;
- integrações;
- decisões técnicas importantes.

## Estrutura recomendada

```text
docs/
|-- README.md
|-- planejamento-inicial/
|-- tecnico/
|   |-- arquitetura/
|   |-- api/
|   `-- infraestrutura/
`-- processo/
```

Essa estrutura pode ser adaptada conforme o tamanho do projeto.

Projetos pequenos não precisam criar pastas vazias sem uso imediato.

## Contratos de API

Quando documentar uma API, inclua:

- método HTTP;
- rota;
- parâmetros;
- exemplo de request, quando existir;
- exemplo de response;
- estados de sucesso;
- estados de erro;
- estados vazios esperados.

Exemplo:

````md
## Buscar perfil

GET /users/{id}

### Parâmetros

- `id`: identificador do usuário.

### Response de sucesso

```json
{
  "id": "123",
  "name": "Nícolas"
}
```

### Estados tratados

- `200`: usuário encontrado.
- `404`: usuário não encontrado.
````

## Decisões técnicas

Registre decisões quando elas ajudarem o time a entender por que uma solução foi escolhida.

Uma decisão técnica deve responder:

- qual problema estava sendo resolvido;
- quais opções foram consideradas;
- qual decisão foi tomada;
- quais impactos ou limitações existem.

## Regra prática

Documentação boa é aquela que reduz dúvida na hora de implementar, revisar, testar ou dar manutenção.

Se o documento não ajuda ninguém a tomar decisão ou executar trabalho real, simplifique.
