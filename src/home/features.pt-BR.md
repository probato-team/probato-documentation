# Features

Probato provides a set of **focused and opinionated features** designed to bring structure, predictability, and observability to functional test automation.

Each feature directly derives from the framework’s conceptual model and addresses common pain points found in large-scale automation projects.

---

## Declarative test structure

Probato enforces a **declarative approach** to test definition.

Instead of embedding execution logic everywhere, tests are described using well-defined concepts such as:
- Suite
- Script
- Procedure
- Page Object

This results in:
- clearer test intent
- consistent structure across projects
- easier onboarding for new team members

---

## Strong separation of responsibilities

Each layer in Probato has a **single, clear responsibility**.

- Suites describe *what* is being validated
- Scripts describe *which scenario* is executed
- Procedures define *how execution happens*
- Page Objects encapsulate UI interaction
- Datasets provide test data
- Database defines application state

This separation reduces coupling and improves maintainability.

---

## Native data-driven execution

Probato treats **data-driven testing as a first-class feature**.

By associating Datasets directly with Scripts:
- the same scenario is executed multiple times
- no conditional logic is required in test code
- test logic remains clean and reusable

---

## Declarative state management

Application state is handled declaratively through Database definitions.

State preparation:
- is separated from execution logic
- can be applied globally (Suite) or per scenario (Script)
- improves test determinism and reproducibility

---

## Centralized configuration

Execution behavior is controlled through centralized configuration files.

Configuration allows teams to define:
- browsers and execution modes
- timeouts and execution settings
- evidence capture (screenshots, recordings)
- integration with external services

This keeps test code focused on behavior, not environment setup.

---

## Observability by design

Probato embeds **observability** into the execution lifecycle.

During test execution, the framework captures:
- execution metadata
- step descriptions
- input parameters
- evidences such as screenshots and videos

These artifacts are automatically forwarded to **Probato Manager**.

---

## JUnit 5 ecosystem integration

Probato is built on top of **JUnit 5**, ensuring:

- native CI/CD compatibility
- dynamic test execution
- parallel execution support
- compatibility with existing tooling

Teams can adopt Probato without changing their testing infrastructure.

---

## Scalable by architecture

Probato’s opinionated design enables:
- consistent automation across multiple projects
- reduced test maintenance cost
- predictable test execution behavior

The framework scales by **architecture**, not by convention.

---

## What to explore next

To learn how these features are applied in practice, continue with:

- **Concepts** — to understand each layer in detail
- **Getting Started** — to execute your first test
- **Guides** — for complete end-to-end examples
