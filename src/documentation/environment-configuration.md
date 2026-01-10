# **Environment Setup**

Correctly configuring the development environment is the first step to fully leveraging the potential of **Probato**, a powerful test automation framework. This guide details the steps required to configure essential tools such as the JDK, Maven, and an IDE, ensuring an environment ready to create and execute automated tests.

## **Install the JDK**

The **Java Development Kit (JDK)** is required to compile and run the Java code used by **Probato**. Make sure to install version 11 or higher.

### Download the JDK

Access one of the links below to download the JDK:

* [Oracle JDK](https://www.oracle.com/java/technologies/javase-downloads.html)
* [OpenJDK](https://jdk.java.net/)
* [Adoptium](https://adoptium.net/)
* [Amazon Corretto](https://aws.amazon.com/corretto/)

### Configure Environment Variables

**On Windows**:

* Open "Edit system environment variables".
* Under **System Variables**, click **New**:
      * Name: `JAVA_HOME`
      * Value: `C:\dev\java\jdk-11`
* Edit the `Path` variable and add: `%JAVA_HOME%\bin`

**On Mac/Linux**:
      
* Add the following lines to `~/.bash_profile` or `~/.zshrc`:
```bash
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home
export PATH=$JAVA_HOME/bin:$PATH
```

### Validate the Installation
```bash
java --version
```
Expected output:
```plaintext
java version "11.0.X"
Java(TM) SE Runtime Environment (build 11.0.X)
Java HotSpot(TM) 64-Bit Server VM (build 11.0.X)
```
**NOTE:** If you see an output similar to the one above, the Java JDK has been installed successfully.

## **Install Maven**

Maven is used to manage project dependencies and automate build processes.

### Download and Install

Visit the official [Apache Maven](https://maven.apache.org/download.cgi) website, download the ZIP file, and extract it to `C:\dev\maven` (Windows) or `/usr/local/maven` (Mac/Linux), or another directory of your choice.

### Configure Environment Variables

**On Windows**:

* Add a new variable:
      * Name: `MAVEN_HOME`
      * Value: `C:\dev\maven`
* Include `%MAVEN_HOME%\bin` in the `Path`.

**On Mac/Linux**:

* Add to `~/.bash_profile` or `~/.zshrc`:
```bash
export MAVEN_HOME=/usr/local/maven
export PATH=$MAVEN_HOME/bin:$PATH
```

### Validate the Installation
```bash
mvn -version
```
Expected output:
```plaintext
Apache Maven 3.X.X
Maven home: /usr/local/maven
Java version: 11.0.X, vendor: Oracle Corporation
OS name: "mac os x", version: "10.15.7", arch: "x86_64"
```
**NOTE:** If you see an output similar to the one above, Maven has been installed successfully.

## **Choose an IDE**

An IDE (Integrated Development Environment) makes it easier to write, run, and debug Java code. Here are some popular options:

| **IDE** | **Main Advantage** | **Recommended Use** |
|-----|--------------------|-----------------|
| :simple-eclipseide:{ .eclipseide } Eclipse | Lightweight and free | For beginners |
| :simple-intellijidea:{ .intellijidea } IntelliJ | Advanced features | For advanced developers |
| :material-microsoft-visual-studio-code:{ .visual-studio-code } VS Code | Modern and extensible | For simple Java projects |

!!! note
    Choose the IDE that best suits your needs. Make sure to install the required plugins for Java support.

## **Final Checklist**

Before proceeding with project creation, make sure that:

- ✅ Java JDK installed and configured (`java --version` working).
- ✅ Maven installed and configured (`mvn -version` working).
- ✅ IDE installed and ready to use.

Your environment is set up! You are now ready to create projects with Probato.
