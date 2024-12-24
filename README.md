# Cloud Infrastructure as a Service (IaaS)

This repository contains resources and steps to deploy a Java Gradle application on an Ubuntu server and access it via a browser.

## Deployment Steps

### 1. Install Ubuntu Server
- Install Ubuntu Server. For this example, Windows Subsystem for Linux (WSL) was used.

### 2. Install Java 8
Run the following command to install Java 8 on the server:
```bash
sudo apt install openjdk-8-jre-headless
```

### 3. Deploy the Java Gradle Application

#### Step 1: Clone the Project
Clone the repository containing the Java Gradle application:
```bash
git clone git@github.com:samuelcj/java-gradle-app.git
```

#### Step 2: Build the Application
Navigate to the cloned project directory and build the application using Gradle:
```bash
./gradlew build
```

#### Step 3: Transfer the Built Artifact to the Server
Use the `scp` command to copy the built JAR file to the remote server:
```bash
scp build/libs/bootcamp-java-project-1.0-SNAPSHOT.jar samuelcj@<server-IP>:/home/cloud-iaas/
```

#### Step 4: Run the Application
Log in to the server and execute the JAR file:
```bash
java -jar bootcamp-java-project-1.0-SNAPSHOT.jar
```

#### Step 5: Verify the Application
- Note the port the server is running on (default is 8080 for Tomcat).
- Ensure the firewall allows access to the port.
- Access the application in your browser using the server's IP and port, e.g., `http://<server-IP>:8080`.

For WSL, access via localhost:
```
http://127.0.0.1:8080
```
You should see the application UI displaying team members and their roles.

#### Step 6: Run the Application in the Background
To free your terminal for other tasks, run the application in the background:
```bash
java -jar bootcamp-java-project-1.0-SNAPSHOT.jar &
```

#### Step 7: Confirm the Application is Running
Check if the process is still running:
```bash
ps aux | grep java
```
Alternatively, use `netstat` to list active internet connections:
```bash
netstat -lpnt
```

#### Step 8: Stop the Application
To terminate the application, use the `kill` command:
```bash
kill -9 <process-ID>
```

---

## Key Notes
- Ensure proper firewall rules are configured to allow traffic to the application port.
- Monitor server performance to optimize resource usage.

# Infrastructure as a Service (IaaS)
This guide demonstrates the setup of a basic IaaS environment for deploying a Java application.


