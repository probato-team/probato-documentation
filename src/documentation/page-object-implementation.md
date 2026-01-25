# Page Object Implementation

In this section, a **Page Object** will be implemented, responsible for encapsulating the user interface interactions required to execute the **successful login** scenario in **Probato**. The Page Object represents the lowest layer of the conceptual hierarchy and must contain only **UI interactions**, without any scenario logic or flow decisions.

## Implementing the Page Object

1. In the package `org.probato.manager.page`, create the class `LoginPage.java`.

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

The `@Action` and `@Param` annotations semantically enrich the execution, enabling:

- clearer logs
- action traceability
- reports that are easier for stakeholders to understand

> **Note:** It is also possible to directly access the automation framework driver through the `driver()` method inherited from the `WebPage` class.

## Updating the Procedure class

With the Page Object implemented, it must be used by the Procedure responsible for executing the scenario.

1. Open the class `DoLoginSuccessfullyProcedure.java`.
2. Inject the Page Object using the `@Page` annotation.

```java title="DoLoginSuccessfullyProcedure.java" linenums="1" hl_lines="8-9 13-16"
package org.probato.manager.automation.usecase.UC01.procedure;

import org.probato.api.Run;
import org.probato.api.Page;

public class DoLoginSuccessfullyProcedure {

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

In this model:

- the **Procedure** coordinates the scenario flow
- the **Page Object** executes only UI interactions
- there is no coupling between Script and Page Object

## Final checklist

Before proceeding to the next section, make sure that:

- ✅ The `LoginPage` class was created correctly.
- ✅ The Procedure injects and uses the Page Object.
- ✅ The browser opens and the actions are executed as expected.

With the Page Object implemented, the next step will be to work with **Dataset**, separating execution data from scenario logic.

➡️ Continue to **Dataset Implementation**.
