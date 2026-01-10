# Environment Setup

This section describes the **minimum environment setup** required to run Probato.

The goal is to ensure your system is ready to execute tests without introducing unnecessary configuration complexity.

---

## Java

Probato requires **Java JDK 17 or later**.

Make sure Java is installed and available in your system path:

```bash
java -version
```

If Java is not installed, download it from a trusted distribution such as:
- Eclipse Temurin
- Oracle JDK

---

## Maven

Probato uses **Apache Maven** for project management and execution.

Required version:
- Maven 3.8 or later

Verify your installation:

```bash
mvn -version
```

---

## Browser

Probato executes functional tests using browser automation.

At least one of the following browsers must be installed:

- Google Chrome
- Mozilla Firefox

Browser drivers are managed automatically by the framework.

---

## Operating system

Probato is platform-independent and can run on:

- Linux
- macOS
- Windows

No OS-specific configuration is required.

---

## Verification checklist

Before proceeding, ensure that:

- Java is installed and accessible
- Maven is installed and accessible
- A supported browser is installed

Once these requirements are met, you are ready to create your first Probato project.

---

## Next step

Continue with:

➡️ **Project Creation** — to create a basic Probato project structure
