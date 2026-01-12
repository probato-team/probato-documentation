# Page Object

O **Page Object** é o componente responsável por encapsular a **interface do usuário** no Probato.  
Ele abstrai detalhes de UI e fornece métodos claros para interação com a aplicação.

No modelo mental do Probato, o Page Object é um **detalhe de implementação**, não um elemento de orquestração.

---

## Papel do Page Object no Probato

O Page Object é responsável por:

- encapsular elementos e ações da interface
- isolar mudanças de UI do restante do código
- fornecer uma API clara para interação
- enriquecer a execução com informações semânticas

> O Page Object responde à pergunta: *Como interagir com o sistema?*

---

## Onde o Page Object se encaixa no modelo mental

```
Suite
 └── Script
      └── Procedure
           └── Page Object
                ├── @Action
                └── @Param
```

O Page Object nunca é acessado diretamente por Scripts ou Suites.

---

## Page Object no Probato

O Probato segue o **padrão clássico de Page Object**, sem reinventá-lo.

Além disso, ele adiciona uma camada semântica por meio de anotações.

### @Action

A anotação `@Action` descreve semanticamente uma ação executada na interface.

Ela permite:

- logs mais claros
- relatórios compreensíveis
- melhor rastreabilidade de execução

A descrição da ação deve representar **o que está sendo feito**, não **como**.

---

### @Param

A anotação `@Param` identifica parâmetros relevantes utilizados em uma ação.

Ela permite:

- rastrear dados utilizados
- enriquecer métricas e evidências
- facilitar auditoria e diagnóstico

---

## Separação de responsabilidades

Para manter a arquitetura clara:

- Page Objects **não devem conter lógica de cenário**
- decisões de fluxo pertencem às Procedures
- dados são fornecidos externamente

O Page Object deve se limitar a:

- localizar elementos
- executar ações
- expor verificações simples

---

## O que NÃO deve estar em um Page Object

Um Page Object **não deve**:

- acessar banco de dados
- conter lógica condicional de cenário
- conhecer Dataset ou Script
- definir estado da aplicação

Essas responsabilidades pertencem a outros níveis do framework.

---

## Boas práticas

- Crie Page Objects pequenos e focados
- Um Page Object deve representar uma tela ou componente
- Evite Page Objects genéricos demais
- Prefira métodos descritivos e legíveis

---

## Próximo passo

Após compreender o Page Object, o próximo conceito é o **Dataset**, responsável por fornecer dados de execução.

➡️ Continue em **Dataset**.
