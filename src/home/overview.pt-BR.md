# Overview

Probato is an **opinionated and declarative framework for functional test automation**, built on top of **JUnit 5**.

Its main goal is to provide **structure, predictability, and clarity** to automated test projects by clearly separating *what is being tested* from *how tests are executed*.

Instead of focusing on low-level test implementation details, Probato introduces a **conceptual model** that organizes tests into well-defined layers, allowing teams to scale automation with consistency and maintainability.

---

## What Probato is

Probato is:

- A **test orchestration framework**, not just a test runner
- Built for **end-to-end functional testing**
- Designed to be **explicit, structured, and opinionated**
- Fully integrated with the **JUnit 5 ecosystem**
- Focused on **observability and execution metrics**

Probato does not replace tools like Selenium or Playwright.  
Instead, it **organizes and orchestrates** how these tools are used within a test suite.

---

## Core idea

At the heart of Probato lies a simple principle:

> **Test code describes what should be tested.  
> The framework decides how execution happens.**

This principle drives all architectural decisions in Probato and results in:

- Declarative test definitions
- Centralized execution configuration
- Strong separation of responsibilities
- Predictable and repeatable test runs

---

## Conceptual structure

Probato structures automated tests using a clear hierarchy of concepts:

```
Suite
 └── Script
      └── Procedure
           └── Page Object
```

This structure is extended with first-class support for:

- **Dataset** — data-driven execution
- **Database** — declarative state management
- **Configuration** — environment and execution control
- **Manager** — metrics and result visualization

Each layer has a single, well-defined responsibility.

---

## Who Probato is for

Probato is primarily designed for:

- **QA Engineers** working with automated functional tests
- **Developers** responsible for test automation
- **Teams** seeking consistency across multiple automation projects

Execution results and metrics can also be consumed by non-technical stakeholders through the Probato Manager.

---

## What to read next

If you are new to Probato, start with:

1. **Concepts** — to understand the framework model
2. **Getting Started** — to run your first test
3. **Guides** — for complete examples and use cases

---

Probato favors **clarity over flexibility** and **structure over convention drift**.  
Understanding its conceptual model is the key to using it effectively.
