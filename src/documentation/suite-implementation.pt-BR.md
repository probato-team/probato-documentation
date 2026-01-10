# **Implementação de Suite**

Nessa seção será implementado um suite de testes básico. O **Probato** adota uma estrutura modular que inclui suites, scripts, procedures e page objects, vamos iniciar pelo nosso test suite. Para exemplificar a automação de uma funcionalidade real, seguiremos com o desenvolvimento da automação da aplicação **Probato Manager**. O **Probato Manager** possui como tela principal a página de login, então partiremos desta funcionalidade para o desenvolvimento dos testes automatizados: **Efetuar Login**

## **Implementado classe Suite**

A _Suite_ consiste em um agrupamento organizado de scripts de teste destinados a validar funcionalidades relacionadas ou específicas de um sistema. A _Suite_ é essencial para estruturar e gerenciar a execução de múltiplos testes, garantindo que eles sejam executados de forma eficiente e em uma ordem lógica, quando necessário. Vamos criar nossa suite de testes.

1. No pacote `org.probato.manager.usecase` vamos criar o novo pacote `UC01` .
2. No pacote `org.probato.manager.usecase.UC01` vamos criar a classe `UC01_PerformLogin.java`.
3. Na classe `UC01_PerformLogin.java` vamos implementar o código abaixo.
```java title="UC01_PerformLogin.java" linenums="1"
package org.probato.manager.usecase.UC01;

import org.probato.api.Suite;
import org.probato.api.TestSuite;

@Suite(
  code = "UC01", 
  name = "Perform login", 
  description = "This feature aims to allow the user to login to this application")
class UC01_PerformLogin implements TestSuite {
  
}
```
4. Caso seja executado o teste no estado atual, será recebido a mensagem informando que a suite deve possuir pelo menos 1 caso de teste.

## **Checklist Final**

Antes de prosseguir para a próxima seção, verifique se:

- ✅ O código criado compila com sucesso.
- ✅ A suite de testes é reconhecida pelo JUnit 5.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o **Probato**.
