# Suite

A **Suite** is the conceptual and structural entry point of Probato.  
It represents a **feature**, **use case**, or **business flow** that will be validated through a set of test scenarios.

In Probato’s mental model, the Suite occupies the **highest level of the hierarchy**, being responsible for defining the *context* in which tests will be executed.

A Suite does not describe test steps or execution logic.  
It defines the **validation intent**.

## The Role of the Suite in Probato

A Suite is responsible for:

- grouping Scripts related to the same feature
- defining global preconditions for scenarios
- serving as the discovery entry point for JUnit 5
- orchestrating the execution of multiple Scripts

It **does not contain test execution logic**.

> A Suite describes *what will be validated*, not *how to validate it*.

## Where the Suite Fits in the Mental Model

In Probato’s conceptual flow, the Suite encapsulates all elements required to validate a complete feature.

``` title="Conceptual model" hl_lines="1-3"
@Suite
 ├── @SQL (global state / feature preconditions)
 ├── @NoSQL (global state / feature preconditions)
 └── @Script
      ├── @Dataset (execution data)
      ├── @SQL (scenario-specific state)
      ├── @NoSQL (scenario-specific state)
      ├── @Precondition
      │     └── Page Object
      │           ├── @Action
      │           └── @Param
      ├── @Procedure
      │     └── Page Object
      │           ├── @Action
      │           └── @Param
      └── @Postcondition
            └── Page Object
                  ├── @Action
                  └── @Param
```

Everything that belongs to the Suite must be **common to all scenarios** (Scripts) it groups.

If something varies between scenarios, it does not belong in the Suite.

## Suite Responsibilities

### Semantic Organization

The Suite provides a **semantic organization** of tests, aligned with the business view of the system.

Examples of Suites:

- User Authentication
- Customer Registration
- Purchase Flow
- Password Recovery

Each Suite represents a **clear validation intent**, easily understood by developers, QAs, and technical stakeholders.

### Grouping of Scripts

A Suite may contain **one or multiple Scripts**, each representing a distinct scenario of the same feature.

For example, for the authentication feature:

- Login with valid credentials
- Login with invalid credentials
- Login with a blocked user

Although the behaviors differ, they all belong to the same Suite because they validate the same business flow.

### Definition of Global State (Database)

A Suite may define **global database state**, typically through SQL scripts.

This state:

- is applied before Script execution
- is shared by all scenarios in the Suite
- must not contain data specific to a single Script

This approach ensures:

- predictable executions
- reproducible tests
- isolation between distinct features

Scenario-specific state must be defined at the Script level.

## What Should NOT Be in a Suite

To maintain clarity and predictability of the model, a Suite **must not**:

- contain test logic
- interact with Page Objects
- perform validations
- depend on scenario-specific data

These responsibilities belong to lower levels of the hierarchy and must be kept out of the Suite.

## Relationship Between the Suite and JUnit 5

In Probato, the Suite is the element that **JUnit 5 discovers and executes**.

From the Suite, the framework:

- identifies declared Scripts
- dynamically executes each Script
- automatically applies datasets and configurations

This model enables:

- native CI/CD pipeline integration
- parallel scenario execution
- report generation compatible with the JUnit ecosystem

All of this happens without requiring the Suite to contain imperative execution code.

## Best Practices

- Create small Suites focused on a single feature
- Avoid mixing unrelated flows within the same Suite
- Use global state only when truly necessary
- Prefer multiple cohesive Suites over a large, generic one

## Next Step

After understanding the role of the Suite, the next concept to study is **Script**, which describes individual test scenarios.

➡️ Continue to **Script**.
