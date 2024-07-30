# Django Web Application Deployment on Kubernetes Using Jenkins CI/CD

This project demonstrates the deployment of a Django web application on a Kubernetes cluster using a CI/CD pipeline in Jenkins, with integrated code quality analysis using SonarQube.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Architecture](#architecture)
- [Setup and Configuration](#setup-and-configuration)
  - [Jenkins Setup](#jenkins-setup)
  - [Kubernetes Setup](#kubernetes-setup)
  - [Django Application Setup](#django-application-setup)
  - [SonarQube Setup](#sonarqube-setup)
- [Deployment](#deployment)
- [Testing](#testing)
- [SonarQube Analysis](#sonarqube-analysis)
- [Troubleshooting](#troubleshooting)

## Introduction

This project automates the deployment of a Django web application using Jenkins for continuous integration and delivery, Kubernetes for container orchestration, and SonarQube for code quality analysis.

## Prerequisites

- Jenkins server with necessary plugins (Kubernetes, Docker, Git, SonarQube, etc.)
- Kubernetes cluster
- Docker installed on the Jenkins server
- Git repository for the Django application
- SonarQube server for code analysis

## Architecture

1. **Jenkins**: Automates the build, test, SonarQube analysis, and deployment process.
2. **Kubernetes**: Manages containerized applications in a clustered environment.
3. **Docker**: Containers for the Django application and other necessary services.
4. **SonarQube**: Analyzes the code for bugs, vulnerabilities, and code smells.

## Setup and Configuration

### Jenkins Setup

1. **Install Jenkins**: Follow the [official documentation](https://www.jenkins.io/doc/book/installing/) to install Jenkins.
2. **Install Plugins**: Install the following plugins:
   - Kubernetes Plugin
   - Docker Pipeline Plugin
   - Git Plugin
   - SonarQube Scanner Plugin
3. **Configure Jenkins**: 
   - Add Kubernetes cluster configuration.
   - Add Docker host configuration.
   - Configure SonarQube server in Jenkins.

### Kubernetes Setup

1. **Install Kubernetes**: Follow the [official documentation](https://kubernetes.io/docs/setup/) to set up a Kubernetes cluster.
2. **Create Namespace**: Create a namespace for the Django application:
   ```sh
   kubectl create namespace django-app

### Django Application Setup

1.  **Dockerize the Application**:
    -   Create a `Dockerfile` for the Django application.
    -   Build and push the Docker image to a container registry.
2.  **Kubernetes Manifests**:
    -   Create deployment and service YAML files for the Django application.

### SonarQube Setup

1.  **Install SonarQube**: Follow the official documentation to set up a SonarQube server.
2.  **Integrate SonarQube with Jenkins**:
    -   Configure the SonarQube Scanner in Jenkins.
    -   Add SonarQube analysis stage in the Jenkins pipeline.

## Deployment

1.  **Configure Jenkins Pipeline**:
    -   Create a Jenkins pipeline script (`Jenkinsfile`) in the root of your repository.
2.  **Run the Pipeline**:
    -   Trigger the pipeline in Jenkins to build, test, analyze code quality with SonarQube, and deploy the application to the Kubernetes cluster.

## Testing

-   Access the Django application using the Kubernetes service URL or ingress.
-   Verify that the application is running as expected.

## SonarQube Analysis

-   Analyze the code quality, bugs, vulnerabilities, and code smells using SonarQube.
-   Review the SonarQube dashboard for detailed analysis and metrics.

## Troubleshooting

-   Check Jenkins build logs for any errors.
-   Use `kubectl logs` to view logs from the Kubernetes pods.
-   Ensure all services and deployments in Kubernetes are running.
-   Review SonarQube logs and dashboard for analysis issues.

