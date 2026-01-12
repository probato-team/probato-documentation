# Architecture

**Probato** was designed with a modular and highly extensible architecture to support functional-level test automation in an efficient and scalable way. The architecture adopts modern software design concepts, such as the **Page Object Model (POM)** and **annotation-based dependency injection**, enabling the creation of reusable, maintainable, and evolvable test scripts.

This approach ensures clear separation of responsibilities, predictable execution, and flexibility to adapt to different automation scenarios.

## Architectural Principles

The **Probato** architecture is based on:

- modularity  
- isolation of responsibilities  
- component reuse  
- extensibility without impact on the core  
- transparent integration with external tools  

These principles guide all layers of the framework.

## Architectural Layers and Responsibility Isolation

The **Probato** architecture is composed of multiple layers, each with well-defined responsibilities, facilitating maintenance, evolution, and fault diagnosis.

### Interaction Layer (Page Object Model)

- Implements the **Page Object Model (POM)** pattern, encapsulating user interface interaction logic.
- Each page, screen, or component is represented as an object containing methods for possible interactions (clicks, data entry, validations, etc.).
- Promotes code reuse and simplifies maintenance when the application interface changes.

### Test Layer (Scripts and Procedures)

- Tests are organized into **scripts**, composed of actions divided into:
  - **Preconditions**
  - **Procedures**
  - **Postconditions**
- This separation helps isolate failures and precisely identify at which stage an error occurred.

### Data Injection Layer

- Enables flexible and dynamic use of input data.
- Supports data injection via CSV files.
- Provides planned future support for JSON, YAML, and databases through custom plugins.

### Persistence Layer and SQL Connectors

- Provides an integrated SQL executor capable of connecting to multiple databases.
- Allows defining database preconditions, dynamically changing states before tests, and restoring states after execution.

## Annotation-Based Dependency Injection

- Adopts a **dependency injection model via Java annotations**, promoting **Inversion of Control (IoC)**.
- Simplifies manual configuration by allowing required objects to be injected automatically.
- Promotes modularity, decoupling, and component reuse.

## JUnit 5–Based Execution Model

**Probato** integrates with the **JUnit 5** lifecycle, using dynamic tests and the `@TestFactory` annotation to generate test cases at runtime.

### Execution Lifecycle

![Probato Life Cycle](/assets/images/introduction/probato-life-cycle.png)

- **BeforeAll**  
  Loads extension points, configurations, and performs code and environment validations. It also creates JUnit 5 dynamic tests.

- **BeforeEach**  
  Loads required datasets and scripts and initiates scenario execution.

- **TestFactory**  
  Dynamically generates tests based on scripts, procedures, and Page Objects. Supports **data-driven testing**, enabling multiple executions with different datasets.

- **AfterEach**  
  Submits collected execution data to **Probato Manager** and stores images and videos in the configured storage.

- **AfterAll**  
  Calculates software quality metrics and notifies collaborators about execution completion.

## Multi-Browser Execution Support

- Built on top of **Selenium** and **Playwright** APIs, enabling automation across multiple browsers.
- Extensible support for additional browsers, operating systems, and execution contexts.

## Extensibility and Plugins

- The framework was designed to be **highly extensible**, allowing new features to be added without modifying the core.
- Plugin support includes:
  - new browser drivers  
  - additional input data formats  
  - new validation types  
  - custom SQL or NoSQL executors  

## Execution Management and Data Collection

During test execution, **Probato** captures and processes data such as:

- execution logs  
- screenshots  
- videos  
- executed steps  

This data is sent to an integrated web application that provides:

- centralized execution monitoring  
- detailed report generation  
- bug tracking  
- version-based analysis  

The Probato architecture allows integration with external test management and defect tracking tools, such as **TestLink** and **Mantis Bug Tracker**, through its extensibility points. These integrations can be implemented as plugins without requiring changes to the framework core.

## Advanced Configuration and Customization

**Probato** offers advanced configuration options for:

- defining **timeouts** and intervals between actions  
- adjusting image and video capture quality  
- controlling execution across multiple monitors  

## Notifications and Continuous Integration

- Automatic notifications are sent to collaborators after each test execution.
- Integration with **CI/CD** tools, such as **Jenkins**, enables full automation of test processes within the development lifecycle.
