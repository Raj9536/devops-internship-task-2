# 🚀 DevOps Internship Task 2 – CI/CD Pipeline with Jenkins and Docker

This project demonstrates the implementation of a complete **CI/CD pipeline** using **Jenkins** and **Docker** for a simple **Node.js** application. The goal is to automate the process of building, testing, and deploying the application whenever code is pushed to the GitHub repository.

---

## 📦 Project Overview

- **Technology Stack**: Node.js, Jenkins, Docker
- **CI/CD Tool**: Jenkins
- **Containerization**: Docker
- **Source Control**: Git & GitHub

The Jenkins pipeline is defined declaratively using a `Jenkinsfile` and leverages Docker to run builds in a containerized Node.js environment.

---

## 🗂️ Project Structure

![image](https://github.com/user-attachments/assets/60e71c46-66e7-486e-837b-d9119c032a2d)


---

## ⚙️ Jenkins Pipeline Stages

The CI/CD pipeline consists of the following stages:

| Stage   | Description                                |
|---------|--------------------------------------------|
| Build   | Installs all dependencies using `npm install` |
| Test    | Runs unit tests using `npm test` (can be customized) |
| Deploy  | Runs the app using `node index.js` (can be extended for production deployment) |

---

## 🚀 Running Jenkins in Docker (Windows PowerShell)

> Ensure that Docker Desktop is installed and running.

```powershell
docker stop jenkins
docker rm jenkins

docker run -d `
  -u root `
  --name jenkins `
  -p 8080:8080 -p 50000:50000 `
  -v jenkins_home:/var/jenkins_home `
  -v //var/run/docker.sock:/var/run/docker.sock `
  jenkins/jenkins:lts


🛠️ Jenkins Job Configuration
Open Jenkins at http://localhost:8080

Install the recommended plugins during setup

Create a new Pipeline project (e.g., devops-internship-task-2)

Choose Pipeline script from SCM

Configure:

SCM: Git

Repository URL: https://github.com/Raj9536/devops-internship-task-2.git

Branch: main

Click Save and then Build Now

📈 Pipeline Output
After a successful build:

Dependencies are installed

Tests are executed

The application is run inside a container

You will see logs for each stage in the Jenkins console output.
