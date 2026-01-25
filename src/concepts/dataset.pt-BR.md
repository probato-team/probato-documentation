# Dataset

O **Dataset** é o conceito responsável por definir os **dados de teste** utilizados durante a execução dos cenários no Probato. Ele permite que um mesmo Script seja executado múltiplas vezes com diferentes conjuntos de dados, de forma nativa e declarativa.

No modelo mental do Probato, o Dataset existe para separar **dados** de **lógica de execução**, evitando condicionais complexas e promovendo reutilização.

## Papel do Dataset no Probato

O Dataset é responsável por:

- Fornecer dados externos para execução de Scripts
- Habilitar execução *data-driven* automaticamente
- Evitar lógica condicional baseada em dados
- Manter o código de teste simples, legível e reutilizável

> O Dataset responde à pergunta: *Com quais dados o cenário será executado?*

## Onde o Dataset se encaixa no modelo mental

No fluxo conceitual do Probato, o Dataset está sempre associado a um Script.

``` title="Modelo conceitual" hl_lines="5"
Suite
 ├── SQL (estado global / pré-condições da funcionalidade)
 ├── NoSQL (estado global / pré-condições da funcionalidade)
 └── Script
      ├── Dataset (dados de execução)
      ├── SQL (estado específico do cenário)
      ├── NoSQL (estado específico do cenário)
      ├── Precondition
      │     └── Page Object
      │           ├── Action
      │           └── Param
      ├── Procedure
      │     └── Page Object
      │           ├── Action
      │           └── Param
      └── Postcondition
            └── Page Object
                  ├── Action
                  └── Param
```

O Dataset **nunca** é associado diretamente a uma Procedure ou Page Object.

## Características do Dataset

No Probato, um Dataset possui as seguintes características:

- Externo ao código de teste
- Fortemente tipado
- Resolvido antes da execução da Procedure
- Independente da lógica de teste

Cada entrada do Dataset gera uma **execução independente** do Script, garantindo isolamento e previsibilidade.

## Modelos de dados

Os dados definidos no Dataset são mapeados para **modelos de dados**.

Esses modelos:

- Representam a estrutura do Dataset
- São injetados automaticamente na Procedure
- Garantem segurança de tipos e clareza na execução

A Procedure recebe apenas o modelo de dados já resolvido, sem conhecer a origem ou o formato físico dos dados.

## Benefícios do uso de Dataset

O uso adequado de Dataset permite:

- Maior cobertura de testes sem duplicação de código
- Cenários mais simples e declarativos
- Separação clara entre dados e comportamento
- Facilidade de manutenção e evolução dos testes

## O que NÃO deve estar em um Dataset

Para manter a separação de responsabilidades, um Dataset **não deve**:

- Conter lógica de execução
- Definir regras de negócio
- Alterar o estado da aplicação
- Depender de contexto de execução

O Dataset deve ser apenas uma **fonte de dados**.

## Boas práticas

- Mantenha Datasets pequenos e objetivos
- Crie um Dataset por tipo de cenário
- Evite Datasets excessivamente genéricos
- Nomeie modelos de dados de forma clara e semântica

## Próximo passo

Após compreender o Dataset, o próximo conceito é o **Database**, responsável por definir o estado da aplicação antes da execução dos cenários.

➡️ Continue em **Database**.
