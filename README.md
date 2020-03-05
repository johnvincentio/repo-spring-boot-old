

[Udemy Spring Boot Course](https://www.udemy.com/spring-boot-intro/learn/v4/t/lecture/3956862?start=0)

[course code](https://github.com/danvega/spring-boot-intro)

[Spring Boot Docs](http://docs.spring.io/spring-boot/docs/current/ref)

[Spring Boot API](http://docs.spring.io/spring-boot/docs/current/api)

[Spring IO Platform](http://spring.io/projects)

[Spring Tools](https://spring.io/tools)

[Getting Started Guides](http://spring.io/guides)

[Java SE Development Kit 8 Downloads](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

## Verify Running Latest Java

```
java -version
```

* System Preferences
* Java
* Update

Shows I am running the latest.

Ensure `Check for Updates Automatically` is Checked

## Install STS

[Spring Tools](https://spring.io/tools)

* Download STS4, macOS 64-bit
* Install

## Install Maven

[Maven](http://maven.apache.org/)

* Downloaded 3.6.0
* Copied to `/Users/⁨jv/⁨Desktop/⁨OtherTools⁩/apache-maven`

Set `M2_HOME`

```
M2_HOME=/Users/jv/Desktop/OtherTools/apache-maven
```

Check the version

```
mvn -v
```


## Install Ant

[Apache Ant](https://ant.apache.org)

* Download `apache-ant-1.10.5-bin.tar.gz`
* Download KEYS
* Download PGP `apache-ant-1.10.5-bin.tar.gz.asc`

```
gpg --import KEYS
gpg --verify apache-ant-1.10.5-bin.tar.gz.asc
```

```
gunzip apache-ant-1.10.5-bin.tar.gz
```

copy `apache-ant-1.10.5` to `/Users/jv/Desktop/OtherTools/apache-ant`

Set `ANT_HOME=/Users/jv/Desktop/OtherTools/apache-ant`

```
ant -v
```

## Install Tomcat

[Apache Tomcat](http://tomcat.apache.org/)

[Tomcat 9](https://tomcat.apache.org/download-90.cgi)

* Download `apache-tomcat-9.0.16.tar.gz`
* Download KEYS
* Download PGP `apache-tomcat-9.0.16.tar.gz.asc`

```
gpg --import KEYS
gpg --verify apache-tomcat-9.0.16.tar.gz.asc
```

```
gunzip apache-tomcat-9.0.16.tar.gz
```

copy `apache-tomcat-9.0.16` to `/Users/jv/Desktop/OtherTools/apache-tomcat`

In `.bash_profile`

```
alias start-tomcat=/Users/jv/Desktop/OtherTools/apache-tomcat/bin/startup.sh
alias stop-tomcat=/Users/jv/Desktop/OtherTools/apache-tomcat/bin/shutdown.sh
```

## Install Gradle

[Gradle](https://gradle.org/)

[Gradle Install](https://gradle.org/install/)

[Gradle Chearsheet](https://devhints.io/homebrew)

```
brew list
brew list --versions gradle
```

shows Gradle is already installed.

```
gradle -v
```

```
Gradle 2.11
```

## Install Spring Boot CLI

```
brew tap pivotal/tap
brew install springboot
```

```
brew list
```

Homebrew installs `spring` to `/usr/local/bin`

### Spring CLI

```
spring version
spring help run
```

## Simple Project

`repo-spring-boot/simple-1`

`app.groovy`

```
@RestController
public class HelloWorld {
	
	@RequestMapping("/")
	public String home() {
	"Hello World"
	}
}
```

```
spring run app.groovy
```

```
http://localhost:8080/
```

# Spring Initializr

Multiple methods

## Use Website

`start.spring.io`

* Maven Project
* Java
* 2.1.3
* com.example
* demo
* demo
* Jar

Generate Project

Downloads `demo.zip`

Unzip and copy to `simple-2`

## Use spring init

```
cd repo-spring-boot/simple-3
spring init -list
```

```
spring init -d=web my-app
```

```
tree .
```

## Configure Finder to use STS

`spring-tool-suite.workflow`

```
cd $1
"/Applications/SpringToolSuite4.app/Contents/MacOS/SpringToolSuite4" -data $1 -showLocation $1
```

## Use STS

Start `STS` from `repo-spring-boot/simple-4`

* File
* New
* Spring Starter Project

Uses `https://start.spring.ui`

Name: HelloSpringBoot

Next>

* Web
	* Web

Next >

### Run the Application

* Select Main Java file
* Run (top nav)
* Spring Boot App

Add `HomeController`

```
package com.example.demo;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class HomeController {
	
	@RequestMapping("/")
	public String home() {
		return "Hello, Spring Boot";
	}
}
```

and run the application

```
localhost:8080
```

will work

### Run with Maven

```
cd simple-4/HelloSpringBoot
mvn spring-boot:run
```

```
localhost:8080
```

Create Jar

```
mvn clean package
```

Run the Jar

```
cd target
java -jar {my-jar}.jar

localhost:8080
```

### Run with Gradle

* File
* New
* Spring Starter Project

Uses `https://start.spring.ui`

Name: HelloSpringBootGradle

Type: Gradle (Buildship 3.x)

Next>

* Web
	* Web

Next >

```
cd HelloSpringBootGradle/
./gradlew build
./gradlew bootRun
```

works the same as Maven

Notice Jar file in `build/libs`

## Create Executable Jars

Create a Jar

```
cd Boot/
spring jar my-app.jar hello.groovy
```

List the Jar

```
jar tf my-app.jar
```

Run the Jar

```
java -jar my-app.jar

localhost:8080
```

# Building Your First Real World Application

```
mkdir first-app
```

Start `STS` from `repo-spring-boot/first-app`

* File
* New
* Spring Starter Project

Uses `https://start.spring.ui`

Name: HelloSpringBoot

Next>

* Web
	* Web

Next >

Added 2 controllers.

```
mvn spring-boot:run
```

```
localhost:8080
```

Create Jar

```
mvn clean package
```

Run the Jar

```
cd target
java -jar {my-jar}.jar

localhost:8080
```

