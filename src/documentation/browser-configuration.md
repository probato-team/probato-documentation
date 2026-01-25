# Browser Configuration

This section describes how to configure the execution of automated tests in different browsers using **Probato**. Multi-browser execution is a fundamental feature to validate application compatibility in real-world environments, ensuring that scenarios are executed consistently across the main browsers available on the market.

## Datasource configuration

The database connection configuration must be defined in the `configuration.yml` file.

```yaml title="configuration.yml"

datasources:

   probato:
      url: jdbc:h2:mem:testdb
      driver: org.h2.Driver
      username: sa
      password: password

```

## The role of browser configuration in Probato

In Probato, browsers are not defined in test code. They are configured exclusively through the configuration file, allowing the same set of tests to be executed across different browsers without any code changes.

Each configured browser generates an independent execution of all scenarios.

## Required dependencies

Browser support is enabled through specific Probato modules.

In the `pom.xml` file, add the dependencies corresponding to the browsers you want to use.

```xml title="pom.xml"
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
```

!!! note
    Only browsers with the corresponding dependency added can be used during execution.

## Minimum browser configuration

The minimum configuration requires at least one browser defined in the `configuration.yml` file.

```yaml title="configuration.yml"
execution:
  target:
    url: http://localhost:8099
    version: 0.0.0

browsers:
- type: CHROME
```

With this configuration, tests can already be executed successfully.

## Multi-browser execution

It is possible to define multiple browsers simultaneously. For each configured browser, Probato will execute the entire test suite again.

```yaml title="configuration.yml"
browsers:
- type: CHROME
- type: FIREFOX
- type: EDGE
```

!!! note
    The configured browsers must be installed on the execution machine.

## Window sizing and execution mode

By default, browsers are executed with a maximized window. However, it is possible to fully control window sizing and execution mode.

```yaml title="configuration.yml"
browsers:
- type: CHROME
  headless: false
  dimension:
    mode: FULLSCREEN

- type: FIREFOX
  headless: true
  dimension:
    mode: MAXIMIZED

- type: EDGE
  dimension:
    mode: CUSTOM
    width: 1256
    height: 1018
```

## Browser properties

| Property | Description |
|---------|-------------|
| browsers[].type | Browser type (CHROME, FIREFOX, EDGE) |
| browsers[].headless | Executes in headless mode |
| browsers[].dimension.mode | FULLSCREEN, MAXIMIZED or CUSTOM |
| browsers[].dimension.width | Window width (CUSTOM) |
| browsers[].dimension.height | Window height (CUSTOM) |

## Timeouts and execution intervals

Waiting times and action intervals are configured globally in the `execution.delay` block.

```yaml title="configuration.yml"
execution:
  delay:
    waitingTimeout: 5000
    actionInterval: 300
```

## Delay properties

| Property | Description |
|---------|-------------|
| execution.delay.waitingTimeout | Maximum wait time per action |
| execution.delay.actionInterval | Interval between actions |

## Final considerations

Browser configuration in Probato is declarative, extensible, and decoupled from test code.

This allows you to:

- reuse the same tests across different environments
- execute validations per browser
- change execution behavior without recompiling the project

➡️ Next step: **Suite Implementation**
