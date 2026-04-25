# Java Web Application CI/CD Pipeline

An automated end-to-end CI/CD workflow that demonstrates the integration of GitHub, Jenkins, Maven, and Apache Tomcat to deploy a live Java web application.

## 🚀 Project Overview

This project automates the lifecycle of a Java web application. Whenever code is pushed to the GitHub repository, Jenkins triggers a build process. Maven then compiles the code, runs tests, and packages it into a Web Application Archive (WAR) file. Finally, Jenkins deploys this WAR file to a remote Apache Tomcat server, making the application live.

[Image of Jenkins CI CD pipeline workflow]

## 🛠 Tech Stack

* **Version Control:** GitHub
* **CI/CD Tool:** Jenkins
* **Build Tool:** Maven
* **Artifact:** WAR (Web Application Archive)
* **Web Server:** Apache Tomcat 10
* **Environment:** Linux (Ubuntu/RHEL)

## 📋 Architecture

1.  **Developer** pushes code to the **GitHub** repository.
2.  **Jenkins** detects changes (via Webhooks or Poll SCM).
3.  **Jenkins** initiates the build process using **Maven**.
4.  **Maven** cleans, compiles, and packages the source code into `java-webapp.war`.
5.  **Jenkins** uses the 'Deploy to container' plugin to push the `.war` file to the **Tomcat** Manager.
6.  The application is accessible live at `http://<server-ip>:8081/java-webapp/`.

## ⚙️ Configuration Details

### 1. Maven Configuration in Jenkins
Jenkins is configured to use a specific Maven installation (e.g., version 3.9.15) to ensure build consistency.
- **Path:** Manage Jenkins > Tools > Maven installations.

### 2. Tomcat Setup
Tomcat is configured with the necessary manager roles in `tomcat-users.xml` to allow Jenkins to deploy applications remotely.
- **Manager App URL:** `http://<ip>:8081/manager/html`
- **Role required:** `manager-script` or `manager-gui`

<img width="1353" height="668" alt="Screenshot 2026-04-25 223705" src="https://github.com/user-attachments/assets/515dc9ba-0293-4284-a645-409de08a2b1f" />


## 🚀 Deployment Steps

1.  **Build:** Jenkins executes `mvn clean install`.
2.  **Packaging:** Maven generates the artifact in the `target/` directory.
3.  **Deployment:** Jenkins attempts to deploy the WAR file. If a previous version exists, it performs a fresh deployment.
4.  **Verification:** Access the application via the browser.

<img width="1349" height="353" alt="Screenshot 2026-04-26 000023" src="https://github.com/user-attachments/assets/73e842cc-125f-4f56-9609-e712fd931dd0" />


### Jenkins Build Success
The console output confirms the Maven build success and the subsequent deployment to the Tomcat container.

<img width="1343" height="675" alt="Screenshot 2026-04-26 001503" src="https://github.com/user-attachments/assets/2dfc4689-b6a8-42c8-a46f-3f265cac99eb" />


### Live Application
The final result showing the "Hello from DevOps CI/CD" message, confirming the pipeline is fully functional.

<img width="1361" height="372" alt="Screenshot 2026-04-26 001642" src="https://github.com/user-attachments/assets/4a7e8b74-ee2b-4969-acc0-95def196b9ae" />


## 📝 Conclusion
This pipeline reduces manual intervention, ensures faster release cycles, and maintains high code quality through automated builds and deployments.
