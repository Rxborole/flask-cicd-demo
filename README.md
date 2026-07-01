# Flask CI/CD Pipeline using Jenkins and GitHub Actions

## Project Overview

This project demonstrates a complete Continuous Integration and Continuous Deployment (CI/CD) pipeline for a simple Python Flask application using **Jenkins** and **GitHub Actions**.

The pipeline automates dependency installation, testing, building, and deployment based on GitHub events.

---

# Technologies Used

* Python 3.11
* Flask
* Pytest
* Jenkins
* GitHub Actions
* Git & GitHub
* Ubuntu 24.04/26.04
* AWS EC2

---

# Project Structure

```
flask-cicd-demo/
│
├── app.py
├── requirements.txt
├── test_app.py
├── Jenkinsfile
├── README.md
└── .github/
    └── workflows/
        └── ci-cd.yml
```

---

# Prerequisites

Before running this project, ensure the following software is installed:

* Python 3.11+
* pip
* Git
* Jenkins
* GitHub Account
* AWS EC2 Instance (for Jenkins)
* Pytest

Install Python dependencies:

```bash
pip install -r requirements.txt
```

---

# Running the Flask Application

Start the application:

```bash
python app.py
```

Open your browser:

```
http://localhost:5000
```

---

# Running Unit Tests

Execute the test cases:

```bash
pytest
```

---

# Jenkins CI/CD Pipeline

The Jenkins pipeline consists of the following stages:

### 1. Checkout

Downloads the latest source code from the GitHub repository.

### 2. Build

* Creates Python virtual environment
* Installs project dependencies

### 3. Test

Runs unit tests using **pytest**.

### 4. Deploy

Deploys the Flask application to the staging environment after successful testing.

### Pipeline Flow

```
GitHub
   │
   ▼
Jenkins
   │
   ▼
Checkout
   │
   ▼
Build
   │
   ▼
Test
   │
   ▼
Deploy
```

---

# GitHub Actions Workflow

The GitHub Actions workflow automates CI/CD based on GitHub events.

## Trigger Events

### Push to Main Branch

```
Test
↓

Build
```

---

### Push to Staging Branch

```
Test
↓

Build
↓

Deploy to Staging
```

---

### Publish Release

```
Test
↓

Build
↓

Deploy to Production
```

---

# GitHub Actions Workflow File

Location:

```
.github/workflows/ci-cd.yml
```

---

# GitHub Secrets

The following repository secrets are used for deployment.

| Secret Name       | Description                  |
| ----------------- | ---------------------------- |
| STAGING_SERVER_IP | Staging Server IP Address    |
| STAGING_USERNAME  | Staging Server Username      |
| STAGING_SSH_KEY   | SSH Private Key              |
| PROD_SERVER_IP    | Production Server IP Address |
| PROD_USERNAME     | Production Server Username   |
| PROD_SSH_KEY      | SSH Private Key              |

---

# Jenkins Configuration

Installed Plugins

* Git Plugin
* Pipeline Plugin
* GitHub Plugin
* Email Extension Plugin
* Credentials Plugin

---

# Email Notifications

Jenkins sends email notifications after every build.

* Build Success
* Build Failure

SMTP Server

```
smtp.gmail.com
```

Port

```
587
```

---

# GitHub Webhook

GitHub webhook is configured to trigger Jenkins automatically after every push to the **main** branch.

Webhook URL

```
http://<JENKINS_PUBLIC_IP>:8080/github-webhook/
```

---

# Repository Branches

* main
* staging

---

# Build Commands

Install Dependencies

```bash
pip install -r requirements.txt
```

Run Tests

```bash
pytest
```

Run Flask

```bash
python app.py
```

---

# CI/CD Workflow

```
Developer
     │
     ▼
Push Code
     │
     ▼
GitHub Repository
     │
     ├──────────────► Jenkins Pipeline
     │                   │
     │                   ▼
     │             Build → Test → Deploy
     │
     ▼
GitHub Actions
     │
     ▼
Build
     │
     ▼
Test
     │
     ├────────────► Staging Deployment
     │
     └────────────► Production Deployment
```

---

# Screenshots Included

* Jenkins Dashboard
* Jenkins Pipeline Execution
* Build Stage
* Test Stage
* Deploy Stage
* GitHub Actions Workflow
* Staging Deployment
* Production Deployment
* GitHub Secrets
* GitHub Release

---

# Repository

```
https://github.com/Rxborole/flask-cicd-demo
```

---

# Author

**Rupesh Borole**

Senior Software Engineer

AWS | Jenkins | GitHub Actions | Docker | Kubernetes | Terraform
