# Script

The **Script** represents a **test scenario** in Probato. It describes *what will be executed* within a given flow, without containing direct execution logic. In Probato’s mental model, the Script occupies the **intermediate level of the hierarchy**, connecting the Suite to the Procedures and enabling scenarios to be described in a clear, isolated, and reusable manner.

Each Script represents an **independent execution**, even when it belongs to the same Suite.

## The Role of the Script in Probato

A Script is responsible for:

- Defining a specific scenario within a feature
- Declaring which data will be used during execution
- Orchestrating the execution of one or more Procedures
- Defining scenario-specific preconditions and postconditions

A Script **does not execute business logic**.

> The Script describes *which scenario will be executed*, not *how to execute it*.

## Where the Script Fits in the Mental Model

In Probato’s conceptual flow, the Script is contained within the Suite and acts as the link between intent and execution.

``` title="Conceptual model" hl_lines="4"
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
```

Each Script represents an independent execution within the Suite, allowing data, state, and behavior to vary without affecting other scenarios.

## Script Responsibilities

### Scenario definition

A Script represents a clear, isolated, and intentional scenario.

Examples of Scripts:

- Login with valid credentials
- Login with invalid password
- Login with a blocked user

Each Script should represent **a single validation intent**, avoiding multiple behaviors within the same scenario.

### Data declaration (Dataset)

The Script is the point where **test data** is declared.

By associating a Dataset with a Script:

- The scenario is executed multiple times
- Each dataset entry generates an independent execution
- The Procedure logic remains unchanged

This enables native, predictable, and transparent *data-driven* execution.

### Definition of scenario-specific state (Database)

A Script may declare **scenario-specific database state** when required.

This state:

- Is applied only to the scenario
- Does not affect other Scripts in the same Suite
- Should contain only data required for the given scenario

Global state remains the responsibility of the Suite.

### Procedure orchestration

The Script defines **which Procedures will be executed**, as well as their execution order.

It does not know internal execution details, only:

- Which Procedures participate in the scenario
- The sequence in which they should be executed

This approach keeps the Script declarative and decoupled from implementation details.

## What Should NOT Be in a Script

To preserve separation of responsibilities, a Script **must not**:

- Contain execution logic
- Interact directly with Page Objects
- Manually access database data
- Perform complex validations

These responsibilities belong to the Procedures.

## Relationship Between Script and Procedure

The Script acts as a **declarative orchestrator**.

While the Script:

- Describes the scenario
- Organizes execution

The Procedure:

- Executes the logic
- Interacts with the application
- Performs validations

This separation ensures:

- Greater Procedure reuse
- Lower coupling between scenarios
- More readable and expressive Scripts

## Best Practices

- Create small, focused Scripts
- Avoid mixing multiple intents within a single Script
- Use Datasets for data variation, not conditional logic
- Prefer multiple simple Scripts over a single complex one

## Next Step

After understanding the role of the Script, the next concept to study is **Procedure**, which is responsible for executing the scenario logic.

➡️ Continue to **Procedure**.
