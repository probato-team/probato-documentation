# Conceptual Architecture

This section describes the **conceptual architecture of Probato**.  
It explains how the framework is structured from a *mental and organizational* perspective, rather than focusing on low-level technical implementation details.

Probato was designed to make test automation **predictable, explicit, and scalable** by enforcing a clear separation of responsibilities.

---

## Architectural principle

Probato follows a simple but strict architectural rule:

> **Each layer has a single responsibility, and no layer skips another.**

This prevents:
- tight coupling
- hidden dependencies
- duplicated logic
- inconsistent test structures

---

## High-level architecture

At a conceptual level, Probato is organized into the following layers:

```
Suite
 ├── Script
 │    ├── Procedure
 │    │    └── Page Object
 │    └── Dataset
 ├── Database
 └── Configuration
```

Each layer answers a specific question during test execution.

---

## Layer responsibilities

### Suite
- Represents a business functionality or use case
- Groups related test scenarios
- Defines global preconditions and shared state
- Serves as the entry point for test discovery

**Question answered:**  
*What functionality is being validated?*

---

### Script
- Represents an individual test scenario
- Declares which procedures are executed
- Defines scenario-specific state and data
- Orchestrates execution without containing logic

**Question answered:**  
*Which scenario is executed?*

---

### Procedure
- Contains executable test logic
- Coordinates interactions with the application
- Receives resolved test data
- Performs validations

**Question answered:**  
*How is the scenario executed?*

---

### Page Object
- Encapsulates user interface interactions
- Isolates UI changes from test logic
- Provides semantic actions and parameters

**Question answered:**  
*How does the test interact with the system?*

---

### Dataset
- Provides external test data
- Enables native data-driven execution
- Generates multiple executions of the same scenario

**Question answered:**  
*With which data is the scenario executed?*

---

### Database
- Defines application state
- Prepares and isolates test environments
- Ensures deterministic test execution

**Question answered:**  
*In which state should the system be before execution?*

---

### Configuration
- Centralizes execution behavior
- Controls browsers, timeouts, recording, and execution modes
- Separates environment concerns from test code

**Question answered:**  
*Where and how should tests be executed?*

---

## Execution flow

A typical execution flow in Probato follows this sequence:

1. Configuration is loaded
2. Global state (Suite Database) is applied
3. Scripts are discovered
4. Scenario-specific state is applied
5. Datasets generate multiple executions
6. Procedures execute test logic
7. Page Objects interact with the system
8. Results and metrics are collected

This flow is fully automated and declarative.

---

## Observability and metrics

Probato treats observability as a core architectural concern.

During execution, the framework collects:
- execution metadata
- step descriptions
- input parameters
- evidences such as screenshots and recordings

These artifacts are consumed by **Probato Manager**, which provides visibility and insights into test quality.

---

## Architectural goals

The conceptual architecture of Probato is designed to:

- Enforce consistency across projects
- Reduce maintenance costs
- Improve test readability
- Enable scalable automation
- Support long-term evolution

---

## What comes next

To understand how these concepts translate into practical usage, continue with:

- **Features** — to see what Probato provides
- **Concepts** — for detailed explanations of each layer
- **Getting Started** — to run your first test
