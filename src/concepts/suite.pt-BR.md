# Suite

A **Suite** é o ponto de entrada conceitual e estrutural do Probato. Ela representa uma **funcionalidade**, **caso de uso** ou **fluxo de negócio** que será validado por meio de um conjunto de cenários de teste. No modelo mental do Probato, a Suite ocupa o **nível mais alto da hierarquia**, sendo responsável por definir *o contexto* no qual os testes serão executados.

A Suite não descreve passos de teste nem lógica de execução. Ela define **a intenção de validação**.

## Papel da Suite no Probato

A Suite é responsável por:

- Agrupar Scripts relacionados a uma mesma funcionalidade
- Definir pré-condições globais para os cenários
- Servir como ponto de descoberta para o JUnit 5
- Orquestrar a execução de múltiplos Scripts

Ela **não contém lógica de execução de teste**.

> A Suite descreve *o que será validado*, não *como validar*.

## Onde a Suite se encaixa no modelo mental

No fluxo conceitual do Probato, a Suite encapsula todos os elementos necessários para validar uma funcionalidade completa.

``` title="Modelo conceitual" hl_lines="1"
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

Tudo que pertence à Suite deve ser **comum a todos os cenários** (Scripts) que ela agrupa. Se algo varia entre cenários, não pertence à Suite.

## Responsabilidades da Suite

### Organização semântica

A Suite fornece uma **organização semântica** dos testes, alinhada à visão de negócio do sistema.

Exemplos de Suites:

- Autenticação de Usuário
- Cadastro de Cliente
- Fluxo de Compra
- Recuperação de Senha

Cada Suite representa uma **intenção clara de validação**, facilmente compreensível por desenvolvedores, QAs e stakeholders técnicos.

### Agrupamento de Scripts

Uma Suite pode conter **um ou vários Scripts**, cada um representando um cenário distinto da mesma funcionalidade.

Por exemplo, para a funcionalidade de autenticação:

- Login com credenciais válidas
- Login com credenciais inválidas
- Login com usuário bloqueado

Embora os comportamentos sejam diferentes, todos pertencem à mesma Suite, pois validam o mesmo fluxo de negócio.

### Definição de estado global (Database)

A Suite pode definir **estado global de banco de dados**, normalmente por meio de scripts SQL.

Esse estado:

- É aplicado antes da execução dos Scripts
- É compartilhado por todos os cenários da Suite
- Não deve conter dados específicos de um único Script

Essa abordagem garante:

- Previsibilidade das execuções
- Reprodutibilidade dos testes
- Isolamento entre funcionalidades distintas

Estados específicos de cenários devem ser definidos no nível do Script.

## O que NÃO deve estar em uma Suite

Para manter a clareza e a previsibilidade do modelo, uma Suite **não deve**:

- Conter lógica de teste
- Interagir com Page Objects
- Executar validações
- Depender de dados específicos de um cenário

Essas responsabilidades pertencem aos níveis inferiores da hierarquia e devem ser mantidas fora da Suite.

## Relação da Suite com o JUnit 5

No Probato, a Suite é o elemento que o **JUnit 5 descobre e executa**.

A partir da Suite, o framework:

- Identifica os Scripts declarados
- Executa cada Script dinamicamente
- Aplica datasets e configurações automaticamente

Esse modelo permite:

- Integração nativa com pipelines de CI/CD
- Execução paralela de cenários
- Geração de relatórios compatíveis com o ecossistema JUnit

Tudo isso ocorre sem que a Suite precise conter código imperativo de execução.

## Boas práticas

- Crie Suites pequenas e focadas em uma única funcionalidade
- Evite misturar fluxos não relacionados na mesma Suite
- Utilize estado global apenas quando realmente necessário
- Prefira múltiplas Suites coesas a uma Suite grande e genérica

## Próximo passo

Após compreender o papel da Suite, o próximo conceito a ser estudado é o **Script**, responsável por descrever os cenários individuais de teste.

➡️ Continue em **Script**.
