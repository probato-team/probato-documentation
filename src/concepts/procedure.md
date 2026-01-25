# Procedure

A **Procedure** is the unit responsible for **executing test logic** in Probato. It contains the code that effectively interacts with the application, performs actions, and executes validations. In Probato’s mental model, the Procedure exists to clearly separate **scenario description** (Script) from **behavior execution**.

While the Script describes *what should happen*, the Procedure defines *how it happens*.

## The Role of the Procedure in Probato

A Procedure is responsible for:

- Executing the scenario logic
- Interacting with Page Objects
- Receiving already-resolved data (Dataset)
- Coordinating preconditions, execution, and postconditions

> The Procedure answers the question: *How is the scenario executed?*

It is the level where the intent declared in the Script is transformed into executable behavior.

## Where the Procedure Fits in the Mental Model

In Probato’s conceptual flow, the Procedure is always contained within a Script and never exists in isolation.

``` title="Conceptual model" hl_lines="8 12 16"
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

The Procedure is always executed within the context of a Script, using data and state previously defined.

## Implementation Forms

Probato allows two ways to implement a Procedure, depending on complexity and reuse needs.

### Procedure as a method

Recommended for simple and isolated scenarios.

Characteristics:

- Direct implementation  
- Minimal structural overhead  
- Scope limited to a single Script  

This approach is recommended only when:

- The logic is small  
- Reuse is not required  
- The flow is simple and specific  

### Procedure as a dedicated class

Recommended for reusable or more complex scenarios.

Characteristics:

- Better code organization  
- Greater reuse across Scripts  
- Clear isolation of responsibilities  

This is the **recommended** approach in most cases, especially for medium and large projects.

## Internal Structure of a Procedure

Conceptually, a Procedure can be organized into three distinct parts:

### Precondition

- Scenario preparation  
- Initial validations  
- Assurance of functional prerequisites  

### Procedure

- Main flow actions (Target objective of the test)
- Interaction with the application  
- Execution of the expected behavior  

### Postcondition

- Final validations  
- Cleanup or state restoration when necessary  

This separation improves:

- Code readability  
- Execution traceability  
- Precise failure diagnosis  

## Relationship with Page Objects

The Procedure is the only level that:

- Knows Page Objects  
- Interacts directly with the user interface  
- Coordinates UI actions as part of the flow  

Page Objects **must not contain scenario logic**. All flow decisions and validations belong to the Procedure.

## What Should NOT Be in a Procedure

To keep the architecture clear and predictable, a Procedure **must not**:

- Define Datasets  
- Configure browsers or environment  
- Declare global database state  
- Know details of Suite or Script  

These responsibilities belong to other levels of the framework.

## Best Practices

- Prefer Procedures implemented as dedicated classes  
- Keep Procedures small, cohesive, and focused  
- Avoid data-driven conditional logic  
- Reuse Procedures whenever possible  

## Next Step

After understanding the Procedure, the next concept is the **Page Object**, responsible for encapsulating user interface interactions.

➡️ Continue to **Page Object**.
