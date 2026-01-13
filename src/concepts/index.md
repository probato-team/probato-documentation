# Concepts

This section presents the **fundamental concepts of Probato**.  
Before learning *how to use* the framework, it is essential to understand **how it thinks**.

Probato is not a generic framework. It is **opinionated and declarative**, which means it enforces a clear structure for organizing and executing automated tests, reducing ambiguity, excessive coupling, and variation between projects.

Understanding these concepts is essential to use the framework correctly and to fully leverage its capabilities.

## The core principle of Probato

Probato is built on a simple and intentional principle:

> **The code describes what should be tested.  
> The framework decides how to execute.**

This principle guides all architectural decisions in Probato and is reflected through:

- extensive use of declarative annotations  
- strict separation of responsibilities  
- centralized configuration outside the code  
- automatic orchestration of the execution lifecycle  

The goal is to allow the test author to focus on **test intent**, while the framework handles execution, instrumentation, and observability.

## Framework mental model

Probato organizes automated tests into **well-defined layers**, each with a clear and non-overlapping responsibility.

The complete conceptual flow is as follows:

``` title="Conceptual model"
@Suite
 ├── @SQL (global state / feature preconditions)
 ├── @NoSQL (global state / feature preconditions)
 └── @Script
      ├── @Dataset (execution data)
      ├── @SQL (scenario-specific state)
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

This model defines **how tests should be thought about**, not just how they are written.  
Each layer has a specific role, and none of them should assume responsibilities of another.

## Overview of structural concepts

The concepts below form the **structural core of Probato**.  
They define the official vocabulary and the mental model adopted by the framework.

### Suite

A **Suite** represents a **business functionality or use case** of the system.

It is responsible for:

- grouping related Scripts  
- defining global preconditions (for example, database state)  
- serving as the discovery entry point for JUnit 5  

The Suite answers the question:

> *What is being validated?*

### Script

A **Script** represents a **test scenario**.

It is purely declarative and contains no business logic.  
Its role is to describe:

- which data will be used  
- which procedures will be executed  
- which preconditions and postconditions apply to the scenario  

The Script answers the question:

> *Which scenario will be executed?*

### Procedure

A **Procedure** is where **executable logic** lives.

It can be implemented as:

- a simple method  
- or a dedicated class when reuse and organization are required  

A Procedure:

- receives already-resolved data  
- executes actions  
- delegates UI interactions to Page Objects  

It answers the question:

> *How is the scenario executed?*

### Page Object

A **Page Object** encapsulates interactions with the user interface.

In Probato:

- it follows the classic Page Object pattern  
- it has no knowledge of Script or Suite  
- it is semantically enriched through annotations  

Annotations such as `@Action` and `@Param` enable:

- traceability  
- richer log and report generation  
- improved execution observability  

The Page Object answers the question:

> *How do we interact with the system?*

### Dataset

A **Dataset** defines the **test data** used during execution.

It is:

- external to the code  
- declared at the Script level  
- responsible for enabling native *data-driven* execution  

Each Dataset entry may generate an independent execution of the same Script.

The Dataset answers the question:

> *With which data will the scenario be executed?*

### Database

The **Database** concept in Probato represents the **application state**.

SQL scripts can be executed:

- at the Suite level (global state)  
- at the Script level (scenario-specific state)  

This approach ensures that:

- state is not mixed with logic  
- tests are more predictable and reproducible  

The Database answers the question:

> *In which state must the system be before execution?*

## Cross-cutting concepts

In addition to structural concepts, Probato uses components that act **transversally** during execution.

### Configuration and execution

The framework relies on **centralized configuration** to define aspects such as:

- browsers  
- parallel execution  
- timeouts  
- evidence capture  
- integration with Probato Manager  

These definitions live outside the code, usually in YAML files, reinforcing the separation between **test intent** and **execution environment**.

### Probato Manager

**Probato Manager** is the component responsible for consuming the data generated during test execution.

It provides:

- metrics  
- reports  
- execution history  
- visibility for non-technical stakeholders  

The Manager does not execute tests — it **observes, consolidates, and presents results**.

## How to proceed from here

From this point forward, the recommended reading order is:

1. **Suite**  
2. **Script**  
3. **Procedure**  
4. **Page Object**  
5. **Dataset**  
6. **Database**  

This sequence follows the exact mental model of the framework.

## Final considerations

Probato does not aim to be generic or neutral.  
It was designed to impose **structure, predictability, and clarity** in automated test projects.

Understanding these concepts is essential before moving on to practical documentation and usage guides.
