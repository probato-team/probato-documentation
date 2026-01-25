# Implementação de Dataset

Nesta seção será implementado um **Dataset**, responsável por fornecer os **dados de entrada** para a execução do cenário de **login com sucesso** no **Probato**. O Dataset permite que o mesmo Script seja executado múltiplas vezes com diferentes conjuntos de dados, de forma **declarativa e automática**, sem introduzir lógica condicional no código de teste.

No modelo do Probato, **dados não pertencem ao Script nem à Procedure**, mas são declarados externamente por meio de Datasets.

## Criando o arquivo de Dataset

1. No diretório `src/test/resources/dataset`, crie a pasta `UC01`.
2. Dentro de `src/test/resources/dataset/UC01`, crie o arquivo `UC01TC01.csv`.
3. Adicione o conteúdo abaixo ao arquivo:

```csv
EMAIL,PASSWORD
user01@probato.org,p@ssword
user02@probato.org,p@ssword123
user03@probato.org,p@ssword321
```

Cada linha do arquivo CSV representa **uma execução independente** do Script associado.

## Implementando o modelo de dados (Datamodel)

Para mapear os dados do CSV de forma tipada e segura, é necessário criar um **modelo de dados**.

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

## Atualizando a classe Procedure

```java
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;
import org.probato.api.Page;
import org.probato.manager.automation.model.LoginData;

public class EfetuarLoginComSucessoProcedure {

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

## Atualizando a classe Script

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
public class UC01TC01_EfetuarLoginComSucesso {

    @Procedure
    private EfetuarLoginComSucessoProcedure procedure;
}
```

## Checklist final

- ✅ Dataset criado corretamente
- ✅ Modelo de dados mapeado
- ✅ Execução data-driven funcionando

➡️ Continue em **Implementação de Database**
