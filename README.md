# dd4
BCSL657D Program 4
4. Practical Exercise: Build and Run a Java Application with Maven, Migrate the Same Application to Gradle.

Step 1: Creating a Maven Project

You can create a Maven project using the mvn command (or through your IDE, as mentioned earlier). But here, I’ll give you the essential pom.xml and Java code.

I’m Using Command Line:
To create a basic Maven project using the command line, you can use the following command:
mvn archetype:generate -DgroupId=com.example -DartifactId=maven-example -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
Step 2: Open The pom.xml File

You can manually navigate the project folder named call maven-example and open the file pom.xml and copy the below code and paste it then save it.
In case if you not getting project folder then type command in your cmd.
cd maven-example – is use to navigate the project folder.
notepad pom.xml – is use to open pom file in notepad.
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>maven-example</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
            <scope>test</scope>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
Step 3: Open Java Code (App.java) File

Open a file App.java inside the src/main/java/com/example/ directory.
After opening the  App.java copy the below code and paste it in that file then save it.
package com.example;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello, Maven");
        System.out.println("This is the simple realworld example....");

        int a = 5;
        int b = 10;
        System.out.println("Sum of " + a + " and " + b + " is " + sum(a, b));
    }

    public static int sum(int x, int y) {
        return x + y;
    }
}
Note: before building the project make sure you are in the project folder if not navigate the project folder type command in your command prompt cd maven-example.

Step 4: Run the Project

To build and run this project, follow these steps:

Open the terminal in the project directory and run the following command to build the project.
mvn clean install
Run the program with below command:
mvn exec:java -Dexec.mainClass="com.example.App"
output of cmd
Step 5: Migrate the Maven Project to Gradle

Initialize Gradle: Navigate to the project directory (gradle-example) and run:
gradle init
It will ask Found a Maven build. Generate a Gradle build from this? (default: yes) [yes, no]
Type Yes
Select build script DSL:
1: Kotlin
2: Groovy
Enter selection (default: Kotlin) [1..2]
Type 2
Generate build using new APIs and behavior (some features may change in the next minor release)? (default: no) [yes, no]
Type No
output of cmd
Navigate the project folder and open build.gradle file then add the below code and save it.
plugins {
    id 'java'
}

group = 'com.example'
version = '1.0-SNAPSHOT'

repositories {
    mavenCentral()
}

dependencies {
    testImplementation 'junit:junit:4.12'
}

task run(type: JavaExec) {
    main = 'com.example.App'
    classpath = sourceSets.main.runtimeClasspath
}
Step 6: Run the Gradle Project

Build the Project: In the project directory (gradle-example), run the below command to build the project:
gradlew build
cmd output
Run the Application: Once the build is successful, run the application using below command:
gradlew run
cmd output
Step 7: Verify the Migration

Compare the Output: Make sure that both the Maven and Gradle builds produce the same output:
Maven Output:
Hello, Maven
This is the simple realworld example....
Sum of 5 and 10 is 15
Gradle Output:
Hello, Maven
This is the simple realworld example....
Sum of 5 and 10 is 15
