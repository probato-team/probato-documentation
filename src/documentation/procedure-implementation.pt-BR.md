# **Implementação de Procedure**

Nessa seção será implementado um procedure de testes básico. Este procedure irá contemplar o script referente ao cenário de teste de login com sucesso no **Probato**. Existem duas forma para implementação de procedures.

## **Implementado método Procedure **

1. Na classe `UC01TC01_PerformLoginSuccessfully.java` vamos implementar o método procedure abaixo.
```java title="UC01TC01_PerformLoginSuccessfully.java" linenums="1" hl_lines="12-15"

package org.probato.manager.automation.usecase.UC01.script;

import org.probato.api.Procedure;
import org.probato.api.Script;

@Script(
  code = "UC01TC01", 
  name = "Perform login successfully", 
  description = "This script aims to validate the user's login in the application successfully")
public class UC01TC01_PerformLoginSuccessfully {

  @Procedure
  private void procedure() {
    System.out.println("Run method procedure");
  }
  
}
```

2. Caso necessário destinção entre procedimentos de pré condição e pós condição, pode ser adicionados métodos específicos para execução desses procedimentos.
```java title="UC01TC01_PerformLoginSuccessfully.java" linenums="1" hl_lines="14-17 19-22 24-27"

package org.probato.manager.automation.usecase.UC01.script;

import org.probato.api.Procedure;
import org.probato.api.Precondition;
import org.probato.api.Postcondition;
import org.probato.api.Script;

@Script(
  code = "UC01TC01", 
  name = "Perform login successfully", 
  description = "This script aims to validate the user's login in the application successfully")
public class UC01TC01_PerformLoginSuccessfully {

  @Precondition
  private void precondition() {
    System.out.println("Run method precondition");
  }

  @Procedure
  private void procedure() {
    System.out.println("Run method procedure");
  }

  @Postcondition
  private void postcondition() {
    System.out.println("Run method postcondition");
  }
  
}
```

## **Implementado classe Procedure**

```java title="PerformLoginSuccessfullyProcedure.java" linenums="1" hl_lines="7-10"
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;

public class PerformLoginSuccessfullyProcedure {

  @Run
  private void procedure() {
    System.out.println("Run method procedure");
  }
  
}

```

## Atualizando classe Script

1. Na classe `UC01TC01_PerformLoginSuccessfully.java` vamos adicionar a implementação abaixo.
```java title="UC01TC01_PerformLoginSuccessfully.java" linenums="1" hl_lines="12-13"

package org.probato.manager.automation.usecase.UC01.script;

import org.probato.api.Procedure;
import org.probato.api.Script;

@Script(
  code = "UC01TC01", 
  name = "Perform login successfully", 
  description = "This script aims to validate the user's login in the application successfully")
public class UC01TC01_PerformLoginSuccessfully {

  @Procedure
  private PerformLoginSuccessfullyProcedure procedure;
  
}
```

## **Checklist Final**

Antes de prosseguir para a próxima seção, verifique se:

- ✅ O código criado compila com sucesso.
- ✅ Os métodos de procedimentos são executados e imprime as saídas esperadas.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o **Probato**.
