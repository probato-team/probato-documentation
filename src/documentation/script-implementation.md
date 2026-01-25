# Script Implementation

In this section, a **basic test Script** will be implemented, responsible for representing a **test scenario** in Probato. The implemented scenario will be **successful login** in the **Probato Manager** application.

The Script describes **which scenario will be executed**, but it does not contain execution logic — that responsibility belongs to Procedures.

## Creating the Script class

The Script belongs to the same context as the Suite and represents a specific scenario within the functionality.

### Step by step

1. In the package `org.probato.manager.usecase.UC01`, create a new package named `script`.
2. In the package `org.probato.manager.usecase.UC01.script`, create the class `UC01TC01_DoLoginSuccessfully.java`.
3. Implement the code below:

```java title="UC01TC01_DoLoginSuccessfully.java" linenums="1"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;

@Script(
    code = "UC01TC01",
    name = "Do login successfully",
    description = "Validates the user authentication scenario with valid credentials"
)
public class UC01TC01_DoLoginSuccessfully {

}
```

The Script above describes only **the intention of the scenario**. No actions are executed at this level.

## Associating the Script with the Suite

After creating the Script, it must be associated with the corresponding Suite.

1. Open the Suite class `UC01_DoLogin`.
2. Add the Script as an annotated field.

```java title="UC01_DoLogin.java" linenums="1" hl_lines="14-15"
package org.probato.manager.usecase.UC01;

import org.probato.api.Suite;
import org.probato.api.TestCase;
import org.probato.manager.usecase.UC01.script.UC01TC01_DoLoginSuccessfully;

@Suite(
    code = "UC01",
    name = "Do Login",
    description = "Validates the user authentication functionality in the system"
)
class UC01_DoLogin {

    @TestCase
    private UC01TC01_DoLoginSuccessfully uc01tc01;

}
```

The `@TestCase` annotation indicates to Probato that this Script is part of the Suite execution.

## Executing at this stage

If the project is executed at this point, Probato will report that:

> the Script must contain at least one Procedure.

This behavior is expected, since the Script only describes the scenario — the logic will be implemented in the next step.

## Final checklist

Before proceeding, make sure that:

- ✅ The `UC01TC01_DoLoginSuccessfully` class was created correctly.
- ✅ The Script was associated with the Suite.
- ✅ The project compiles without errors.
- ✅ The scenario is recognized by JUnit 5.

With the Script defined, the next step is to implement the **Procedure**, responsible for executing the scenario logic.

➡️ Continue to **Procedure Implementation**.
