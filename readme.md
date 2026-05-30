# Dockerized Flask Application with GitHub Actions CI

## Overview

This project demonstrates a basic CI pipeline using GitHub Actions and Docker.

A simple Flask application is containerized using Docker. Whenever code is pushed to the main branch, GitHub Actions automatically triggers a workflow that builds the Docker image and validates that the application can be successfully containerized.

This project was built to gain hands-on experience with:

* Docker
* GitHub Actions
* Continuous Integration (CI)
* Containerized Application Development

---

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
GitHub Actions Workflow
    │
    ▼
Docker Image Build
    │
    ▼
Build Success / Failure
```

---

## Project Structure

```text
.
├── app.py
├── requirements.txt
├── Dockerfile
└── .github
    └── workflows
        └── docker-build.yml
```

---

## Application

### app.py

A simple Flask application exposing a single endpoint:

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "DevOps Project Running"

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
```

---

## Docker Configuration

### Build Docker Image

```bash
docker build -t flask-demo .
```

### Run Container

```bash
docker run -p 5000:5000 flask-demo
```

### Verify Application

Open:

```text
http://localhost:5000
```

Expected Output:

```text
DevOps Project Running
```

---

## GitHub Actions Workflow

The workflow is triggered automatically whenever code is pushed to the main branch.

### Workflow Steps

1. Checkout source code
2. Build Docker image
3. Verify build completion

### Workflow File

```yaml
name: Docker Build

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Code
      uses: actions/checkout@v4

    - name: Build Docker Image
      run: docker build -t flask-demo .
```

---

## CI Pipeline Flow

```text
Code Push
   │
   ▼
GitHub Actions Triggered
   │
   ▼
Checkout Repository
   │
   ▼
Build Docker Image
   │
   ▼
Pipeline Success
```

---

## Skills Demonstrated

* Git Version Control
* GitHub Actions
* CI Pipeline Creation
* Docker Image Build Process
* Containerization
* Linux Command Line
* DevOps Fundamentals

---

## Future Enhancements

* Add automated testing stage
* Push Docker image to Amazon ECR
* Deploy image to Amazon EKS
* Implement GitOps using ArgoCD
* Add monitoring and observability

---

## Learning Outcome

This project helped reinforce Docker fundamentals and introduced Continuous Integration using GitHub Actions. It serves as the foundation for building a complete CI/CD pipeline involving Amazon ECR, Amazon EKS, and ArgoCD.

