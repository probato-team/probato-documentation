# Suite de Teste

A **Suite de Teste** é o ponto de entrada conceitual e estrutural do Probato.  
Ela representa uma **funcionalidade**, **caso de uso** ou **fluxo de negócio** que será validado por meio de um conjunto de cenários de teste.

No modelo mental do Probato, a Suite está no nível mais alto da hierarquia.

---

## Papel da Suite no Probato

A Suite é responsável por:

- agrupar Scripts relacionados a uma mesma funcionalidade
- definir pré-condições globais para os cenários
- servir como ponto de descoberta para o JUnit 5
- orquestrar a execução de múltiplos Scripts

Ela **não contém lógica de execução de teste**.

> A Suite descreve *o que será validado*, não *como validar*.

---

## Onde a Suite se encaixa no modelo mental

```
Suite
 ├── @SQL (estado global)
 └── Script
      ├── @Dataset
      ├── @SQL (estado do cenário)
      ├── Procedure
      └── Page Object
```

Tudo que pertence à Suite deve ser comum a **todos os cenários** (Scripts) que ela agrupa.

---

## Responsabilidades da Suite

### 1. Organização semântica

A Suite fornece uma **organização semântica** dos testes.

Exemplos de Suites:

- Autenticação de Usuário
- Cadastro de Cliente
- Fluxo de Compra
- Recuperação de Senha

Cada Suite representa uma intenção clara de validação.

---

### 2. Agrupamento de Scripts

Uma Suite pode conter **um ou vários Scripts**, cada um representando um cenário distinto da mesma funcionalidade.

Por exemplo:

- Login com credenciais válidas
- Login com credenciais inválidas
- Login com usuário bloqueado

Todos esses Scripts pertencem à mesma Suite.

---

### 3. Definição de estado global (Database)

A Suite pode definir **estado global de banco de dados**, por meio de scripts SQL.

Esse estado:

- é aplicado antes da execução dos Scripts
- é compartilhado por todos os cenários da Suite
- não deve conter dados específicos de um único Script

Isso garante:

- previsibilidade
- reprodutibilidade
- isolamento entre funcionalidades

---

## O que NÃO deve estar em uma Suite

Para manter a clareza e a previsibilidade, uma Suite **não deve**:

- conter lógica de teste
- interagir com Page Objects
- executar validações
- depender de dados específicos de um cenário

Essas responsabilidades pertencem aos níveis inferiores da hierarquia.

---

## Relação da Suite com o JUnit 5

No Probato, a Suite é o elemento que o **JUnit 5 descobre e executa**.

A partir da Suite:

- o framework identifica os Scripts declarados
- executa cada Script dinamicamente
- aplica datasets e configurações automaticamente

Isso permite:

- integração nativa com CI/CD
- execução paralela
- geração de relatórios compatíveis com o ecossistema JUnit

---

## Boas práticas

- Crie Suites pequenas e focadas em uma funcionalidade
- Evite misturar fluxos não relacionados na mesma Suite
- Utilize estado global apenas quando realmente necessário
- Prefira múltiplas Suites a uma Suite genérica e grande

---

## Próximo passo

Após compreender o papel da Suite, o próximo conceito a ser estudado é o **Script**, que descreve os cenários individuais de teste.

➡️ Continue em **Test Script**.
