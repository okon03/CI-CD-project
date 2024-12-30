# CI/CD Pipeline Documentation

## Overview

This project demonstrates a complete CI/CD pipeline implemented using Jenkins. The pipeline automates the process from source code retrieval to deployment and monitoring in a Kubernetes environment. It also integrates code quality checks, artifact storage, and container image management.

## Pipeline Stages

The Jenkins pipeline consists of the following stages:

1. **Git Checkout**

   - Retrieves the source code from the GitHub repository.
   - Repository: [GitHub Repository](https://github.com/okon03/Devops_proj.git)

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

Monitoring is handled by Prometheus and Grafana, deployed in the Kubernetes cluster.

### Prometheus

- Collects metrics from the Kubernetes cluster and application pods.
- Configuration includes scraping endpoints for:
  - Kubernetes API
  - Application-specific metrics (if implemented).

### Grafana

- Visualizes metrics collected by Prometheus.
- Dashboards include:
  - Pod health and resource usage.
  - Application performance metrics.
  - Cluster-wide statistics.

## Tools and Technologies

The pipeline leverages the following tools:

- **Jenkins**: Orchestrates the CI/CD pipeline.
- **Maven**: Builds, tests, and packages the Java application.
- **SonarQube**: Ensures code quality through static analysis.
- **Nexus**: Stores build artifacts.
- **Docker**: Builds and manages container images.
- **Kubernetes**: Deploys and manages the application in a containerized environment.
- **Prometheus & Grafana**: Monitors and visualizes application and cluster metrics.
- **AWS**: Hosts the Kubernetes cluster on virtual machines.
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
└── monitoring/                  # Prometheus and Grafana configuration files
    ├── prometheus.yml
    └── grafana-dashboard.json
