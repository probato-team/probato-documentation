# Procedure

A **Procedure** é a unidade responsável pela **execução da lógica de teste** no Probato.  
Ela contém o código que efetivamente interage com a aplicação, executa ações e realiza validações.

No modelo mental do Probato, a Procedure separa **descrição de cenário** (Script) de **execução**.

---

## Papel da Procedure no Probato

A Procedure é responsável por:

- executar a lógica do cenário
- interagir com Page Objects
- receber dados já resolvidos (Dataset)
- organizar pré-condições, execução e pós-condições

> A Procedure responde à pergunta: *Como o cenário é executado?*

---

## Onde a Procedure se encaixa no modelo mental

```
Suite
 └── Script
      ├── Precondition
      ├── Procedure
      │     └── Page Object
      └── Postcondition
```

A Procedure nunca existe isoladamente: ela sempre é executada no contexto de um Script.

---

## Formas de implementação

O Probato permite duas formas de implementação de Procedure.

### Procedure como método

Indicada para cenários simples e pontuais.

Características:
- implementação direta
- menor sobrecarga estrutural
- uso restrito a um Script

Essa abordagem é recomendada apenas quando:
- a lógica é pequena
- não há necessidade de reutilização

---

### Procedure como classe dedicada

Indicada para cenários reutilizáveis ou mais complexos.

Características:
- melhor organização
- maior reutilização
- isolamento de responsabilidades

Essa é a forma **recomendada** na maioria dos casos.

---

## Estrutura interna da Procedure

Uma Procedure pode ser dividida conceitualmente em três partes:

### Precondition
- preparação do cenário
- validações iniciais
- pré-requisitos funcionais

### Execution
- ações principais do fluxo
- interação com a aplicação
- execução do comportamento esperado

### Postcondition
- validações finais
- limpeza de estado, se necessário

Essa divisão melhora:
- legibilidade
- rastreabilidade
- diagnóstico de falhas

---

## Relação com Page Objects

A Procedure é o único nível que:

- conhece Page Objects
- interage diretamente com a UI
- coordena ações de interface

Page Objects **não devem conter lógica de cenário**.  
Toda decisão de fluxo pertence à Procedure.

---

## O que NÃO deve estar em uma Procedure

Para manter a arquitetura clara, uma Procedure **não deve**:

- conter definição de Dataset
- configurar browsers ou ambiente
- declarar estado global de banco
- conhecer detalhes de Suite ou Script

Essas responsabilidades pertencem a outros níveis do framework.

---

## Boas práticas

- Prefira Procedures como classes dedicadas
- Mantenha Procedures pequenas e focadas
- Evite lógica condicional baseada em dados
- Reutilize Procedures sempre que possível

---

## Próximo passo

Após compreender a Procedure, o próximo conceito é o **Page Object**, responsável por encapsular interações com a interface.

➡️ Continue em **Page Object**.
