# **Implementação de Page Object**

Nessa seção será implementado Page Object. NEste Page Object irá contemplar o conjunto de procedimentos necessários para execução do cenário de teste de login com sucesso no **Probato**

## **Implementando Page Object**

1. No pacote `org.probato.manager.page` vamos criar a classe `LoginPage.java`.
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
  
  @Action("Fill in the 'Password' field with {{password}} value")
  public void fillPassword(@Param("password") String password) {
    passwordInput.sendKeys(password);
  }
  
  @Action("Press the 'Access' button")
  public void pressAccessButton() {
    accessButton.click();
  }
  
}
```
**Obs:** Também poderá ser acionadas execuções direta para os frameworks de execução atravês do método `driver()`

## Atualizando classe Procedure

1. Na classe `PerformLoginSuccessfullyProcedure.java` vamos implementar o método procedure abaixo.
```java title="PerformLoginSuccessfullyProcedure.java" linenums="1" hl_lines="8-9 13-16"
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;
import org.probato.api.Page;

public class PerformLoginSuccessfullyProcedure {

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

## **Checklist Final**

Antes de prosseguir para a próxima seção, verifique se:

- ✅ O código criado compila com sucesso.
- ✅ A execução abre navegador e executa os procedimentos.

Seu projeto está pronto para avançar para as próximas etapas da automação de testes com o **Probato**.
