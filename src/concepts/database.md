# Database

The **Database** concept in Probato represents the **application state** required for the execution of a test scenario.
It allows preparing, validating, or cleaning data in a declarative way, without mixing state with execution logic.

In the Probato mental model, Database deals with **state**, not behavior.

Probato provides support for **SQL and NoSQL scripts**, allowing state preparation for both relational and non-relational databases.

## Role of Database in Probato

The Database is responsible for:

- Preparing the application state before execution
- Ensuring predictability and reproducibility of tests
- Isolating external dependencies from test logic
- Keeping execution code clean and focused

> The Database answers the question: *In which state must the system be before execution?*

## Where Database fits in the mental model

Suite
 ├── SQL (global state / feature preconditions)
 ├── NoSQL (global state / feature preconditions)
 └── Script
      ├── Dataset (execution data)
      ├── SQL (scenario-specific state)
      ├── NoSQL (scenario-specific state)
      ├── Precondition
      │     └── Page Object
      │           ├── Action
      │           └── Param
      ├── Procedure
      │     └── Page Object
      │           ├── Action
      │           └── Param
      └── Postcondition
            └── Page Object
                  ├── Action
                  └── Param

## Database at the Suite level

When defined at the **Suite** level, Database represents a **global feature state**.

Characteristics:

- Applied before Script execution
- Shared by all scenarios within the Suite
- Ideal for common data and general prerequisites

Examples of use:

- Initial data loading
- Default user configuration
- Functional environment preparation

## Database at the Script level

When defined at the **Script** level, Database represents a **scenario-specific state**.

Characteristics:

- Applied only to that Script
- Does not affect other scenarios
- Ideal for specific data or state variations

Examples of use:

- Blocked user
- Invalid data
- Transient states

## Separation between state and logic

In Probato:

- Database **does not execute test logic**
- Procedures **do not manipulate state directly**
- Scripts only declare which state is required

This separation ensures:

- more predictable tests
- lower coupling
- easier maintenance

## Best practices

- Use Database only when necessary
- Prefer minimal state for each scenario
- Avoid dependencies between executions
- Keep SQL and NoSQL scripts simple and clear

## Final considerations

Proper use of Database is essential to ensure reliable and reproducible tests.
It should be treated as **supporting infrastructure**, never as part of validation logic.

## Next step

With all concepts understood, the next step is to move on to the **Guides** or **Configuration** sections, where the practical use of the framework is detailed.
