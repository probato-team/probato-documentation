# Page Object

O **Page Object** é o componente responsável por encapsular a **interface do usuário** no Probato.  
Ele abstrai detalhes de UI e fornece métodos claros para interação com a aplicação.

No modelo mental do Probato, o Page Object é um **detalhe de implementação**, não um elemento de orquestração ou decisão de fluxo.

Seu objetivo é isolar a interface do restante do código de teste, tornando os testes mais legíveis, reutilizáveis e resilientes a mudanças de UI.

## Papel do Page Object no Probato

O Page Object é responsável por:

- encapsular elementos e ações da interface do usuário
- isolar mudanças de UI do restante do código
- fornecer uma API clara e expressiva para interação
- enriquecer a execução com informações semânticas

> O Page Object responde à pergunta: *Como interagir com o sistema?*

Ele não sabe **por que** uma ação é executada, apenas **como executá-la**.

## Onde o Page Object se encaixa no modelo mental

No fluxo conceitual do Probato, o Page Object é sempre utilizado por Procedures e nunca acessado diretamente por Scripts ou Suites.

``` title="Conceptual model" hl_lines="9-11 13-15 17-19"
@Suite
 ├── @SQL (global state / feature preconditions)
 ├── @NoSQL (global state / feature preconditions)
 └── @Script
      ├── @Dataset (execution data)
      ├── @SQL (scenario-specific state)
      ├── @NoSQL (scenario-specific state)
      ├── @Precondition
      │     └── Page Object
      │           ├── @Action
      │           └── @Param
      ├── @Procedure
      │     └── Page Object
      │           ├── @Action
      │           └── @Param
      └── @Postcondition
            └── Page Object
                  ├── @Action
                  └── @Param
```

Essa restrição garante que decisões de fluxo permaneçam fora da camada de interface.

## Page Object no Probato

O Probato adota o **padrão clássico de Page Object**, sem reinventá-lo ou criar abstrações artificiais.

Sobre esse padrão consolidado, o framework adiciona uma **camada semântica**, enriquecendo a execução por meio de anotações.

### @Action

A anotação `@Action` descreve semanticamente uma ação executada na interface.

Ela permite:

- geração de logs mais claros
- relatórios mais compreensíveis
- melhor rastreabilidade da execução

A descrição da ação deve representar **o que está sendo feito**, e não **como a ação é implementada**.

### @Param

A anotação `@Param` identifica parâmetros relevantes utilizados em uma ação.

Ela permite:

- rastrear dados utilizados durante a execução
- enriquecer métricas e evidências
- facilitar auditoria e diagnóstico de falhas

Essas anotações não alteram o comportamento do código, mas ampliam significativamente sua observabilidade.

## Separação de responsabilidades

Para manter a arquitetura clara e previsível:

- Page Objects **não devem conter lógica de cenário**
- decisões de fluxo pertencem às Procedures
- dados são fornecidos externamente (Dataset)
- estado da aplicação é tratado fora da camada de UI

O Page Object deve se limitar a:

- localizar elementos
- executar ações
- expor verificações simples e diretas

## O que NÃO deve estar em um Page Object

Um Page Object **não deve**:

- acessar banco de dados
- conter lógica condicional baseada em cenário
- conhecer Dataset, Script ou Suite
- definir ou manipular estado global da aplicação

Essas responsabilidades pertencem a outros níveis do framework.

## Boas práticas

- Crie Page Objects pequenos e coesos
- Um Page Object deve representar uma tela ou componente específico
- Evite Page Objects genéricos demais
- Prefira métodos descritivos e legíveis
- Nomeie ações de acordo com o comportamento percebido pelo usuário

## Próximo passo

Após compreender o Page Object, o próximo conceito é o **Dataset**, responsável por fornecer dados de execução aos cenários.

➡️ Continue em **Dataset**.
