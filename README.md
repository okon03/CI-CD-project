# CI/CD Pipeline Documentation

## Overview

This project demonstrates a complete CI/CD pipeline implemented using Jenkins. The pipeline automates the process from source code retrieval to deployment and monitoring in a Kubernetes environment. It also integrates code quality checks, artifact storage, and container image management.

## Pipeline Stages

The Jenkins pipeline consists of the following stages:

1. **Git Checkout**

   - Retrieves the source code from the GitHub repository.
   - Repository: [GitHub Repository](https://github.com/okon03/CI-CD-project.git)

2. **Compile**

   - Compiles the project using Maven.

3. **Test**

   - Runs unit tests with Maven.

4. **SonarQube Analysis**

   - Performs static code analysis using SonarQube to ensure code quality.

5. **Quality Gate**

   - Checks the code quality results from SonarQube.

6. **Build**

   - Packages the application into a deployable artifact using Maven.

7. **Publish to Nexus**

   - Deploys the build artifact to a Nexus repository.

8. **Build & Tag Docker Image**

   - Builds a Docker image for the application and tags it.

9. **Push Docker Image**

   - Pushes the Docker image to Docker Hub.

10. **Deploy to Kubernetes**

    - Deploys the application to a Kubernetes cluster using deployment and service configurations.

11. **Verify**

    - Verifies the deployment by checking Kubernetes pods and services.

12. **Slack Notifications**

    - Sends notifications to a Slack channel about the pipeline status.

## Monitoring

Prometheus with Blackbox Exporter was used to monitor the availability of the Jenkins instance and the Kubernetes application, with the collected data being sent to Grafana, where metric templates were utilized for visualizing system performance and availability.

## Tools and Technologies

The pipeline leverages the following tools:

- **Jenkins**: Orchestrates the CI/CD pipeline.
- **Maven**: Builds, tests, and packages the Java application.
- **SonarQube**: Ensures code quality through static analysis.
- **Nexus**: Stores build artifacts.
- **Docker**: Builds and manages container images.
- **Kubernetes**: Deploys and manages the application in a containerized environment.
- **Prometheus with blackbox Exporter & Grafana**: Monitors and visualizes application and cluster metrics.
- **AWS**: Hosts virtual machines running SonarQube, Nexus, Jenkins, Prometheus & Grafana, as well as Kubernetes master and worker nodes, with configurations for security groups and appropriate open ports.
- **Slack**: Sends notifications about pipeline events.

## Repository Structure

The repository is structured as follows:

```
Devops_proj/
├── Jenkinsfile                  # Jenkins pipeline definition
├── pom.xml                      # Maven build file
├── src/                         # Source code of the application
├── deployment-service.yaml      # Kubernetes deployment and service configuration
├── README.md                    # Documentation
├── prometheus.yml               # Prometheus configuration file
├── CI-CD-Project-Schema.png     # Project schema
├── sonar-project.properties     # SonarQube project configuration file
├── Dockerfile                   # Docker configuration file for building container image
