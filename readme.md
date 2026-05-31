# Dockerized Flask Application with GitHub Actions and Amazon ECR

## Overview

This project demonstrates a Continuous Integration (CI) pipeline using GitHub Actions, Docker, and Amazon Elastic Container Registry (ECR).

Whenever code is pushed to the main branch, GitHub Actions automatically builds a Docker image and publishes it to Amazon ECR, making it available for deployment to container orchestration platforms such as Amazon EKS.

## Architecture

```text
Developer
    │
    ▼
Git Push
    │
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ▼
Docker Build
    │
    ▼
Amazon ECR
```

## Project Objectives

* Containerize a Python Flask application
* Automate Docker image builds using GitHub Actions
* Securely authenticate with AWS using GitHub Secrets
* Push Docker images to Amazon ECR automatically
* Build the foundation for a future EKS and GitOps deployment pipeline

---

## Technology Stack

* Python Flask
* Docker
* GitHub Actions
* AWS ECR
* Git
* Linux

---

## Repository Structure

```text
.
├── app.py
├── requirements.txt
├── Dockerfile
├── README.md
└── .github
    └── workflows
        └── docker-build.yml
```

---

## Application

A simple Flask application exposing a web endpoint.

### Run Locally

Build image:

```bash
docker build -t docker-test-ecr .
```

Run container:

```bash
docker run -p 5000:5000 docker-test-ecr
```

Access application:

```text
http://localhost:5000
```

---

## CI Pipeline Workflow

The workflow is triggered automatically whenever code is pushed to the main branch.

### Pipeline Stages

1. Checkout source code
2. Configure AWS credentials
3. Authenticate with Amazon ECR
4. Build Docker image
5. Tag Docker image
6. Push Docker image to ECR

### Workflow Diagram

```text
Code Push
   │
   ▼
GitHub Actions
   │
   ▼
Docker Build
   │
   ▼
Image Tagging
   │
   ▼
Amazon ECR Login
   │
   ▼
Push Image
```

---

## GitHub Secrets

The following repository secrets are configured:

```text
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION
```

These credentials are consumed securely by GitHub Actions during workflow execution.

---

## Amazon ECR Repository

Docker images are pushed to:

```text
915370161276.dkr.ecr.us-east-1.amazonaws.com/docker-test-ecr
```

Images stored in ECR can later be consumed by Amazon EKS deployments.

---

## Key Learning Outcomes

Through this project, the following concepts were implemented and validated:

* Docker image creation
* Containerization best practices
* GitHub Actions workflow development
* CI pipeline automation
* AWS credential management
* Amazon ECR authentication
* Automated image publishing
* Infrastructure integration with cloud-native services

---

## Future Enhancements

Planned improvements include:

* Automated application testing
* Image vulnerability scanning
* Amazon EKS deployment
* Kubernetes manifests
* Ingress configuration
* ArgoCD integration
* GitOps workflow implementation
* Rolling deployments
* Monitoring and observability

---

## End Goal Architecture

```text
Developer
    │
    ▼
GitHub
    │
    ▼
GitHub Actions
    │
    ▼
Docker Build
    │
    ▼
Amazon ECR
    │
    ▼
Amazon EKS
    │
    ▼
ArgoCD
    │
    ▼
Production Deployment
```

## Author

Built as a hands-on DevOps learning project to gain practical experience with containerization, CI pipelines, AWS services, and cloud-native deployment workflows.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/020562d8-5ac7-4e14-8b3c-6501232a6366" />

