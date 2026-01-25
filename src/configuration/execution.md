# Execution Settings

This section describes how **test execution behavior** is configured in Probato.

Execution settings define *how* tests are executed, including parallelism, lifecycle behavior, and evidence collection.  
They do not change test structure or logic.

---

## Purpose of execution configuration

Execution configuration is responsible for:

- controlling execution flow
- enabling or disabling parallel execution
- managing test lifecycle behavior
- defining evidence capture strategy

This ensures predictable and repeatable executions across environments.

---

## Execution section

Execution settings are defined under the `execution` section of the configuration file.

Example:

```yaml
execution:
  parallel: false
  timeout: 30000
  retry:
    enabled: false
    attempts: 0
```

---

## Available properties

### parallel
Controls whether tests are executed in parallel.

- `true` — enables parallel execution
- `false` — executes tests sequentially

Parallel execution improves speed but may require:
- isolated test data
- isolated environments

---

### timeout
Defines the maximum execution time (in milliseconds) for a test.

If the timeout is exceeded:
- the test is interrupted
- execution is marked as failed

---

### retry
Controls automatic retry behavior for failed tests.

Properties:
- `enabled` — enables or disables retry
- `attempts` — number of retry attempts

Retry is useful for:
- unstable environments
- flaky external dependencies

It should not be used to hide real defects.

---

## Evidence capture

Probato supports automatic evidence capture during execution.

Evidence may include:
- screenshots
- execution logs
- browser recordings

Evidence settings are typically integrated with execution lifecycle and external systems such as **Probato Manager**.

---

## Lifecycle behavior

During execution, Probato manages the full lifecycle:

1. Configuration loading
2. Environment initialization
3. State preparation
4. Scenario execution
5. Evidence collection
6. Result consolidation

This lifecycle is automatic and requires no manual control.

---

## Best practices

- Start with sequential execution
- Enable parallelism only when tests are isolated
- Use retries sparingly
- Treat evidence as a diagnostic tool, not a success metric

---

## What comes next

With configuration completed, you can now:

- build complete test scenarios
- integrate with CI/CD pipelines
- explore advanced execution strategies

Continue with:

➡️ **Guides** — for complete end-to-end examples
