#### This Repo is for Cloud as Infrastructure As A Service (IAAS) 
#### Here is a breakdown of the staps taken to acheive the Deployment of a Java Gradle App on an Ubuntu Server and connect to it from The Browser.

Activities Done.

1. Install Ubuntu Server (I used the windows WSL)

2. Download Java Version 8 into it
 sudo apt install openjdk-8-jre-headless

3. Use a jar file for an application to build and start it on the server.
This is a Gradle project.

i. clone the project
git clone git@github.com:samuelcj/java-gradle-app.git

ii. Execute the gradle command in the root clone directory
.gradlew build

iii. Copy the built artifact from the local to the remote server using scp
scp build/libs/bootcamp-java-project-1.0-SNAPSHOT.jar samuelcj@<server IP>:/home/cloud-iaas/

iv. Then execute your java command to run the application on the remote.
java -jar bootcamp-java-project-1.0-SNAPSHOT.jar

v. Take Note of the port the server is running, for this application, the Tomcat is running on 8080

vi. confirm that you allow the port to be accessible from your firewall rule.

vii. Then check on your browser for the application:
<ip address>:8080.
for mine on my ubuntu wsl server i used: 127.0.0.1:8080 (representing my local host)

You should get the application UI showing you Team Members and their roles.

viii. You can decide to run the application in the background so you can use your terminal for other purposes 
java -jar bootcamp-java-project-1.0-SNAPSHOT.jar &

ix. To confirm the process is still running.
ps aux | grep java

x. You can also use the "netstat" utility to confim the running process. by running:
netstat -lpnt   =>> This will list the servers that have active internet connection.

xi. You can kill the process using
kill -9 <process id>

