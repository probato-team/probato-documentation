# Test Script

O **Test Script** representa um **cenário de teste** no Probato.  
Ele descreve *o que será executado* em um determinado fluxo, sem conter lógica de execução direta.

No modelo mental do Probato, o Script ocupa o nível intermediário da hierarquia, conectando a Suite às Procedures.

---

## Papel do Script no Probato

O Script é responsável por:

- definir um cenário específico dentro de uma funcionalidade
- declarar quais dados serão utilizados na execução
- orquestrar a execução de uma ou mais Procedures
- definir pré e pós-condições específicas do cenário

O Script **não executa lógica de negócio**.

> O Script descreve *qual cenário será executado*, não *como executá-lo*.

---

## Onde o Script se encaixa no modelo mental

```
Suite
 └── Script
      ├── @Dataset
      ├── @SQL (estado do cenário)
      ├── Precondition
      ├── Procedure
      └── Postcondition
```

Cada Script representa uma execução independente dentro da Suite.

---

## Responsabilidades do Script

### 1. Definição do cenário

O Script representa um cenário claro e isolado.

Exemplos de Scripts:
- Login com credenciais válidas
- Login com senha inválida
- Login com usuário bloqueado

Cada Script deve representar **uma única intenção de validação**.

---

### 2. Declaração de dados (Dataset)

O Script é o ponto onde os **dados de teste** são declarados.

Ao associar um Dataset a um Script:
- o cenário passa a ser executado múltiplas vezes
- cada conjunto de dados gera uma execução independente
- a lógica da Procedure permanece inalterada

Isso permite execução *data-driven* de forma nativa e transparente.

---

### 3. Definição de estado específico (Database)

O Script pode declarar **estado específico de banco de dados**, quando necessário.

Esse estado:
- é aplicado apenas ao cenário
- não afeta outros Scripts da mesma Suite
- deve conter apenas dados necessários para o cenário em questão

---

### 4. Orquestração de Procedures

O Script define **quais Procedures serão executadas**, bem como sua ordem.

Ele não conhece detalhes internos da execução, apenas:
- quais Procedures participam do cenário
- em qual sequência elas devem ser executadas

---

## O que NÃO deve estar em um Script

Para manter a separação de responsabilidades, um Script **não deve**:

- conter lógica de execução
- interagir diretamente com Page Objects
- acessar dados de banco manualmente
- realizar validações complexas

Essas responsabilidades pertencem às Procedures.

---

## Relação entre Script e Procedure

O Script funciona como um **orquestrador declarativo**.

Enquanto o Script:
- descreve o cenário
- organiza a execução

A Procedure:
- executa a lógica
- interage com a aplicação
- realiza validações

Essa separação garante:
- maior reutilização
- menor acoplamento
- cenários mais legíveis

---

## Boas práticas

- Crie Scripts pequenos e focados
- Evite misturar múltiplas intenções no mesmo Script
- Utilize Dataset para variação de dados, não lógica condicional
- Prefira múltiplos Scripts simples a um Script complexo

---

## Próximo passo

Após compreender o papel do Script, o próximo conceito a ser estudado é a **Procedure**, responsável pela execução da lógica do cenário.

➡️ Continue em **Procedure**.
