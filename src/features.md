# Features

**Probato** provides a comprehensive set of features to structure, execute, observe, and evolve test automation projects in a consistent and scalable way.

The features below are organized according to their role in the automation lifecycle.

## Test Structure and Organization

### Simple and Intuitive Structure

**Probato** offers an organized and modular structure for test implementation, making component reuse and script maintenance easier. This allows teams to focus more on test logic than on implementation structure.

### Annotation-Based Object Injection

The use of annotations simplifies test configuration, enabling clear and concise object injection without the need for additional implementations.

### Page Object Model (POM)

**Probato** follows the **Page Object Model** pattern, helping separate layers and organize code. This approach improves maintainability and readability of scripts, especially when working with frameworks such as Selenium.

### Test Procedure Organization

Tests are organized into three stages:

1. **Preconditions**
2. **Procedures**
3. **Postconditions**

This structure makes it easier to quickly identify the source of failures and understand whether errors originate from the target functionality, preparatory steps, or unmet postconditions.

### Intuitive Test Script Creation

Test scripts can be created with code, descriptions, and weights based on the relevance and complexity of the functionality. This helps with prioritization and metric analysis to assess the quality of the tested software.

## Data and Application State

### Implicit Data Loading and Injection

Scripts can be executed with different data sets, enabling broad test coverage without code duplication. This feature improves efficiency and expands test coverage.

### SQL and NoSQL Executors

Executors allow connections to multiple databases to modify the application state according to test preconditions. This provides flexibility when preparing test scenarios.

## Execution and Control

### Timeout and Interval Configuration

**Probato** allows:

- configuring _timeouts_ for wait times during test execution;
- adjusting intervals between actions to optimize execution performance.

### Cross-Browser Execution

Support for running tests across multiple browsers, with options such as:

- maximized, normal, or custom window modes (specific dimensions);
- selection of the execution monitor (primary or secondary).

## Observability and Result Analysis

### Execution Data Management

**Probato** includes a dedicated web application for:

- managing execution data;
- analyzing software quality;
- creating bugs based on execution results;
- viewing versioned execution history;
- generating detailed reports with logs and coverage charts.

### Data Capture During Execution

During test execution, Probato collects and stores information such as:

- test suites and scripts;
- executed steps;
- applied data;
- SQL scripts;
- videos and screenshots.

Video quality can be configured to support detailed analysis.

### Execution Notifications

The framework supports sending notifications to collaborators whenever new executions occur, keeping everyone informed about test status.

## Extensibility and Integration

### Extensibility

**Probato** supports customization through plugins, including:

- support for new browsers;
- additional validations;
- data input in new formats;
- custom SQL or NoSQL executors;
- openness for creating new features.

### CI/CD Tool Integration

The framework integrates easily with continuous integration systems such as:

- **Jenkins**
- **Travis CI**
- **GitLab CI**

This integration enables automated test execution on each commit or at strategic stages of development, ensuring continuous and agile validation.
