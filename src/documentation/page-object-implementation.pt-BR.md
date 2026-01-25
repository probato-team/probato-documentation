# Implementação de Page Object

Nesta seção será implementado um **Page Object**, responsável por encapsular as interações com a interface do usuário necessárias para a execução do cenário de **login com sucesso** no **Probato**. O Page Object representa a camada mais baixa da hierarquia conceitual e deve conter apenas **interações de interface**, sem qualquer lógica de cenário ou decisão de fluxo.

## Implementando o Page Object

1. No pacote `org.probato.manager.page`, crie a classe `LoginPage.java`.

```java title="LoginPage.java" linenums="1"
package org.probato.manager.automation.page;

import static org.junit.jupiter.api.Assertions.assertEquals;
import static org.junit.jupiter.api.Assertions.assertTrue;

import org.openqa.selenium.WebElement;
import org.openqa.selenium.support.FindBy;

import org.probato.api.Action;
import org.probato.api.Param;
import org.probato.page.WebPage;

public class LoginPage extends WebPage {

    @FindBy(xpath = "//*[@id=\"public-container\"]/app-login/form/div/div[1]/h1")
    private WebElement titlePage;

    @FindBy(xpath = "//*[@id=\"email\"]")
    private WebElement emailInput;

    @FindBy(xpath = "//*[@id=\"password\"]")
    private WebElement passwordInput;

    @FindBy(xpath = "//*[@id=\"login-btn\"]")
    private WebElement accessButton;

    @Action("Check `Login` page")
    public void checkPage() {
        assertEquals("Login", titlePage.getText());
        assertTrue(emailInput.isDisplayed());
        assertTrue(passwordInput.isDisplayed());
        assertTrue(accessButton.isDisplayed());
    }

    @Action("Fill in the 'Email' field with '{{email}}' value")
    public void fillEmail(@Param("email") String email) {
        emailInput.sendKeys(email);
    }

    @Action("Fill in the 'Password' field with '{{password}}' value")
    public void fillPassword(@Param("password") String password) {
        passwordInput.sendKeys(password);
    }

    @Action("Press the 'Access' button")
    public void pressAccessButton() {
        accessButton.click();
    }

}
```

As anotações `@Action` e `@Param` enriquecem semanticamente a execução, permitindo:

- Geração de logs mais claros
- Rastreabilidade de ações
- Relatórios compreensíveis para stakeholders

> **Observação:** Também é possível acionar diretamente o driver do framework de automação por meio do método `driver()`, herdado da classe `WebPage`.

## Atualizando a classe Procedure

Com o Page Object implementado, ele deve ser utilizado pela Procedure responsável pela execução do cenário.

1. Abra a classe `EfetuarLoginComSucessoProcedure.java`.
2. Injete o Page Object utilizando a anotação `@Page`.

```java title="EfetuarLoginComSucessoProcedure.java" linenums="1" hl_lines="8-9 13-16"
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;
import org.probato.api.Page;

public class EfetuarLoginComSucessoProcedure {

    @Page
    private LoginPage loginPage;

    @Run
    private void procedure() {
        loginPage.checkPage();
        loginPage.fillEmail("user@probato.org");
        loginPage.fillPassword("@pass123");
        loginPage.pressAccessButton();
    }

}
```

Nesse modelo:

- A **Procedure** coordena o fluxo do cenário
- O **Page Object** executa apenas interações de interface
- Não há acoplamento entre Script e Page Object

## Checklist final

Antes de prosseguir para a próxima seção, verifique se:

- ✅ A classe `LoginPage` foi criada corretamente.
- ✅ A Procedure injeta e utiliza o Page Object.
- ✅ O navegador é aberto e as ações são executadas conforme esperado.

Com o Page Object implementado, o próximo passo será trabalhar com **Dataset**, separando dados de execução da lógica do cenário.

➡️ Continue em **Implementação de Dataset**.
