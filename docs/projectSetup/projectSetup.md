# Project Setup
## Pre-requisites
1. MacOS Sierra 10.12.6
2. IntelliJ IDEA Ultimate Edition 2017.3
3. Gradle 4.6 installed locally

## New IntelliJ IDEA project with Java 9 and Gradle
1. Create New Project in IntelliJ IDEA 
2. [Pick Gradle and 
Java 9 as Project SDK
](https://www.dropbox.com/s/bt66h4t83airnlx/Screenshot%202018-03-19%2006.11.46.png?dl=0)
3. [Enter GroupId = `me.edufun`
ArtifactId = `${Your project name}`
Version = `1.0-SNAPSHOT`
](https://www.dropbox.com/s/gw8fr4wqskuoxbh/Screenshot%202018-03-19%2006.14.12.png?dl=0)
4. [Select 'Use Gradle locally'
and point to location, where Gradle
has been installed by Homebrew
`/usr/local/Cellar/gradle/4.6/libexec`
](https://www.dropbox.com/s/hn6neh4mfz4z0ui/Screenshot%202018-03-19%2006.14.46.png?dl=0)
5. Choose project folder name and project location in your file system and finish the process.

## Configuring JUnit5 to run Unit Tests
[Check this article about Unit Tests](../unitTests/unitTests.md)

## Configuring Spring 5 Application
### Add Spring Boot 2 dependency to Gradle 
Add this to `build.gradle`.
```
buildscript {
    dependencies {
        classpath org.springframework.boot:spring-boot-gradle-plugin:2.0.0.RELEASE'
    }
}

apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'

bootJar {
    baseName = '${YOUR-PROJECT-NAME}
    version = '0.0.1'
}

dependencies {
    compile 'org.springframework.boot:spring-boot-starter-web'
}
```
### Configure Jetty instead of Tomcat
By default with `org.springframework.boot:spring-boot-starter-web`
you'll get `spring-boot-starter-tomcat`.

You don't want Tomcat. Jetty is your platform.

To change Tomcat to Jetty, changes you `build.gradle`
```
dependencies {
    compile("org.springframework.boot:spring-boot-starter-web") {
        exclude module: "spring-boot-starter-tomcat"
    }
    compile 'org.eclipse.jetty:jetty-webapp:9.+'
    compile 'org.eclipse.jetty:jetty-jsp:9.+'
}
```