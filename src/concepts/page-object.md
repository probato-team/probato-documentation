# Page Object

The **Page Object** is the component responsible for encapsulating the **user interface** in Probato. It abstracts UI details and provides clear methods for interacting with the application. In Probato’s mental model, the Page Object is an **implementation detail**, not an orchestration or flow-decision element.

Its goal is to isolate the user interface from the rest of the test code, making tests more readable, reusable, and resilient to UI changes.

## The Role of the Page Object in Probato

The Page Object is responsible for:

- Encapsulating user interface elements and actions
- Isolating UI changes from the rest of the codebase
- Providing a clear and expressive API for interaction
- Enriching execution with semantic information

> The Page Object answers the question: *How to interact with the system?*

It does not know **why** an action is executed, only **how to execute it**.

## Where the Page Object Fits in the Mental Model

In Probato’s conceptual flow, the Page Object is always used by Procedures and is never accessed directly by Scripts or Suites.

``` title="Conceptual model" hl_lines="9-11 13-15 17-19"
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

This restriction ensures that flow decisions remain outside the UI layer.

## Page Object in Probato

Probato adopts the **classic Page Object pattern** without reinventing it or introducing artificial abstractions. On top of this well-established pattern, the framework adds a **semantic layer**, enriching execution through annotations.

### Action

The `@Action` annotation semantically describes an action performed on the interface.

It enables:

- Clearer log generation
- More understandable reports
- Improved execution traceability

The action description should represent **what is being done**, not **how it is implemented**.

### Param

The `@Param` annotation identifies relevant parameters used in an action.

It enables:

- Tracking of data used during execution
- Enrichment of metrics and evidence
- Easier auditing and failure diagnosis

These annotations do not change code behavior, but significantly improve observability.

## Separation of Responsibilities

To keep the architecture clear and predictable:

- Page Objects **must not contain scenario logic**
- Flow decisions belong to Procedures
- Data is provided externally (Dataset)
- Application state is handled outside the UI layer

The Page Object should be limited to:

- Locating elements
- Performing actions
- Exposing simple and direct checks

## What Should NOT Be in a Page Object

A Page Object **must not**:

- Access databases
- Contain scenario-based conditional logic
- Know about Dataset, Script, or Suite
- Define or manipulate global application state

These responsibilities belong to other levels of the framework.

## Best Practices

- Create small, cohesive Page Objects
- A Page Object should represent a specific screen or component
- Avoid overly generic Page Objects
- Prefer descriptive and readable methods
- Name actions according to user-perceived behavior

## Next Step

After understanding the Page Object, the next concept is **Dataset**, responsible for providing execution data to scenarios.

➡️ Continue to **Dataset**.
