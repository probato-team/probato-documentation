# Procedure Implementation

In this section, a **basic test Procedure** will be implemented, responsible for **executing the scenario logic** previously defined in the successful login Script. The Procedure is the point where the system behavior is effectively exercised. It executes actions, interacts with the application, and performs validations, always within the context of a Script.

In Probato, a Procedure can be implemented in **two ways**:

- As a method inside the Script
- As a reusable dedicated class

## Implementing a Procedure as a method in the Script

This approach is recommended for simple scenarios, with short logic and no need for reuse.

1. Open the class `UC01TC01_DoLoginSuccessfully.java`.
2. Add a method annotated with `@Procedure`.

```java title="UC01TC01_DoLoginSuccessfully.java" linenums="1" hl_lines="13-16"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;
import org.probato.api.Procedure;

@Script(
    code = "UC01TC01",
    name = "Do login successfully",
    description = "Validates the user authentication scenario with valid credentials"
)
public class UC01TC01_DoLoginSuccessfully {

    @Procedure
    private void procedure() {
        System.out.println("Executing main procedure");
    }

}
```

In this model, the method annotated with `@Procedure` represents the **main execution of the scenario**.

## Separating precondition and postcondition

If it is necessary to distinguish scenario stages, specific methods can be defined.

```java title="UC01TC01_DoLoginSuccessfully.java" linenums="1" hl_lines="15-18 20-23 25-28"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;
import org.probato.api.Procedure;
import org.probato.api.Precondition;
import org.probato.api.Postcondition;

@Script(
    code = "UC01TC01",
    name = "Do login successfully",
    description = "Validates the user authentication scenario with valid credentials"
)
public class UC01TC01_DoLoginSuccessfully {

    @Precondition
    private void precondition() {
        System.out.println("Executing precondition");
    }

    @Procedure
    private void procedure() {
        System.out.println("Executing main procedure");
    }

    @Postcondition
    private void postcondition() {
        System.out.println("Executing postcondition");
    }

}
```

This separation improves readability, traceability, and failure diagnostics.

## Implementing a Procedure as a dedicated class

This approach is recommended when the logic:

- Is more complex
- Needs to be reused
- Should be isolated from the Script

1. Create the class `DoLoginSuccessfullyProcedure.java`.

```java title="DoLoginSuccessfullyProcedure.java" linenums="1" hl_lines="7-10"
package org.probato.manager.usecase.UC01.procedure;

import org.probato.api.Run;

public class DoLoginSuccessfullyProcedure {

    @Run
    private void procedure() {
        System.out.println("Executing main procedure");
    }

}
```

The `@Run` annotation indicates the entry point for the Procedure execution.

## Associating the Procedure with the Script

After creating the Procedure class, it must be associated with the Script.

```java title="UC01TC01_DoLoginSuccessfully.java" linenums="1" hl_lines="14-15"
package org.probato.manager.usecase.UC01.script;

import org.probato.api.Script;
import org.probato.api.Procedure;
import org.probato.manager.usecase.UC01.procedure.DoLoginSuccessfullyProcedure;

@Script(
    code = "UC01TC01",
    name = "Do login successfully",
    description = "Validates the user authentication scenario with valid credentials"
)
public class UC01TC01_DoLoginSuccessfully {

    @Procedure
    private DoLoginSuccessfullyProcedure procedure;

}
```

In this model, the Script remains declarative, while the logic is encapsulated in the Procedure.

## Executing at this stage

When executing the project at this point:

- Probato will locate the associated Procedure
- Execute the annotated methods correctly
- Display the outputs in the console

This confirms that the Script → Procedure flow is working.

## Final checklist

Before proceeding, make sure that:

- ✅ The Procedure was implemented correctly.
- ✅ The Script references the Procedure.
- ✅ The project compiles without errors.
- ✅ The precondition, execution, and postcondition methods are executed.

With the Procedure implemented, the next step will be to create the **Page Objects**, responsible for encapsulating interactions with the user interface.

➡️ Continue to **Page Object Implementation**.
