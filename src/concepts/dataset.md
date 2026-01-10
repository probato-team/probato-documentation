# Dataset

O **Dataset** é o conceito responsável por definir os **dados de teste** utilizados durante a execução dos cenários no Probato.  
Ele permite que um mesmo Script seja executado múltiplas vezes com diferentes conjuntos de dados, de forma nativa e declarativa.

No modelo mental do Probato, o Dataset separa **dados** de **lógica de execução**.

---

## Papel do Dataset no Probato

O Dataset é responsável por:

- fornecer dados externos para execução de Scripts
- habilitar execução *data-driven* automaticamente
- evitar lógica condicional baseada em dados
- manter o código de teste simples e reutilizável

> O Dataset responde à pergunta: *Com quais dados o cenário será executado?*

---

## Onde o Dataset se encaixa no modelo mental

```
Suite
 └── Script
      ├── @Dataset
      └── Procedure(model)
```

O Dataset é sempre associado a um **Script**, nunca diretamente a uma Procedure.

---

## Características do Dataset

O Dataset no Probato é:

- externo ao código
- fortemente tipado
- resolvido antes da execução da Procedure
- independente da lógica de teste

Cada entrada de Dataset gera uma execução independente do Script.

---

## Modelos de dados

Os dados do Dataset são mapeados para **modelos de dados**.

Esses modelos:
- representam a estrutura do Dataset
- são injetados automaticamente na Procedure
- garantem segurança e clareza na execução

A Procedure recebe apenas o modelo já resolvido, sem conhecer a origem dos dados.

---

## Benefícios do uso de Dataset

O uso de Dataset permite:

- maior cobertura de testes
- redução de duplicação de código
- cenários mais simples e legíveis
- separação clara entre dados e comportamento

---

## O que NÃO deve estar em um Dataset

Para manter a separação de responsabilidades, um Dataset **não deve**:

- conter lógica de execução
- definir regras de negócio
- alterar estado da aplicação
- depender de contexto de execução

O Dataset deve ser apenas uma **fonte de dados**.

---

## Boas práticas

- Mantenha Datasets pequenos e objetivos
- Crie um Dataset por tipo de cenário
- Evite Datasets excessivamente genéricos
- Nomeie modelos de dados de forma clara

---

## Próximo passo

Após compreender o Dataset, o próximo conceito é o **Database**, responsável por definir o estado da aplicação antes da execução.

➡️ Continue em **Database**.
