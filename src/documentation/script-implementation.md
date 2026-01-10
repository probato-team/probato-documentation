# **Implementação de Script**

Nessa seção será implementado um script de testes básico. Este script irá contemplar o cenário de teste de login com sucesso no **Probato**

## **Implementado classe Script**

1. No pacote `org.probato.manager.usecase.UC01` vamos criar o novo pacote `script` .
2. No pacote `org.probato.manager.usecase.UC01.script` vamos criar a classe `UC01TC01_PerformLoginSuccessfully.java`.
3. Na classe `UC01TC01_PerformLoginSuccessfully.java` vamos implementar o código abaixo.
```java title="UC01TC01_PerformLoginSuccessfully.java" linenums="1"
package org.probato.manager.automation.usecase.UC01.script;

import org.probato.api.Script;

@Script(
  code = "UC01TC01", 
  name = "Perform login successfully", 
  description = "This script aims to validate the user's login in the application successfully")
public class UC01TC01_PerformLoginSuccessfully {

} 
```

## **Atualizando classe Suite**

1. Na classe `UC01_PerformLogin.java` vamos adicionar a implementação abaixo.
```java title="UC01_PerformLogin.java" linenums="1" hl_lines="13-14"
package org.probato.manager.usecase.UC01;

import org.probato.api.Suite;
import org.probato.api.TestSuite;
import org.probato.manager.automation.usecase.UC01.script.UC01TC01_PerformLoginSuccessfully;

@Suite(
  code = "UC01", 
  name = "Perform login", 
  description = "This feature aims to allow the user to login to this application")
class UC01_PerformLogin implements TestSuite {

  @TestCase
  private UC01TC01_PerformLoginSuccessfully uc01tc01;

}
```
2. Caso seja executado o teste no estado atual, será recebido a mensagem informando que o script deve possuir pelo menos 1 procedure.

## **Checklist Final**

Antes de prosseguir para a próxima seção, verifique se:

- ✅ O código criado compila com sucesso.
- ✅ O cenário de testes é reconhecida pelo JUnit 5.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o **Probato**.
