# Overview

**An Open Source proposal for end-to-end (E2E) functional test automation.**

Probato is an initiative that aims to make the automation process **more viable, sustainable, and accessible** for teams and companies of any size.

It does not aim to be a definitive or complete solution, but rather an **initial foundation**, built from real-world needs, that evolves collaboratively with community participation.

Probato was created as a **structured starting point** to discuss, experiment with, and collectively evolve functional test automation.

---

## The problem Probato addresses

In practice, functional test automation often faces recurring challenges:

- Dispersed use of multiple libraries and utilities  
- Lack of standardization and code reuse  
- High maintenance cost of tests over time  
- Results and evidence scattered across reports, logs, and pipelines  
- Limited visibility of the value of automation beyond the technical team  

These factors make automation fragile, difficult to scale, and often unfeasible for most projects.

**Probato** was created to tackle these problems directly, offering a structured and integrated approach to E2E test automation.

---

## What Probato is

**Probato** is a proposal composed of two major components that work in a complementary way.

Together, they make it possible to clearly separate **test execution** from **quality analysis**, while maintaining organization, traceability, and visibility over time.

### Java Library

The Java library is the core of the automation. It centralizes and organizes the use of well-established market solutions, such as Selenium, while adding:

- Design patterns and best practices  
- Code reuse  
- A simple, annotation-driven API  
- A Page Object–based structure  
- Minimal configuration for execution across multiple browsers  

The goal is not to reinvent existing tools, but to **organize, standardize, and simplify** their use in real-world projects.

### Web Application

The Web application aims to centralize and provide visibility into the information collected during test executions.

It allows you to:

- Store results and evidence in a structured way  
- Maintain execution history over time  
- Visualize technical and functional data in a single place  
- Track quality metrics and indicators  

The way this data is collected, stored, and analyzed is **not definitive** and is open to evolution as new needs, contexts, and learnings emerge.

---

## Probato’s proposal

The core proposal of **Probato** is to function as a “recipe-style” approach to functional test automation:

- Simple to adopt in new projects  
- Easy to develop and evolve  
- Sustainable to maintain over time  
- Based on well-established best practices  

The goal is to reduce technical complexity and operational effort, allowing teams to focus on software quality rather than automation maintenance.

---

## Metrics and visibility

During test execution, the library collects a wide range of technical and functional information, which is automatically sent to the Web application.

This information makes it possible to:

- Analyze feature stability  
- Identify recurring failures and critical points  
- Evaluate quality evolution over time  
- Support technical and strategic decisions based on data  

Automation ceases to be merely a point-in-time validation mechanism and becomes a continuous source of information about product quality.

---

## Who it is for

**Probato** was designed to serve different contexts and maturity levels:

- Small teams looking to start automation in an organized way  
- Mature teams seeking standardization and visibility  
- Medium and large companies with multiple projects  
- Corporate environments with CI/CD pipelines  

Its flexible architecture allows gradual adoption without imposing abrupt changes to the existing ecosystem.

---

## Open Source and collaboration

**Probato** is an **Open Source** project that embraces its nature as an evolving proposal.

The project starts from an initial vision and technical decisions that are **not final**. The expectation is that the community will actively participate with opinions, suggestions, and contributions to complement, adjust, and mature the tool over time.

Community collaboration is considered an **essential and fundamental** factor for Probato to adapt to different contexts, realities, and needs.

---

## What Probato does not aim to be

To align expectations, it is important to clarify that Probato:

- Does not aim to be a definitive or complete framework  
- Does not replace the entire existing test automation ecosystem  
- Does not cover all possible scenarios, contexts, and needs  

It is an initial proposal, open to evolution and adaptation based on practical use and community contributions.

---

## Get started

- [Getting Started](first-steps.md)  
- [Java Library](library.md)  
- [Web Application](web-app.md)  
- [Example Project](examples.md)  
- [About the Project](about.md)
