# Dataset

O **Dataset** é o conceito responsável por definir os **dados de teste** utilizados durante a execução dos cenários no Probato.  
Ele permite que um mesmo Script seja executado múltiplas vezes com diferentes conjuntos de dados, de forma nativa e declarativa.

No modelo mental do Probato, o Dataset existe para separar **dados** de **lógica de execução**, evitando condicionais complexas e promovendo reutilização.

## Papel do Dataset no Probato

O Dataset é responsável por:

- fornecer dados externos para execução de Scripts
- habilitar execução *data-driven* automaticamente
- evitar lógica condicional baseada em dados
- manter o código de teste simples, legível e reutilizável

> O Dataset responde à pergunta: *Com quais dados o cenário será executado?*

## Onde o Dataset se encaixa no modelo mental

No fluxo conceitual do Probato, o Dataset está sempre associado a um Script.

``` title="Modelo conceitual" hl_lines="5"
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

O Dataset **nunca** é associado diretamente a uma Procedure ou Page Object.

## Características do Dataset

No Probato, um Dataset possui as seguintes características:

- externo ao código de teste
- fortemente tipado
- resolvido antes da execução da Procedure
- independente da lógica de teste

Cada entrada do Dataset gera uma **execução independente** do Script, garantindo isolamento e previsibilidade.

## Modelos de dados

Os dados definidos no Dataset são mapeados para **modelos de dados**.

Esses modelos:

- representam a estrutura do Dataset
- são injetados automaticamente na Procedure
- garantem segurança de tipos e clareza na execução

A Procedure recebe apenas o modelo de dados já resolvido, sem conhecer a origem ou o formato físico dos dados.

## Benefícios do uso de Dataset

O uso adequado de Dataset permite:

- maior cobertura de testes sem duplicação de código
- cenários mais simples e declarativos
- separação clara entre dados e comportamento
- facilidade de manutenção e evolução dos testes

## O que NÃO deve estar em um Dataset

Para manter a separação de responsabilidades, um Dataset **não deve**:

- conter lógica de execução
- definir regras de negócio
- alterar o estado da aplicação
- depender de contexto de execução

O Dataset deve ser apenas uma **fonte de dados**.

## Boas práticas

- Mantenha Datasets pequenos e objetivos
- Crie um Dataset por tipo de cenário
- Evite Datasets excessivamente genéricos
- Nomeie modelos de dados de forma clara e semântica

## Próximo passo

Após compreender o Dataset, o próximo conceito é o **Database**, responsável por definir o estado da aplicação antes da execução dos cenários.

➡️ Continue em **Database**.
