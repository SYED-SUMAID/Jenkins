# Jenkins Introduction with Architecture

## What is Jenkins?

Jenkins is an open-source automation server used to automate software development and deployment processes.

It is commonly used for:

- Continuous Integration (CI)
- Continuous Delivery/Deployment (CD)
- Building applications
- Running tests
- Building Docker images
- Deploying applications

---

## CI/CD

### Continuous Integration (CI)

CI automatically builds and tests code whenever developers push changes to a shared repository.

### Continuous Delivery/Deployment (CD)

CD automates the process of delivering or deploying the tested application.

Basic flow:

Developer → GitHub → Jenkins → Build → Test → Deploy

---

## Jenkins Architecture

Jenkins mainly follows a **Controller-Agent architecture**.

### Controller

The Jenkins Controller manages the Jenkins environment.

It is responsible for:

- Managing jobs and pipelines
- Scheduling builds
- Managing credentials
- Assigning tasks to agents
- Monitoring build results

### Agent

A Jenkins Agent performs the actual tasks assigned by the Controller.

An agent can:

- Pull source code
- Build applications
- Run tests
- Build Docker images
- Deploy applications

### Executor

An Executor is a slot that allows Jenkins to run a task.

For example:

- 1 executor → 1 task at a time
- 2 executors → 2 tasks at the same time

---

## Jenkins Architecture Flow

Developer  
↓  
GitHub  
↓  
Jenkins Controller  
↓  
Jenkins Agent  
↓  
Build → Test → Docker → Deploy

---

## Jenkins Pipeline

A Jenkins Pipeline defines the steps required to automate the CI/CD process.

Common stages:

1. Checkout
2. Build
3. Test
4. Docker Build
5. Docker Push
6. Deploy

---

## Jenkinsfile

A `Jenkinsfile` contains the pipeline configuration as code.

It is usually stored inside the GitHub repository.

Example project structure:

    project/
    ├── Dockerfile
    ├── Jenkinsfile
    └── src/

---

## Jenkins + GitHub

Jenkins can integrate with GitHub using webhooks.

Basic workflow:

Developer → Git Push → GitHub → Webhook → Jenkins → Pipeline

---

## Jenkins + Docker

Jenkins can automate Docker image creation and deployment.

Basic workflow:

GitHub  
↓  
Jenkins  
↓  
Docker Build  
↓  
Docker Image  
↓  
Docker Hub  
↓  
Deployment

---

## Jenkins Credentials

Jenkins provides secure credential management for sensitive information such as:

- GitHub tokens
- SSH keys
- Docker Hub credentials
- API tokens

Credentials should not be written directly inside a `Jenkinsfile`.

---

## Important Terms

| Term | Meaning |
|---|---|
| Jenkins | Automation server |
| Controller | Manages Jenkins |
| Agent | Executes tasks |
| Executor | Runs a task |
| Pipeline | CI/CD workflow |
| Jenkinsfile | Pipeline as code |
| Stage | Section of a pipeline |
| Webhook | Automatically triggers Jenkins |
| Credentials | Secure authentication information |

---

## Key Takeaway

Jenkins automates the software delivery process:

**Code → GitHub → Jenkins → Build → Test → Docker → Deploy**

## jenkins pipeline

A Jenkins Pipeline defines the steps required to automate the CI/CD process.

Common stages:

1. Checkout
2. Build
3. Test
4. Deploy

## Simple Jenkins Pipeline

A basic `Jenkinsfile` can look like this:

![alt text](<Screenshot From 2026-10-08 19-32-24.png>)