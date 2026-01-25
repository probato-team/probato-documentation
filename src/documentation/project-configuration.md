# Project Configuration

This section describes how to configure a Maven project to use **Probato**. It defines both the **artifacts required for the build** and the **framework execution behavior**.

The goal of this step is to prepare the project to run automated tests in a predictable, declarative, and extensible way.

## The role of configuration in Probato

In Probato, configuration is explicitly separated from test code.

While the code describes **what will be tested**, configuration defines:

- How tests will be executed
- Which browsers will be used
- How evidences will be captured
- Which integrations will be enabled

This separation avoids conditional logic in code and allows changing project behavior without recompilation.

## Build Configuration (Maven)

Probato is distributed in a **modular** way. Each framework capability is enabled through Maven dependencies.

### Core Probato dependencies

Open the `pom.xml` file located at the project root and add the required dependencies.

```xml title="pom.xml"
<project 
    xmlns="http://maven.apache.org/POM/4.0.0" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example.automation</groupId>
    <artifactId>my-project-automation</artifactId>
    <version>1.0.0</version>

    <properties>
        <probato.version>0.1.0</probato.version>
        <selenium.version>4.33.0</selenium.version>
        <playwright.version>1.57.0</playwright.version>
        <postgresql.version>42.7.3</postgresql.version>
    </properties>

    <dependencies>

        <!-- Probato Core -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-core</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Browsers -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-browser-chrome</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-browser-firefox</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-browser-edge</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Datasets -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-datasets-csv</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Database -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-database-sql</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- Record -->
        <dependency>
            <groupId>org.probato</groupId>
            <artifactId>probato-record</artifactId>
            <version>${probato.version}</version>
            <scope>test</scope>
        </dependency>

        <!-- UI executors -->
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>${selenium.version}</version>
        </dependency>

        <dependency>
            <groupId>com.microsoft.playwright</groupId>
            <artifactId>playwright</artifactId>
            <version>${playwright.version}</version>
        </dependency>

        <!-- Database driver -->
        <dependency>
            <groupId>org.postgresql</groupId>
            <artifactId>postgresql</artifactId>
            <version>${postgresql.version}</version>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>3.0.0-M7</version>
                <configuration>
                    <includes>
                        <include>**/*.java</include>
                    </includes>
                </configuration>
            </plugin>
        </plugins>
    </build>

</project>
```

## Probato configuration file

Framework execution behavior is defined in:

```
src/test/resources/configuration.yml
```

This file centralizes all test execution settings.

### Configuration example

```yaml title="configuration.yml"
execution:
  engine: SELENIUM

  target:
    url: http://localhost:8099
    version: 0.0.0

  delay:
    waitingTimeout: 5000
    actionInterval: 500

  video:
    enabled: true
    frameRate: 1000
    quality: MEDIUM

  manager:
    submit: true
    url: http://localhost:8080
    token: [TOKEN]

browsers:
- type: CHROME
  headless: false
  dimension:
    mode: FULLSCREEN

datasources:
  probato:
    url: jdbc:postgresql://localhost:5444/probato
    driver: org.postgresql.Driver
    username: root
    password: root
```

## Available configuration properties

### Execution

| Property | Description |
|---------|-------------|
| execution.engine | Execution engine (SELENIUM or PLAYWRIGHT) |
| execution.target.url | Target application URL |
| execution.target.version | Target application version |
| execution.delay.waitingTimeout | Maximum wait time |
| execution.delay.actionInterval | Interval between actions |
| execution.video.enabled | Enables video recording |
| execution.video.frameRate | Frame rate |
| execution.video.quality | Video quality |
| execution.manager.submit | Sends data to Probato Manager |
| execution.manager.url | Manager URL |
| execution.manager.token | Authentication token |

### Browsers

| Property | Description |
|---------|-------------|
| browsers[].type | Browser type |
| browsers[].headless | Headless mode |
| browsers[].dimension.mode | FULLSCREEN, MAXIMIZED or CUSTOM |
| browsers[].dimension.width | Width (CUSTOM) |
| browsers[].dimension.height | Height (CUSTOM) |

### Datasources

| Property | Description |
|---------|-------------|
| datasources.*.url | Connection URL |
| datasources.*.driver | JDBC driver |
| datasources.*.username | Username |
| datasources.*.password | Password |

## Final checklist

- ✅ Dependencies configured in `pom.xml`
- ✅ `configuration.yml` file created
- ✅ Properties adjusted for the environment

➡️ Next step: **Browser Configuration**
