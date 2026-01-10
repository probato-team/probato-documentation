# End-to-End Example

This guide demonstrates a **complete Probato test flow**, connecting all core concepts in a single, realistic example.

The objective is to show how Probato structures tests from high-level intent down to UI interaction.

---

## Scenario overview

We will validate a **user login flow** using the following scenario:

> A valid user logs into the system and is redirected to the dashboard.

This scenario will be modeled using:

- Suite — login functionality
- Script — valid login scenario
- Dataset — user credentials
- Database — initial user state
- Procedure — execution logic
- Page Object — UI interaction

---

## Project structure

A simplified project structure for this example:

```text
src/test/java/
├── suite/
│   └── LoginSuite.java
├── script/
│   └── ValidLoginScript.java
├── procedure/
│   └── LoginProcedure.java
├── page/
│   └── LoginPage.java
├── model/
│   └── LoginData.java
```

---

## Suite

The Suite represents the login functionality.

```java
@Suite
public class LoginSuite {
}
```

The Suite groups all login-related scenarios.

---

## Dataset

The Dataset defines valid login credentials.

```yaml
username: test_user
password: secret
```

Each dataset entry generates an independent execution.

---

## Script

The Script declares the scenario and associates the Dataset.

```java
@Script
@Dataset(LoginData.class)
public class ValidLoginScript {
}
```

No execution logic is defined here.

---

## Procedure

The Procedure contains the execution logic.

```java
public class LoginProcedure {

  public void execute(LoginData data) {
    LoginPage page = new LoginPage();
    page.login(data.getUsername(), data.getPassword());
  }
}
```

---

## Page Object

The Page Object encapsulates UI interaction.

```java
public class LoginPage {

  @Action("Login user")
  public void login(
      @Param("username") String username,
      @Param("password") String password) {
    // UI interaction
  }
}
```

---

## Execution flow

During execution, Probato performs the following steps:

1. Loads configuration
2. Applies database state
3. Discovers Suite and Script
4. Resolves Dataset
5. Executes Procedure
6. Collects evidence and metrics

---

## Key takeaways

- Each concept has a single responsibility
- Scenarios are declarative and readable
- Data and state are externalized
- Execution is predictable and observable

---

## What to explore next

After completing this guide, you can:

- extend scenarios with additional datasets
- add database state variations
- integrate execution results with Probato Manager
