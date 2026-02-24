# **Example**

This section presents official projects that demonstrate the use of
**Probato** in real-world automation scenarios. The examples were
structured to serve as a practical reference for architecture,
organization, and recommended best practices.

------------------------------------------------------------------------

# **Probato Manager Automation**

The **Probato Manager Automation** project is a complete example of
automating the **Probato Manager** application, demonstrating the
modular structure proposed by the framework.

🔗 [**Official
repository**](https://github.com/probato-team/probato-manager-automation)

------------------------------------------------------------------------

## **Project Objective**

This project demonstrates:

-   Implementation of **Suite**
-   Organization of **Scripts**
-   Separation of responsibilities using **Procedures**
-   Application of the **Page Object** pattern
-   Use of **Dataset (CSV)**
-   Execution of **SQL Scripts** as preconditions
-   Multi-browser execution
-   Configuration via `configuration.yml`

It serves as a reference model for teams that want to structure their
automation projects using Probato.

------------------------------------------------------------------------

## **Project Structure**

The structure adopted in the example follows the recommended pattern:

``` plaintext
probato-manager-automation/
├── src/
│   └── test/
│       ├── java/
│       │   └── org.probato.manager.automation/
│       │       ├── model/
│       │       ├── page/
│       │       └── usecase/
│       └── resources/
│           ├── dataset/
│           ├── sql/
│           └── configuration.yml
└── pom.xml
```

### **Folder Description**

-   `model/` → Data mapping classes (Datamodel)
-   `page/` → Page Object implementations
-   `usecase/` → Suites, Scripts, and Procedures organized by
    functionality
-   `dataset/` → CSV files containing test data
-   `sql/` → Database preparation scripts
-   `configuration.yml` → Central execution configuration

------------------------------------------------------------------------

## **Simplified Example**

### Suite

``` java
@Suite(
  code = "UC01",
  name = "Perform login",
  description = "Allow user to login")
class UC01_PerformLogin implements TestSuite {

  @TestCase
  private UC01TC01_PerformLoginSuccessfully uc01tc01;
}
```

------------------------------------------------------------------------

### Script

``` java
@Script(
  code = "UC01TC01",
  name = "Perform login successfully",
  description = "Validate successful login")
public class UC01TC01_PerformLoginSuccessfully {

  @Page
  private LoginPage loginPage;

  @Procedure
  private void procedure(LoginModel model) {
    loginPage.checkPage();
    loginPage.fillEmail(model.getEmail());
    loginPage.fillPassword(model.getPassword());
    loginPage.pressAccessButton();
  }
}
```

------------------------------------------------------------------------

## **Demonstrated Best Practices**

This project highlights fundamental principles of Probato:

-   Clear separation between structure and execution logic
-   Business-oriented organization (Use Case → Script → Procedure)
-   Reusability through Page Objects
-   Isolation and repeatability using SQL and Dataset
-   Centralized configuration

------------------------------------------------------------------------

## **When to Use This Example**

Recommended for:

-   Teams starting with Probato
-   Projects that require modular organization
-   Automation with database integration
-   Multi-browser implementation
-   Architectural reference for new projects

------------------------------------------------------------------------

## **How to Run**

1.  Clone the repository:

``` bash
git clone https://github.com/probato-team/probato-manager-automation
```

2.  Adjust the `configuration.yml` according to your environment.

3.  Run via Maven:

``` bash
mvn test
```

------------------------------------------------------------------------

# **Contributions**

If you would like to contribute additional examples:

-   Fork the repository
-   Submit a Pull Request
-   Propose new reference scenarios
-   Provide CI/CD integrations

The evolution of examples is part of the growth of the Probato
ecosystem.
