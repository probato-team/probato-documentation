# First Execution

This section walks you through the **first execution of a Probato test**.

The goal is to validate that:
- the project is correctly configured
- the environment is ready
- Probato is able to discover and execute tests

This first execution focuses on **structure and flow**, not complex validations.

---

## Minimal configuration

Before running tests, create a basic configuration file.

Create the file:

```text
src/test/resources/configuration.yml
```

With the following minimal content:

```yaml
execution:
  parallel: false

browser:
  name: chrome
  headless: true
```

This configuration is enough to run a simple test.

---

## Create a minimal Suite

Create a Suite class to serve as the entry point for execution.

```java
package suite;

import org.probato.annotations.Suite;

@Suite
public class SampleSuite {
}
```

At this stage, the Suite does not need to reference any Scripts.

---

## Run the tests

Execute the following Maven command:

```bash
mvn test
```

During execution, Probato will:

1. Load the configuration
2. Discover the Suite
3. Initialize the browser
4. Execute the test lifecycle
5. Report results to the console

---

## Expected result

A successful execution should:

- start the browser in headless mode
- complete without errors
- report execution results in the console

No test failures are expected at this stage.

---

## Troubleshooting

If execution fails, verify:

- Java and Maven versions
- Browser installation
- Configuration file location
- Probato dependencies in `pom.xml`

---

## What comes next

Once your first execution succeeds, you are ready to:

- define Scripts and Procedures
- use Datasets and Database
- enable observability with Probato Manager

Continue exploring:

➡️ **Concepts** — to deepen your understanding  
➡️ **Guides** — for complete end-to-end examples
