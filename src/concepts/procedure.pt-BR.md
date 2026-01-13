# Procedure

A **Procedure** é a unidade responsável pela **execução da lógica de teste** no Probato.  
Ela contém o código que efetivamente interage com a aplicação, executa ações e realiza validações.

No modelo mental do Probato, a Procedure existe para separar claramente a **descrição do cenário** (Script) da **execução do comportamento**.

Enquanto o Script descreve *o que deve acontecer*, a Procedure define *como isso acontece*.

## Papel da Procedure no Probato

A Procedure é responsável por:

- executar a lógica do cenário
- interagir com Page Objects
- receber dados já resolvidos (Dataset)
- coordenar pré-condições, execução e pós-condições

> A Procedure responde à pergunta: *Como o cenário é executado?*

Ela é o nível onde a intenção declarada no Script se transforma em comportamento executável.

## Onde a Procedure se encaixa no modelo mental

No fluxo conceitual do Probato, a Procedure está sempre contida em um Script e nunca existe de forma isolada.

``` title="Modelo conceitual" hl_lines="8 12 16"
@Suite
 ├── @SQL (estado global / pré-condições da funcionalidade)
 ├── @NoSQL (estado global / pré-condições da funcionalidade)
 └── @Script
      ├── @Dataset (dados de execução)
      ├── @SQL (estado específico do cenário)
      ├── @NoSQL (estado específico do cenário)
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

A Procedure é sempre executada no contexto de um Script, utilizando dados e estado previamente definidos.

## Formas de implementação

O Probato permite duas formas de implementação de Procedure, dependendo da complexidade e da necessidade de reutilização.

### Procedure como método

Indicada para cenários simples e pontuais.

Características:

- implementação direta
- menor sobrecarga estrutural
- escopo limitado a um único Script

Essa abordagem é recomendada apenas quando:

- a lógica é pequena
- não há necessidade de reutilização
- o fluxo é simples e específico

### Procedure como classe dedicada

Indicada para cenários reutilizáveis ou mais complexos.

Características:

- melhor organização do código
- maior reutilização entre Scripts
- isolamento claro de responsabilidades

Essa é a forma **recomendada** na maioria dos casos, especialmente em projetos de médio e grande porte.

## Estrutura interna da Procedure

Conceitualmente, uma Procedure pode ser organizada em três partes distintas:

### Precondition

- preparação do cenário
- validações iniciais
- garantia de pré-requisitos funcionais

### Execution

- ações principais do fluxo
- interação com a aplicação
- execução do comportamento esperado

### Postcondition

- validações finais
- limpeza ou restauração de estado, quando necessário

Essa divisão melhora:

- legibilidade do código
- rastreabilidade da execução
- diagnóstico preciso de falhas

## Relação com Page Objects

A Procedure é o único nível que:

- conhece Page Objects
- interage diretamente com a interface do usuário
- coordena ações de UI como parte do fluxo

Page Objects **não devem conter lógica de cenário**.  
Toda decisão de fluxo e validação pertence à Procedure.

## O que NÃO deve estar em uma Procedure

Para manter a arquitetura clara e previsível, uma Procedure **não deve**:

- conter definição de Dataset
- configurar browsers ou ambiente
- declarar estado global de banco
- conhecer detalhes de Suite ou Script

Essas responsabilidades pertencem a outros níveis do framework.

## Boas práticas

- Prefira Procedures implementadas como classes dedicadas
- Mantenha Procedures pequenas, coesas e focadas
- Evite lógica condicional baseada em dados
- Reutilize Procedures sempre que possível

## Próximo passo

Após compreender a Procedure, o próximo conceito é o **Page Object**, responsável por encapsular interações com a interface.

➡️ Continue em **Page Object**.
