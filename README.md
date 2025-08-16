Run a Simple Java Maven Build Job in Jenkins
📌 Objective

Learn how to use Jenkins to build a simple Java application using Maven — your first step into CI/CD.

🛠️ Tools Required (All Free)

Jenkins (installed locally or via Docker)

Java JDK 8 or 11

Maven

Git (optional — can run from local folder)

📂 Deliverables

✅ A basic Java HelloWorld app (pom.xml included)

✅ Jenkins Freestyle job configured to build it

✅ Screenshot of successful build console output

🚀 Steps to Reproduce
1. Create a Java Maven Project
mvn archetype:generate -DgroupId=com.example -DartifactId=helloworld \
-DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
cd helloworld

2. Update the Java file

Edit src/main/java/com/example/App.java:

package com.example;

public class App {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins Maven Build!");
    }
}

3. Test Locally with Maven
mvn clean install


You should see:

BUILD SUCCESS

4. Run Jenkins

Start Jenkins:

docker run -p 8080:8080 -p 50000:50000 jenkins/jenkins:lts


Open http://localhost:8080

Install Maven Integration plugin

5. Create a Freestyle Job in Jenkins

New Item → Freestyle Project

Source Code Management → Git (or none if local)

Build Step → Invoke Maven → Goals:

clean install


Save & Build

6. Verify

Check Console Output → You should see:

[INFO] BUILD SUCCESS
