# Maven Profiles Example

An example maven project on how to use profiles to control how your project is configured based on various conditions.

### Project Prerequisites

- JDK 18
- Maven

### Table of Contents

- What are Profiles?
- How to Activate a Profile
- Manual Activated Profiles
- Environment Detection
  - JDK Version
  - Operating System (OS)
- Checking Active Profiles

### What are Profiles?

Maven profiles provide a method of being able to dynamically configure your maven projects based on the machine
environment the project is being run on.

For example, depending on which operating system (OS) your project is being run on, file paths of plugins may differ.

However, there are many other scenarios during development where profiles could come in extremely useful.

### How to Activate a Profile

### Manual Activated Profiles

```xml
...
<profiles>
  <!-- Profile Without Detection -->
  <profile>
    <id>without-detection</id>
  </profile>
</profiles>
...
```

### Environment Detection

#### JDK Version

```xml
...
<profiles>
  <!-- JDK Detection -->
  <!-- Single JDK Activation -->
  <profile>
    <id>jdk-18</id>
    <activation>
      <jdk>18</jdk>
    </activation>
  </profile>

  <!-- Multiple JDK Activation -->
  <profile>
    <id>jdk-17-11</id>
    <activation>
      <jdk>[17, 11]</jdk>
    </activation>
  </profile>
</profiles>
...
```

#### Operating System (OS)

```xml
...
<profiles>
  <!-- OS Detection -->
  <!-- MacOS Activation -->
  <profile>
    <id>macos</id>
    <activation>
      <os>
        <name>Mac OS X</name>
        <family>mac</family>
      </os>
    </activation>
  </profile>

  <!-- Linux Activation -->
  <profile>
    <id>linux</id>
    <activation>
      <os>
        <name>Linux</name>
        <family>unix</family>
      </os>
    </activation>
  </profile>

  <!-- Windows Activation -->
  <profile>
    <id>windows</id>
    <activation>
      <os>
        <family>windows</family>
      </os>
    </activation>
  </profile>
</profiles>
...
```

### Checking Active Profiles

To check what maven profiles are currently active in your project, simply run `mvn help:active-profiles` in the root
directory of your project and examine the output. 

An example output on a machine running **JDK 18** and **MacOS**.

```bash
The following profiles are active:

 - jdk-18 (source: dev.andrewjfei:maven-profiles-example:1.0-SNAPSHOT)
 - macos (source: dev.andrewjfei:maven-profiles-example:1.0-SNAPSHOT)
```
