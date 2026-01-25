# Implementação de Suite

Nesta seção será implementada uma **Suite de testes básica** utilizando o **Probato**. O framework adota uma estrutura modular composta por **Suites**, **Scripts**, **Procedures** e **Page Objects**. O ponto de partida de qualquer funcionalidade automatizada é a **Suite**, pois ela define o contexto e agrupa os cenários de teste relacionados.

Para exemplificar a automação de uma funcionalidade real, utilizaremos a aplicação **Probato Manager**. A funcionalidade inicial escolhida será **Efetuar Login**, já que a tela de login é o ponto de entrada principal da aplicação.

## Objetivo desta implementação

Ao final desta seção, você terá:

- Uma Suite corretamente definida e reconhecida pelo JUnit 5
- A base estrutural para adicionar Scripts de teste
- Compreensão prática de como o Probato organiza funcionalidades

## Criando a classe Suite

Uma **Suite** consiste em um agrupamento organizado de Scripts de teste destinados a validar uma funcionalidade específica do sistema. Ela não contém lógica de execução, apenas descreve **o que será validado**.

### Passo a passo

1. No pacote `org.probato.manager.usecase`, crie um novo pacote chamado `UC01`.
2. Dentro do pacote `org.probato.manager.usecase.UC01`, crie a classe `UC01_EfetuarLogin.java`.
3. Implemente o código abaixo:

```java title="UC01_EfetuarLogin.java" linenums="1"
package org.probato.manager.usecase.UC01;

import org.probato.api.Suite;
import org.probato.api.TestSuite;

@Suite(
    code = "UC01",
    name = "Efetuar Login",
    description = "Valida a funcionalidade de autenticação de usuários no sistema"
)
class UC01_EfetuarLogin implements TestSuite {

}
```

### Entendendo a anotação @Suite

- **code**: Identificador único da funcionalidade.
- **name**: Nome legível da funcionalidade.
- **description**: Descrição do objetivo da Suite.

Essa anotação permite que o Probato e o JUnit 5 descubram automaticamente a funcionalidade a ser executada.

## Executando a Suite

Se você executar o projeto neste ponto, o Probato informará que:

> A Suite deve possuir pelo menos um Script de teste.

Esse comportamento é esperado, pois a Suite apenas define o contexto da funcionalidade — os cenários serão adicionados nos próximos passos.

## Checklist final

Antes de prosseguir para a próxima seção, verifique se:

- ✅ A classe `UC01_EfetuarLogin` foi criada corretamente.
- ✅ O projeto compila sem erros.
- ✅ A Suite é reconhecida pelo JUnit 5 durante a execução.

Com a Suite criada, o próximo passo será implementar o **Script**, que representa um cenário específico de teste.

➡️ Continue em **Implementação de Script**.
