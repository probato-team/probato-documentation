# Suite Implementation

In this section, a **basic test Suite** will be implemented using **Probato**.  
The framework adopts a modular structure composed of **Suites**, **Scripts**, **Procedures**, and **Page Objects**. The starting point of any automated functionality is the **Suite**, as it defines the context and groups the related test scenarios.

To exemplify the automation of a real feature, we will use the **Probato Manager** application. The initial functionality chosen will be **Perform Login**, since the login screen is the main entry point of the application.

## Objective of this implementation

By the end of this section, you will have:

- A Suite correctly defined and recognized by JUnit 5
- The structural foundation to add test Scripts
- A practical understanding of how Probato organizes functionalities

## Creating the Suite class

A **Suite** consists of an organized grouping of test Scripts intended to validate a specific system functionality. It does not contain execution logic; it only describes **what will be validated**.

### Step by step

1. In the package `org.probato.manager.usecase`, create a new package named `UC01`.
2. Inside the package `org.probato.manager.usecase.UC01`, create the class `UC01_DoLogin.java`.
3. Implement the code below:

```java title="UC01_DoLogin.java" linenums="1"
package org.probato.manager.usecase.UC01;

import org.probato.api.Suite;
import org.probato.api.TestSuite;

@Suite(
    code = "UC01",
    name = "Do Login",
    description = "Validates the user authentication functionality in the system"
)
class UC01_DoLogin implements TestSuite {

}
```

### Understanding the @Suite annotation

- **code**: Unique identifier of the functionality.
- **name**: Human-readable name of the functionality.
- **description**: Description of the Suite’s objective.

This annotation allows Probato and JUnit 5 to automatically discover the functionality to be executed.

## Executing the Suite

If you run the project at this point, Probato will report that:

> The Suite must contain at least one test Script.

This behavior is expected, since the Suite only defines the context of the functionality — the scenarios will be added in the next steps.

## Final checklist

Before proceeding to the next section, make sure that:

- ✅ The `UC01_DoLogin` class was created correctly.
- ✅ The project compiles without errors.
- ✅ The Suite is recognized by JUnit 5 during execution.

With the Suite created, the next step will be to implement the **Script**, which represents a specific test scenario.

➡️ Continue to **Script Implementation**.
