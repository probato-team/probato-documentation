# Java Library

The **Probato** Java library is the core of the end-to-end (E2E) functional test automation proposal.

It was designed to **centralize and organize best practices**, patterns, and utilities widely used in test automation, reducing repetitive decisions and the long-term maintenance cost of tests.

The library does not aim to be a definitive or closed framework, but rather a **structured foundation**, open to adaptation according to the context of each project.

---

## Library objectives

The main goal of the Probato library is to make functional test automation:

- Easier to start  
- More consistent over time  
- Easier to maintain and evolve  
- Less dependent on improvised solutions  

It seeks to reduce initial complexity without preventing advanced customizations when necessary.

---

## Adopted approach

The library does not reinvent established tools. On the contrary, it **centralizes and organizes** the use of solutions already widely adopted in the market, such as Selenium, adding:

- Well-defined design patterns  
- A Page Object–based structure  
- A simple, annotation-driven API  
- Code reuse  
- Minimal execution configuration  

The proposal is to standardize what is essential while maintaining flexibility where the context requires it.

---

## Key features

Among the features offered by the library, the following stand out:

- Execution of functional tests across multiple browsers  
- Simplified configuration of execution environments  
- Test data management  
- Execution of SQL scripts  
- Support for multiple databases  
- Automatic collection of execution context information  
- Generation of evidence such as screenshots and videos  

These features reflect common needs found in real-world automation projects.

---

## API and usage pattern

The library’s API was designed to be:

- Simple  
- Declarative  
- Focused on readability  

Test implementation is primarily based on:

- Annotations  
- Page Object classes  
- External configurations  

This approach reduces repetitive code and makes tests easier to understand, especially in teams with different maturity levels.

---

## Library scope

It is important to align expectations regarding the library’s scope:

- It **does not cover all possible automation scenarios**  
- It does not eliminate the need for local architectural decisions  
- It does not fully replace other libraries or specialized solutions  

The library provides a solid initial foundation that can be extended or adapted as needed.

---

## Standalone usage and integration

The Probato library can be used **independently**, without requiring the Web application.

When integrated with the Web application, it automatically sends execution data, evidence, and context information, enhancing quality analysis and metrics.

This integration is **optional**, allowing gradual adoption.

---

## Target audience

The library was designed to serve:

- Teams new to automation seeking standardization  
- Mature teams aiming to reduce operational effort  
- Projects that require consistency across different test suites  

It supports different maturity levels without imposing excessive rigidity.

---

## Library evolution

Technical decisions and adopted patterns are **not final**.

The evolution of the library depends directly on:

- Practical usage  
- Community feedback  
- Technical discussions  
- Improvement suggestions  

The proposal is to evolve incrementally and collaboratively.

➡ Previous section: **[First Steps](first-steps.md)** <br>
➡ Next section: **[Web Application](web-app.md)**
