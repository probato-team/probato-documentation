# Dataset

The **Dataset** is the concept responsible for defining the **test data** used during scenario execution in Probato. It allows the same Script to be executed multiple times with different data sets, in a native and declarative way.

In Probato’s mental model, the Dataset exists to separate **data** from **execution logic**, avoiding complex conditionals and promoting reuse.

## The Role of the Dataset in Probato

The Dataset is responsible for:

- Providing external data for Script execution
- Enabling automatic *data-driven* execution
- Avoiding data-based conditional logic
- Keeping test code simple, readable, and reusable

> The Dataset answers the question: *With which data will the scenario be executed?*

## Where the Dataset Fits in the Mental Model

In Probato’s conceptual flow, the Dataset is always associated with a Script.

``` title="Conceptual model" hl_lines="5"
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

The Dataset is **never** associated directly with a Procedure or a Page Object.

## Dataset Characteristics

In Probato, a Dataset has the following characteristics:

- External to the test code
- Strongly typed
- Resolved before Procedure execution
- Independent of test logic

Each Dataset entry generates an **independent execution** of the Script, ensuring isolation and predictability.

## Data Models

The data defined in a Dataset is mapped to **data models**.

These models:

- Represent the Dataset structure
- Are automatically injected into the Procedure
- Ensure type safety and execution clarity

The Procedure receives only the resolved data model, without knowing the data’s origin or physical format.

## Benefits of Using Datasets

Proper use of Datasets enables:

- Greater test coverage without code duplication
- Simpler, more declarative scenarios
- Clear separation between data and behavior
- Easier test maintenance and evolution

## What Should NOT Be in a Dataset

To maintain separation of responsibilities, a Dataset **must not**:

- Contain execution logic
- Define business rules
- Change application state
- Depend on execution context

A Dataset must be only a **data source**.

## Best Practices

- Keep Datasets small and focused
- Create one Dataset per scenario type
- Avoid overly generic Datasets
- Name data models clearly and semantically

## Next Step

After understanding the Dataset, the next concept is **Database**, responsible for defining the application state before scenario execution.

➡️ Continue to **Database**.
