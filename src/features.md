# Features

**Probato** provides a comprehensive set of features to structure, execute, observe, and evolve test automation projects in a consistent and scalable way.

The features below are organized according to their role in the automation lifecycle.

## Test structure and organization

### Simple and intuitive structure

**Probato** offers an organized and modular structure for test implementation, making component reuse and script maintenance easier. This allows teams to focus more on test logic than on implementation structure.

### Annotation-based object injection

The use of annotations simplifies test configuration, enabling clear and concise object injection without the need for additional implementations.

### Page Object Model (POM)

**Probato** follows the **Page Object Model** pattern, helping separate layers and organize code. This approach improves maintainability and readability of scripts, especially when working with frameworks such as Selenium.

### Test procedure organization

Tests are organized into three stages:

1. **Preconditions**
2. **Procedures**
3. **Postconditions**

This structure makes it easier to quickly identify the source of failures and understand whether errors originate from the target functionality, preparatory steps, or unmet postconditions.

### Intuitive test script creation

Test scripts can be created with code, descriptions, and weights based on the relevance and complexity of the functionality. This helps with prioritization and metric analysis to assess the quality of the tested software.

## Data and application state

### Implicit data loading and injection

Scripts can be executed with different data sets, enabling broad test coverage without code duplication. This feature improves efficiency and expands test coverage.

### SQL and NoSQL executors

Executors allow connections to multiple databases to modify the application state according to test preconditions. This provides flexibility when preparing test scenarios.

## Execution and control

### Timeout and interval configuration

**Probato** allows:

- Configuring _timeouts_ for wait times during test execution;
- Adjusting intervals between actions to optimize execution performance.

### Cross-browser execution

Support for running tests across multiple browsers, with options such as:

- Maximized, fullscreen, or custom window modes (specific dimensions);
- Selection of the execution monitor (primary or secondary).

## Observability and result analysis

### Execution data management

**Probato** includes a dedicated web application for:

- Managing execution data;
- Analyzing software quality;
- Creating bugs based on execution results;
- Viewing versioned execution history;
- Generating detailed reports with logs and coverage charts.

### Data capture during execution

During test execution, Probato collects and stores information such as:

- Test suites and scripts;
- Executed steps;
- Applied data;
- SQL scripts and NoSQL;
- Videos and screenshots.

Video quality can be configured to support detailed analysis.

### Execution notifications

The framework supports sending notifications to collaborators whenever new executions occur, keeping everyone informed about test status.

## Extensibility and integration

### Extensibility

**Probato** supports customization through plugins, including:

- Support for new browsers;
- Additional validations;
- Data input in new formats;
- Custom SQL or NoSQL executors;
- Openness for creating new features.

### CI/CD tool integration

The framework integrates easily with continuous integration systems such as:

- **Jenkins**
- **Travis CI**
- **GitLab CI**

This integration enables automated test execution on each commit or at strategic stages of development, ensuring continuous and agile validation.
