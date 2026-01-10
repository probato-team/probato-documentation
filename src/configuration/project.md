# Project Configuration

This section describes **project-level configuration** in Probato.

Project configuration defines metadata and global identifiers that help organize executions, reports, and integrations, without affecting test logic.

---

## Purpose of project configuration

Project configuration is used to:

- identify the test project
- group executions logically
- enrich reports and metrics
- support integrations such as Probato Manager

It does **not** control execution behavior or test flow.

---

## Project section

Project settings are defined under the `project` section of the configuration file.

Example:

```yaml
project:
  name: Probato Sample Project
  code: SAMPLE
  description: Sample project used to demonstrate Probato configuration
```

---

## Available properties

### name
Human-readable project name.

Used in:
- reports
- dashboards
- logs

---

### code
Short identifier for the project.

Used to:
- group executions
- identify results in integrations
- avoid ambiguity across environments

Recommended to be:
- short
- uppercase
- stable

---

### description
Optional project description.

Provides additional context about:
- the purpose of the project
- the scope of test coverage

---

## Best practices

- Keep project identifiers stable over time
- Avoid environment-specific values in project configuration
- Use meaningful names and codes
- Do not encode execution behavior in project settings

---

## What comes next

Continue with:

➡️ **Browser Configuration** — to control browser execution  
➡️ **Execution Settings** — to define execution lifecycle and behavior
