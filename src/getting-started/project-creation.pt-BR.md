# Project Creation

This section guides you through the creation of a **basic Probato project**.

The goal is to set up a clean and minimal project structure that is ready to execute automated tests using Probato.

---

## Create a Maven project

Probato integrates naturally with standard Java projects.

Create a new Maven project using the default archetype:

```bash
mvn archetype:generate   -DarchetypeGroupId=org.apache.maven.archetypes   -DarchetypeArtifactId=maven-archetype-quickstart   -DarchetypeVersion=1.4
```

During project creation, provide:
- GroupId (e.g. `org.example`)
- ArtifactId (e.g. `probato-tests`)
- Version (default is fine)

---

## Project structure

After creation, organize your project using the following structure:

```text
src/
 └── test/
      └── java/
           ├── suite/
           ├── script/
           ├── procedure/
           ├── page/
           └── model/
```

This structure aligns with Probato concepts and keeps responsibilities clearly separated.

---

## Add Probato dependencies

Add the required Probato dependencies to your `pom.xml`.

At minimum, include:

```xml
<dependencies>
  <dependency>
    <groupId>org.probato</groupId>
    <artifactId>probato-core</artifactId>
    <version>${probato.version}</version>
  </dependency>
</dependencies>
```

Additional modules (browser, dataset, database, manager) can be added later as needed.

---

## Verify project setup

At this point, you should have:

- A valid Maven project
- A structured test directory
- Probato dependencies declared

No test code is required yet.

---

## Next step

Continue with:

➡️ **First Execution** — to configure and run your first Probato test
