# Conceitos

Esta seção apresenta os **conceitos fundamentais do Probato**.  
Antes de aprender *como usar* o framework, é essencial entender **como ele pensa**.

O Probato não é um framework genérico. Ele é **opinativo e declarativo**, o que significa que impõe uma estrutura clara para organização e execução de testes automatizados, reduzindo ambiguidades, acoplamento excessivo e variações entre projetos.

Compreender esses conceitos é essencial para utilizar o framework corretamente e aproveitar todo o seu potencial.

## O princípio central do Probato

O Probato é construído sobre um princípio simples e intencional:

> **O código descreve o que deve ser testado.  
> O framework decide como executar.**

Esse princípio orienta todas as decisões arquiteturais do Probato e se materializa em:

- uso extensivo de anotações declarativas
- separação rigorosa de responsabilidades
- configuração centralizada fora do código
- orquestração automática do ciclo de execução

O objetivo é permitir que o autor do teste foque **na intenção do teste**, enquanto o framework cuida da execução, instrumentação e observabilidade.

## Modelo mental do framework

O Probato organiza testes automatizados em **camadas bem definidas**, cada uma com uma responsabilidade clara e não sobreposta.

O fluxo conceitual completo é o seguinte:

``` title="Modelo conceitual"
@Suite
 ├── @SQL (estado global / pré-condições da funcionalidade)
 ├── @NoSQL (estado global / pré-condições da funcionalidade)
 └── @Script
      ├── @Dataset (dados de execução)
      ├── @SQL (estado específico do cenário)
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

Esse modelo define **como os testes devem ser pensados**, não apenas como são escritos.  
Cada camada possui um papel específico e nenhuma delas deve assumir responsabilidades de outra.

## Visão geral dos conceitos estruturais

Os conceitos abaixo formam o **núcleo estrutural do Probato**.  
Eles definem o vocabulário e o modelo mental adotado pelo framework.

### Suite

A **Suite** representa uma **funcionalidade ou caso de uso** do sistema.

Ela é responsável por:

- agrupar Scripts relacionados
- definir pré-condições globais (por exemplo, estado de banco de dados)
- servir como ponto de descoberta para o JUnit 5

A Suite responde à pergunta:

> *O que está sendo validado?*

### Script

O **Script** representa um **cenário de teste**.

Ele é puramente declarativo e não contém lógica de negócio.  
Sua função é descrever:

- quais dados serão utilizados
- quais procedures serão executadas
- quais pré e pós-condições se aplicam ao cenário

O Script responde à pergunta:

> *Qual cenário será executado?*

### Procedure

A **Procedure** é onde a **lógica executável** vive.

Ela pode ser implementada como:

- um método simples
- ou uma classe dedicada, quando há necessidade de reutilização e organização

A Procedure:

- recebe dados já resolvidos
- executa ações
- delega interações de UI aos Page Objects

Ela responde à pergunta:

> *Como o cenário é executado?*

### Page Object

O **Page Object** encapsula interações com a interface do usuário.

No Probato:

- ele segue o padrão clássico de Page Object
- não conhece Script nem Suite
- é enriquecido semanticamente por meio de anotações

Anotações como `@Action` e `@Param` permitem:

- rastreabilidade
- geração de logs e relatórios mais ricos
- melhor observabilidade da execução

O Page Object responde à pergunta:

> *Como interagir com o sistema?*

### Dataset

O **Dataset** define os **dados de teste** utilizados na execução.

Ele é:

- externo ao código
- declarado no Script
- responsável por habilitar execução *data-driven* de forma nativa

Cada entrada de Dataset pode gerar uma execução independente do mesmo Script.

O Dataset responde à pergunta:

> *Com quais dados o cenário será executado?*

### Database

O conceito de **Database** no Probato representa o **estado da aplicação**.

Scripts SQL podem ser executados:

- no nível da Suite (estado global)
- no nível do Script (estado específico do cenário)

Essa abordagem garante que:

- estado não fique misturado com lógica
- testes sejam mais previsíveis e reprodutíveis

O Database responde à pergunta:

> *Em qual estado o sistema deve estar antes da execução?*

## Conceitos transversais

Além dos conceitos estruturais, o Probato utiliza componentes que atuam de forma **transversal** durante a execução.

### Configuração e execução

O framework utiliza **configuração centralizada** para definir aspectos como:

- browsers
- execução paralela
- timeouts
- captura de evidências
- integração com o Probato Manager

Essas definições ficam fora do código, normalmente em arquivos YAML, reforçando a separação entre **intenção do teste** e **ambiente de execução**.

### Probato Manager

O **Probato Manager** é o componente responsável por consumir os dados gerados durante a execução dos testes.

Ele fornece:

- métricas
- relatórios
- histórico de execuções
- visibilidade para stakeholders não técnicos

O Manager não executa testes — ele **observa, consolida e apresenta resultados**.

## Como navegar a partir daqui

A partir deste ponto, recomenda-se a seguinte ordem de leitura:

1. **Suite**
2. **Script**
3. **Procedure**
4. **Page Object**
5. **Dataset**
6. **Database**

Essa sequência segue exatamente o modelo mental do framework.

## Considerações finais

O Probato não busca ser genérico ou neutro.  
Ele foi projetado para impor **estrutura, previsibilidade e clareza** em projetos de automação de testes.

Compreender esses conceitos é essencial antes de avançar para documentação prática e guias de uso.
