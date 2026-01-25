# Configuration Overview

This section describes how **Probato is configured**.

Probato uses **centralized configuration files** to control execution behavior, environment settings, and integrations.  
This approach keeps test code focused on behavior while configuration defines *how* and *where* tests run.

---

## Configuration philosophy

Probato follows three core configuration principles:

1. **Configuration over code**  
   Execution behavior should not be hardcoded.

2. **Single source of truth**  
   All execution-related settings are defined in one place.

3. **Explicit behavior**  
   Nothing is implicit or hidden.

---

## Configuration file

Probato is configured using a YAML file, typically located at:

```text
src/test/resources/configuration.yml
```

This file controls:

- execution mode
- browser behavior
- timeouts and retries
- evidence capture
- integrations (such as Probato Manager)

---

## Configuration scope

Configuration is global for a test execution and applies to:

- all Suites
- all Scripts
- all Procedures

Scenario-specific behavior should be modeled using **Concepts** (Dataset, Database), not configuration switches.

---

## Sections overview

The configuration file is divided into logical sections:

- **Project** — general project metadata
- **Execution** — execution strategy and lifecycle
- **Browser** — browser automation settings
- **Integrations** — external systems and services

Each section is documented in detail in the following pages.

---

## What comes next

Continue with:

➡️ **Project Configuration** — project-level settings  
➡️ **Browser Configuration** — browser execution options  
➡️ **Execution Settings** — execution behavior and lifecycle
