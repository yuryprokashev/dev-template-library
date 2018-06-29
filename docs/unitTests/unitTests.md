# Unit Tests
## Running Tests with JUnit 5
### Pre-requisites 
1. MacOS Sierra 10.12.6
2. IntelliJ IDEA Ultimate 2017.3
3. Homebrew 1.5.10

### Installing Homebrew
1. [Unistall Homebrew](https://docs.brew.sh/FAQ)
2. [Install Homebrew](https://brew.sh/)

### Installing and configuring Gradle 4.6
#### Installation
[Install Gradle locally using Homebrew](https://gradle.org/install/)

#### Basic build.gradle configuration for JUnit5
[Check here for full configuration](https://docs.gradle.org/current/userguide/java_plugin.html#using_junit5)

The following code enables JUnit Platform support in `build.gradle`:
```
test {
    useJUnitPlatform()
}
```
Add JUnit5 dependencies to `build.gradle`:
```
dependencies {
    testImplementation 'org.junit.jupiter:junit-jupiter-api:5.1.0'
    testRuntimeOnly 'org.junit.jupiter:junit-jupiter-engine:5.1.0'
}
```
Add test to `src/test/java/org/gradle/junitplatform/JupiterTest.java`
```java
package org.gradle.junitplatform;

import org.junit.jupiter.api.*;

public class JupiterTest {
    @Test
    public void ok() {
        System.out.println("Hello from JUnit Jupiter!");
    }
}
```

#### Configuring IntelliJ IDEA Project
In `Preferences/Build../Gradle`:
1. Select `Use local gradle discribution`
2. Put path, where Gradle has been installed by Homebrew: `/usr/local/Cellar/gradle/4.6/libexec`

[Check Preferences Screenshot](https://www.dropbox.com/s/kabts5dvt1yj7lh/Screenshot%202018-03-18%2020.15.27.png?dl=0)

#### Run JUnit 5 tests in IntelliJ IDEA using Gradle task
Run [Gradle Panel `test` task](https://www.dropbox.com/s/2snlzd0ziw6qzce/Screenshot%202018-03-18%2020.21.24.png?dl=0)

Sample output:
```
Testing started at 19:09 ...
19:09:58: Executing task 'test'...

:compileJava NO-SOURCE
:processResources NO-SOURCE
:classes UP-TO-DATE
:compileTestJava
:processTestResources NO-SOURCE
:testClasses
:test
Hello from JUnit Jupiter!
BUILD SUCCESSFUL in 15s
2 actionable tasks: 2 executed
19:10:14: Task execution finished 'test'.
```


