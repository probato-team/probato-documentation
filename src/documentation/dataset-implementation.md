# Dataset Implementation

In this section, a **Dataset** will be implemented, responsible for providing the **input data** for executing the **successful login** scenario in **Probato**. The Dataset allows the same Script to be executed multiple times with different data sets in a **declarative and automatic** way, without introducing conditional logic into the test code.

In the Probato model, **data does not belong to the Script or the Procedure**, but is declared externally through Datasets.

## Creating the Dataset file

1. No diretório `src/test/resources/dataset`, crie a pasta `UC01`.
2. Dentro de `src/test/resources/dataset/UC01`, crie o arquivo `UC01TC01.csv`.
3. Adicione o conteúdo abaixo ao arquivo:

```csv
EMAIL,PASSWORD
user01@probato.org,p@ssword
user02@probato.org,p@ssword123
user03@probato.org,p@ssword321
```

Each line in the CSV file represents an **independent execution** of the associated Script.

## Implementing the data model (Datamodel)

To map the CSV data in a type-safe and reliable way, it is necessary to create a **data model**.

1. No pacote `org.probato.manager.automation.model`, crie a classe `LoginData.java`.

```java
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

## Updating the Procedure class

```java
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;
import org.probato.api.Page;
import org.probato.manager.automation.model.LoginData;

public class DoLoginSuccessfullyProcedure {

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

## Updating the Script class

```java
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Dataset;
import org.probato.api.Procedure;
import org.probato.api.Script;

@Dataset("dataset/UC01/UC01TC01.csv")
@Script(
    code = "UC01TC01",
    name = "Efetuar login com sucesso",
    description = "Valida o cenário de autenticação do usuário com credenciais válidas"
)
public class UC01TC01_DoLoginSuccessfully {

    @Procedure
    private DoLoginSuccessfullyProcedure procedure;
}
```

## Final Checklist

- ✅ Dataset criado corretamente
- ✅ Modelo de dados mapeado
- ✅ Execução data-driven funcionando

➡️ Continue to **Database Implementation**
