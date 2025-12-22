# First Steps

This section presents a starting point for using **Probato**.

The goal is not to cover all possible scenarios, but to offer a **simple initial path**, allowing teams with different maturity levels to experiment with the proposal, validate concepts, and evolve gradually.

---

## Before you start

Probato is composed of two independent components:

* **Java Library**: responsible for executing automated tests  
* **Web Application**: responsible for centralizing results, evidence, and metrics  

It is possible to use only the Java library in isolation or integrate it with the Web application to gain greater visibility and quality history.

---

## Prerequisites

To use the Probato Java library, the following is recommended:

* Java 11 or later  
* Maven or Gradle  
* Basic knowledge of automated testing  
* Familiarity with Page Objects and functional tests  

To use the Web application:

* Docker  
* A modern web browser  

---

## First steps with the library

Adoption of the Probato library was designed to be incremental.

In general, the initial flow involves:

1. Adding the library dependency to the project  
2. Defining basic execution settings  
3. Creating Page Objects  
4. Implementing test scenarios using annotations  
5. Running the tests  

The library aims to reduce the amount of code required to structure functional tests, without hiding important concepts of the automation process.

---

## Initial configuration

The library’s initial configuration includes, among other aspects:

* Execution browsers  
* Target environment  
* Evidence directories  
* Database configurations  

These settings are kept within the code, where different configurations can be created for different environments, making it easier to switch executions between environments and pipelines.

---

## Test execution

After the basic configuration, tests can be executed locally or through continuous integration pipelines.

During execution, the library automatically collects information such as:

* Test results  
* Evidence  
* Environment data  
* Context information  

This data can be used locally or sent to the Web application.

---

## Integration with the Web application

Integration with the Web application is **optional**, but recommended for teams that want to:

* Centralize results  
* Maintain execution history  
* Visualize quality metrics  

When configured, the library automatically sends execution data to the Web application.

---

## Progressive usage

Probato was designed to allow progressive usage:

* Small projects can start with a few tests and minimal configuration  
* More mature teams can explore integrations, metrics, and history  

There is no need to adopt all features from the beginning.

---

## Sample project

In addition to the documentation, Probato includes a sample automation project that demonstrates, in practice, the use of the library by automating the Probato Web application itself. The Probato Web application is used as the target in the sample automation project.

[Sample](https://github.com/probato-team/probato-sample-e2e){:target="_blank"}

---

## Next steps

After the first tests, it is recommended to:

* Explore the [Java Library](library.md) documentation  
* Learn about the [Web Application](web-app.md)  
* Review the [Sample Project](examples.md)  

Probato is an evolving proposal, and practical usage is a fundamental part of this process.
