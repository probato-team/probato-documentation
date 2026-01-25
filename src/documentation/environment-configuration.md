# Environment Configuration

Correctly setting up the environment is the first step to using **Probato** effectively. This step ensures that all required tools are available to create, execute, and evolve automation test projects based on the framework.

This section focuses **exclusively on environment preparation**.  
No Probato concepts are introduced here — they are already covered in the *Concepts* section.

## Overview of the required environment

To work with Probato, you need:

- Java Development Kit (JDK) 11 or higher
- Apache Maven
- An IDE with Java support

These components form the execution foundation of the framework.

## Java Development Kit (JDK)

The **Java Development Kit (JDK)** is required to compile and run the Java code used by Probato.

The minimum recommended version is **Java 11**.

### Distribution options

You may use any Java 11+ compatible distribution, such as:

- [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html)
- [OpenJDK](https://jdk.java.net/)
- [Temurin](https://adoptium.net/)
- [Corretto](https://aws.amazon.com/pt/corretto/)

The choice of distribution does not affect Probato’s behavior.

### Environment variable configuration

#### Windows

1. Open **Edit system environment variables**
2. Under **System Variables**, click **New**:
   - Name: `JAVA_HOME`
   - Value: `C:\dev\java\jdk-11`
3. Edit the `Path` variable and add:
   ```
   %JAVA_HOME%\bin
   ```

#### Mac / Linux

Add the following lines to `~/.bash_profile` or `~/.zshrc`:

```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
```

### Installation validation

Run:

```bash
java --version
```

Expected output:

```plaintext
java version "11.0.X"
Java(TM) SE Runtime Environment (build 11.0.X)
Java HotSpot(TM) 64-Bit Server VM (build 11.0.X)
```

If the version is displayed correctly, the JDK is configured.

## Apache Maven

**Apache Maven** is used by Probato for:

- Dependency management
- Test execution
- Build automation

### Installation

Download Maven from the official website:

- https://maven.apache.org/download.cgi

Extract it to a directory of your choice, for example:

- Windows: `C:\dev\maven`
- Mac/Linux: `/usr/local/maven`

### Environment variable configuration

#### Windows

- Create the variable:
  - Name: `MAVEN_HOME`
  - Value: `C:\dev\maven`
- Add to `Path`:
  ```
  %MAVEN_HOME%\bin
  ```

#### Mac / Linux

Add to `~/.bash_profile` or `~/.zshrc`:

```bash
export MAVEN_HOME=/usr/local/maven
export PATH=$MAVEN_HOME/bin:$PATH
```

### Installation validation

Run:

```bash
mvn -version
```

Expected output:

```plaintext
Apache Maven 3.X.X
Maven home: /usr/local/maven
Java version: 11.0.X
```

If Maven responds correctly, the installation is complete.

## IDE (Integrated Development Environment)

An IDE simplifies writing, running, and debugging automated tests.

Commonly used IDEs with Probato include:

| IDE | Main advantage | Recommended usage |
|-----|---------------|------------------|
| :simple-eclipseide:{ .eclipseide } [Eclipse](https://www.eclipse.org/downloads/) | Lightweight and free | Beginners |
| :simple-intellijidea:{ .intellijidea } [IntelliJ IDEA](https://www.jetbrains.com/idea/download/) | Advanced features | Larger projects |
| :material-microsoft-visual-studio-code:{ .visual-studio-code } [Visual Studio Code](https://code.visualstudio.com/download) | Lightweight and extensible | Simple projects |

!!! note
    Regardless of the IDE you choose, make sure to install the necessary plugins for Java and Maven support.

## Final checklist

Before proceeding to project creation, verify that:

- ✅ Java is installed and accessible (`java --version`)
- ✅ Maven is installed and accessible (`mvn -version`)
- ✅ An IDE is installed and configured

With the environment ready, you can move on to creating your first Probato project.

➡️ Next step: **Project Creation**
