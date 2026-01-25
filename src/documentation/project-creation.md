# Project Creation

This section describes how to create the **base structure of an automation project using Probato**. The goal is not only to generate a Maven project, but to establish a consistent organization that facilitates the application of the framework concepts.

At the end of this step, the project will be ready to receive configurations, Suites, Scripts, and other Probato components.

## Overview of the project structure

Probato is used **exclusively in the context of automated tests**. For this reason, all framework-related implementation resides under the `src/test` directory.

Project creation follows three main steps:

1. Maven project creation  
2. Package and directory structure adjustment  
3. Preparation of execution resources  

## Maven project creation

### Using terminal or command prompt

1. Open a terminal or command prompt.
2. Navigate to the directory where the project will be created.
3. Execute the command below:

```bash
mvn archetype:generate   -DgroupId=com.example.automation   -DartifactId=my-project-automation   -DarchetypeArtifactId=maven-archetype-quickstart   -DinteractiveMode=false
```

### Parameters used

- **groupId**  
  Organization group identifier, usually related to the domain.  
  Example: `com.example.automation`

- **artifactId**  
  Automation project name.  
  Example: `my-project-automation`

!!! note
    Project creation can also be performed directly through the IDE using Maven project wizards.

### Initial generated structure

After executing the command, Maven creates the following default structure:

```plaintext title="Default Maven structure"
my-project-automation/
├── src/
│   ├── main/
│   │   └── java/
│   │       └── com/example/automation/App.java
│   └── test/
│       └── java/
│           └── com/example/automation/AppTest.java
└── pom.xml
```

This structure is generic and must be adjusted for use with Probato.

## Package and directory structure adjustment

Probato does not use production code (`src/main`). All relevant code lives under `src/test`.

### Initial cleanup

1. Remove the `src/main/java` directory.
2. In `src/test/java`, remove the auto-generated class (`AppTest.java`).

### Creating the Probato structure

Create the following directories:

- `src/test/java/com/example/automation/`
- `src/test/resources/`

Organize the structure as shown below:

```plaintext title="Project structure with Probato"
my-project-automation/
├── src/
│   └── test/
│       ├── java/
│       │   └── com/example/automation/
│       │       ├── model/
│       │       ├── page/
│       │       └── usecase/
│       └── resources/
│           ├── dataset/
│           ├── sql/
│           └── configuration.yml
└── pom.xml
```

### Directory description

- **src/test/java**  
  Contains all automated test implementation:

    - Suites
    - Scripts
    - Procedures
    - Page Objects
    - Auxiliary models

- **src/test/resources**  
  Stores external resources used during execution:

    - Dataset files
    - SQL or NoSQL scripts
    - Probato configuration file

The `configuration.yml` file is the central configuration point of the framework.

!!! note
    The content and structure of `configuration.yml` will be detailed in the next section.

## Final checklist

Before moving forward, confirm that:

- ✅ The Maven project was created successfully
- ✅ The directory structure was adjusted
- ✅ The `src/main` directory was removed
- ✅ The `configuration.yml` file exists in `src/test/resources`

With the project created, the next step is to configure the framework behavior.

➡️ Next step: **Project Configuration**
