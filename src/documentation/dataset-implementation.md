# **Implementação de Dataset**

Nessa seção será implementado Dataset. Neste Dataset irá contemplar o conjunto de dados para execução do cenário de teste de login com sucesso no **Probato**

## **Criando arquivo dataset**

1. Na pasta `src/test/resources/dataset` vamos criar a nova pasta `UC01`.
2. Na pasta `src/test/resources/dataset/UC01` vamos criar o arquivo chamado `UC01TC01.csv`.
3. No arquivo `UC01TC01.csv` vamos adicionar o conteúdo abaixo.
``` title="UC01TC01.csv" linenums="1"
EMAIL, PASSWORD
user01@probato.org, p@ssword
user02@probato.org, p@ssword123
user02@probato.org, p@ssword321

```

### Implementando classe de mapeamento de entrada

1. No pacote `org.probato.manager.automation.model` vamos criar a classe `LoginData.java`.
```java title="LoginModel.java" linenums="1"
package org.probato.manager.automation.model;

import org.probato.model.Datamodel;

public class LoginData extends Datamodel {

	private String email;
	private String password;

	public String getEmail() {
		return email;
	}

	public String getPassword() {
		return password;
	}
}
```

## **Atualizando classe Procedure**

1. Na classe `PerformLoginSuccessfullyProcedure.java` vamos implementar o método procedure abaixo.
```java title="PerformLoginSuccessfullyProcedure.java" linenums="1" hl_lines="14"
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;
import org.probato.api.Page;

import org.probato.manager.automation.model.LoginData;

public class PerformLoginSuccessfullyProcedure {

  @Page
  private LoginPage loginPage;

  @Run
  private void procedure(LoginData model) {
    loginPage.checkPage();
    loginPage.fillEmail(model.getEmail());
    loginPage.fillPassword(model.getPassword());
    loginPage.pressAccessButton();
  }
  
}

```

## **Atualizando classe Script**

1. Na classe `UC01TC01_PerformLoginSuccessfully.java` vamos adicionar a implementação abaixo.
```java title="UC01TC01_PerformLoginSuccessfully.java" linenums="1" hl_lines="7"

package org.probato.manager.automation.usecase.UC01.script;

import org.probato.api.Dataset;
import org.probato.api.Procedure;
import org.probato.api.Script;

@Dataset("dataset/UC01/UC01TC01.csv")
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
- ✅ O cenário de testes é reconhecida para cada uma das linhas do arquivo CSV pelo JUnit 5.
- ✅ A execução deve receber valores parametrizados do arquivo CSV.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o **Probato**.
