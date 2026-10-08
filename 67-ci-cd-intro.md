# CI/CD

## Overview

**CI/CD** stands for **Continuous Integration and Continuous Delivery/Deployment**. It is a software development and delivery practice that automates the process of integrating code changes, validating them, preparing releases, and deploying applications to target environments.

CI/CD enables development and operations teams to deliver software more frequently, reliably, and consistently. Instead of relying on manual steps, teams use automated pipelines to move code through a series of controlled stages.

    Developer Changes Code
            │
            ▼
       Source Control
            │
            ▼
     Continuous Integration
            │
            ├── Build
            ├── Unit Tests
            ├── Code Quality Checks
            └── Security Scans
            │
            ▼
       Release Preparation
            │
            ├── Continuous Delivery
            │       └── Manual Approval
            │
            └── Continuous Deployment
                    └── Automatic Deployment
            │
            ▼
       Target Environment

A typical CI/CD workflow can be summarized as:

    Code → Build → Test → Validate → Release → Deploy → Monitor

---

## Why CI/CD Is Important

Without CI/CD, software delivery often depends on manual processes. These processes can be slow, inconsistent, and difficult to repeat. CI/CD introduces automation and standardization into the software development lifecycle.

CI/CD helps teams:

- Deliver software faster and more frequently
- Detect defects early in the development process
- Reduce repetitive manual work
- Improve code quality and reliability
- Make deployments more predictable
- Reduce the risk of human error
- Maintain consistent development, testing, and production environments
- Create a repeatable and auditable delivery process
- Support faster feedback between developers, testers, and operations teams

---

## CI/CD Terminology

| Term | Meaning |
| --- | --- |
| **Continuous Integration** | The practice of frequently merging code changes into a shared repository and automatically validating them through builds and tests. |
| **Continuous Delivery** | The practice of automatically preparing validated code for release while usually requiring manual approval before production deployment. |
| **Continuous Deployment** | The practice of automatically deploying validated code to production without requiring manual approval. |
| **Pipeline** | An automated workflow that moves code through stages such as build, test, security scanning, release, and deployment. |
| **Build** | The process of compiling source code, installing dependencies, packaging the application, or creating a deployable artifact. |
| **Artifact** | A versioned output produced by the build process, such as a package, binary, container image, or deployment bundle. |
| **Environment** | A location where the application runs, such as development, testing, staging, or production. |
| **Deployment** | The process of installing and running an application in a target environment. |
| **Rollback** | The process of returning an application to a previous stable version after a failed or problematic deployment. |
| **Approval Gate** | A manual or automated checkpoint that must be passed before the pipeline can continue. |

---

## Continuous Integration

### Definition

**Continuous Integration**, commonly called **CI**, is the practice of frequently integrating code changes into a shared source-code repository.

Whenever a developer pushes code or creates a pull request, the CI pipeline automatically performs validation activities such as:

- Compiling or building the application
- Running unit tests
- Running integration tests
- Checking code formatting
- Performing static code analysis
- Scanning for security vulnerabilities
- Verifying dependencies
- Creating a deployable artifact

The main purpose of CI is to identify problems as early as possible.

### Continuous Integration Flow

    Developer Writes Code
            │
            ▼
    Commit or Pull Request
            │
            ▼
    Source Code Repository
            │
            ▼
    CI Pipeline Starts
            │
            ├── Restore Dependencies
            ├── Build Application
            ├── Run Unit Tests
            ├── Run Integration Tests
            ├── Perform Code Quality Checks
            └── Run Security Scans
            │
            ▼
    Validation Result
            │
            ├── Failed → Developer Fixes the Issue
            │
            └── Passed → Code Can Continue to the Next Stage

### Benefits of Continuous Integration

| Benefit | Description |
| --- | --- |
| **Early defect detection** | Problems are identified shortly after code is committed. |
| **Smaller changes** | Frequent integration reduces the size and complexity of changes. |
| **Faster feedback** | Developers quickly learn whether their changes are safe to merge. |
| **Improved collaboration** | Teams work against a shared and continuously validated codebase. |
| **Reduced integration risk** | Frequent merges reduce large, difficult-to-resolve conflicts. |
| **Improved code quality** | Automated tests and analysis run consistently for every change. |

---

## Continuous Delivery

### Definition

**Continuous Delivery** is the practice of automatically building, testing, validating, and preparing software for release.

In Continuous Delivery, the application is always maintained in a **releasable state**. The pipeline completes all required automated checks and produces a deployable artifact. However, deployment to production usually requires manual approval or a release decision.

### Continuous Delivery Flow

    Code Change
        │
        ▼
    Build
        │
        ▼
    Automated Tests
        │
        ▼
    Security and Quality Checks
        │
        ▼
    Create Versioned Artifact
        │
        ▼
    Deploy to Testing or Staging
        │
        ▼
    Manual Approval
        │
        ▼
    Production Deployment

The key idea is:

> The software is always ready to be deployed, but a person or business process decides when the production release should occur.

### When Continuous Delivery Is Useful

Continuous Delivery is commonly used when:

- Production releases require business approval
- Regulatory or compliance controls are required
- Releases are scheduled for specific times
- Additional manual testing is needed
- The organization wants control over production release timing
- The application requires coordination with other systems or teams

---

## Continuous Deployment

### Definition

**Continuous Deployment** extends Continuous Delivery by automatically deploying every change that successfully passes the pipeline.

There is no manual production approval in the normal workflow. Once the code passes all required automated checks, it is automatically released to production.

### Continuous Deployment Flow

    Code Change
        │
        ▼
    Build
        │
        ▼
    Automated Tests
        │
        ▼
    Security and Quality Checks
        │
        ▼
    Create Versioned Artifact
        │
        ▼
    Deploy to Testing or Staging
        │
        ▼
    Automated Validation
        │
        ▼
    Automatic Production Deployment
        │
        ▼
    Monitoring and Feedback

The key idea is:

> If the change passes all required automated checks, it is automatically deployed to production.

### When Continuous Deployment Is Useful

Continuous Deployment is commonly used when:

- Automated test coverage is strong
- The application can be deployed safely and frequently
- Fast delivery is important
- The organization has reliable monitoring and alerting
- Rollback or recovery procedures are well established
- The team uses feature flags, canary releases, or blue-green deployments

---

## Continuous Delivery vs. Continuous Deployment

The main difference is whether production deployment requires manual approval.

| Capability | Continuous Integration | Continuous Delivery | Continuous Deployment |
| --- | --- | --- | --- |
| Code is frequently integrated | Yes | Yes | Yes |
| Application is automatically built | Yes | Yes | Yes |
| Automated tests are executed | Yes | Yes | Yes |
| Code quality checks are performed | Usually | Usually | Usually |
| Security checks are performed | Recommended | Recommended | Recommended |
| Deployable artifact is created | Sometimes | Yes | Yes |
| Application is prepared for release | No | Yes | Yes |
| Manual production approval is required | Not applicable | Usually | No |
| Production deployment is automatic | No | No | Yes |
| Requires strong monitoring | Recommended | Recommended | Essential |
| Requires rollback capability | Recommended | Recommended | Essential |

### Simple Comparison

| Aspect | Continuous Delivery | Continuous Deployment |
| --- | --- | --- |
| Production readiness | Code is automatically prepared for production | Code is automatically prepared and deployed |
| Production release | Usually requires manual approval | Happens automatically after successful validation |
| Release control | Human-controlled | Pipeline-controlled |
| Release frequency | Frequent, but scheduled or approved | Potentially every successful change |
| Risk management | Uses approval gates and controlled releases | Uses automation, monitoring, feature flags, and rollback |
| Best suited for | Regulated, controlled, or approval-based environments | Fast-moving teams with mature automation |

### Easy Way to Remember

    Continuous Delivery   = Always ready to deploy
    Continuous Deployment = Automatically deployed

---

## Complete CI/CD Pipeline

A complete CI/CD pipeline usually contains several stages. The exact stages may vary depending on the programming language, application architecture, organization, and deployment platform.

    Source Code
        │
        ▼
    Trigger Pipeline
        │
        ▼
    Install Dependencies
        │
        ▼
    Build Application
        │
        ▼
    Run Unit Tests
        │
        ▼
    Run Integration Tests
        │
        ▼
    Perform Code Quality Checks
        │
        ▼
    Perform Security Scans
        │
        ▼
    Package Application
        │
        ▼
    Store Artifact
        │
        ▼
    Deploy to Development
        │
        ▼
    Deploy to Test
        │
        ▼
    Deploy to Staging
        │
        ▼
    Acceptance and Smoke Tests
        │
        ├── Continuous Delivery
        │       └── Manual Approval → Production
        │
        └── Continuous Deployment
                └── Automatic Deployment → Production
        │
        ▼
    Monitor Application

---

## Common CI/CD Pipeline Stages

| Stage | Purpose | Typical Activities |
| --- | --- | --- |
| **Source** | Detect a code change | Commit, pull request, merge, or tag |
| **Dependency Installation** | Prepare required libraries and tools | Install packages and restore dependencies |
| **Build** | Create a usable application output | Compile code, bundle files, or build a container image |
| **Unit Testing** | Validate individual components | Test functions, classes, and modules |
| **Integration Testing** | Validate interactions between components | Test APIs, databases, services, and queues |
| **Code Quality** | Maintain coding standards | Linting, formatting, static analysis, and complexity checks |
| **Security Scanning** | Identify security risks | Dependency scanning, secret detection, and vulnerability analysis |
| **Packaging** | Create a deployable output | Generate packages, binaries, archives, or container images |
| **Artifact Storage** | Store versioned build outputs | Upload artifacts to a repository or registry |
| **Deployment** | Install the application in an environment | Deploy to development, testing, staging, or production |
| **Validation** | Confirm that the deployment works | Smoke tests, acceptance tests, and health checks |
| **Monitoring** | Observe application behavior | Logs, metrics, traces, alerts, and dashboards |
| **Rollback** | Recover from a failed release | Restore a previous version or redirect traffic |

---

## CI/CD Environments

CI/CD pipelines commonly use multiple environments to validate changes progressively.

    Development
         │
         ▼
    Testing
         │
         ▼
    Staging
         │
         ▼
    Production

| Environment | Purpose | Typical Users |
| --- | --- | --- |
| **Development** | Used for active development and early testing | Developers |
| **Testing** | Used for automated and manual validation | Developers and testers |
| **Staging** | Provides a production-like environment for final verification | Developers, testers, and operations teams |
| **Production** | Serves real users and business workloads | Customers and end users |

A common promotion model is:

    Build Once → Test the Same Artifact → Promote Across Environments

This approach reduces inconsistencies because the exact artifact tested in earlier environments is promoted to later environments.

---

## CI/CD Pipeline Triggers

A pipeline can start for different reasons.

| Trigger | Description |
| --- | --- |
| **Code Commit** | Starts the pipeline when code is pushed to a repository. |
| **Pull Request** | Validates changes before they are merged into a shared branch. |
| **Branch Merge** | Runs after changes are merged into a target branch. |
| **Tag or Release** | Starts a release pipeline for a specific version. |
| **Scheduled Run** | Executes at a defined time, such as nightly or weekly. |
| **Manual Trigger** | Allows an authorized user to start the pipeline. |
| **External Event** | Starts the pipeline through an API, webhook, or another system. |

---

## Deployment Strategies

CI/CD pipelines can use different deployment strategies to reduce risk.

| Strategy | Description | Advantages | Considerations |
| --- | --- | --- | --- |
| **Rolling Deployment** | Replaces application instances gradually. | Reduces downtime and resource requirements. | Old and new versions may run at the same time. |
| **Blue-Green Deployment** | Maintains two environments and switches traffic between them. | Fast rollback and minimal downtime. | Requires additional infrastructure. |
| **Canary Deployment** | Releases the change to a small percentage of users first. | Limits the impact of a failure. | Requires traffic control and monitoring. |
| **Recreate Deployment** | Stops the old version before starting the new version. | Simple to implement. | May cause downtime. |
| **Feature Flag Release** | Deploys code while controlling feature visibility separately. | Separates deployment from feature release. | Requires feature-flag management and cleanup. |

---

## Quality and Security Controls

A professional CI/CD pipeline should validate more than whether the application builds successfully.

| Control | Purpose |
| --- | --- |
| **Unit Tests** | Verify individual functions and components. |
| **Integration Tests** | Verify communication between application components and external services. |
| **End-to-End Tests** | Validate complete user workflows. |
| **Smoke Tests** | Confirm that the most important application functions work after deployment. |
| **Regression Tests** | Ensure that existing functionality has not been broken. |
| **Static Code Analysis** | Identify code defects, maintainability issues, and coding standard violations. |
| **Dependency Scanning** | Detect vulnerable third-party libraries. |
| **Secret Scanning** | Prevent passwords, tokens, and keys from being committed to source control. |
| **Container Scanning** | Identify vulnerabilities in container images. |
| **Infrastructure Validation** | Verify infrastructure configuration before deployment. |
| **Approval Gates** | Require authorization before sensitive stages. |
| **Policy Checks** | Enforce organizational, security, and compliance requirements. |

---

## Monitoring and Feedback

CI/CD does not end when an application is deployed. Monitoring is required to confirm that the release is healthy and to provide feedback for future improvements.

Important monitoring areas include:

| Monitoring Area | Examples |
| --- | --- |
| **Application Performance** | Response time, throughput, and error rate |
| **Infrastructure Health** | CPU, memory, disk, and network usage |
| **Availability** | Uptime, health checks, and service status |
| **Logs** | Application events, warnings, and errors |
| **Metrics** | Business and technical measurements |
| **Traces** | Request flow across distributed services |
| **User Experience** | Page load time, failed requests, and user behavior |
| **Deployment Health** | Failed deployments, rollback frequency, and release success rate |

A typical feedback loop is:

    Deploy
      │
      ▼
    Monitor
      │
      ▼
    Detect Issues
      │
      ├── Healthy → Continue Delivery
      │
      └── Unhealthy → Alert, Investigate, and Roll Back

---

## CI/CD Best Practices

| Best Practice | Description |
| --- | --- |
| **Commit small changes frequently** | Smaller changes are easier to review, test, and troubleshoot. |
| **Automate repetitive tasks** | Reduce manual work and improve consistency. |
| **Keep pipelines fast** | Fast feedback encourages developers to use the pipeline regularly. |
| **Test at multiple levels** | Combine unit, integration, acceptance, and end-to-end testing. |
| **Build once and promote the same artifact** | Prevent differences between environments. |
| **Secure the pipeline** | Protect credentials, secrets, agents, repositories, and deployment permissions. |
| **Use version control for configuration** | Store application and infrastructure configuration as code. |
| **Make deployments repeatable** | Ensure the same process can be executed consistently. |
| **Use approval gates where appropriate** | Add control for production, regulated, or high-risk changes. |
| **Implement rollback procedures** | Prepare a reliable recovery process before a failure occurs. |
| **Monitor every deployment** | Confirm that the application remains healthy after release. |
| **Measure pipeline performance** | Track duration, failure rate, recovery time, and deployment frequency. |
| **Review and improve continuously** | Use pipeline results and incidents to improve the delivery process. |

---

## CI/CD Metrics

Teams can use metrics to evaluate the effectiveness of their CI/CD process.

| Metric | Description |
| --- | --- |
| **Deployment Frequency** | How often changes are successfully deployed. |
| **Lead Time for Changes** | The time between committing a change and deploying it. |
| **Change Failure Rate** | The percentage of deployments that cause failures or require remediation. |
| **Mean Time to Recovery** | The average time required to restore service after a failure. |
| **Pipeline Success Rate** | The percentage of pipeline runs that complete successfully. |
| **Pipeline Duration** | The time required for a pipeline to complete. |
| **Rollback Frequency** | How often deployments must be reverted. |
| **Test Pass Rate** | The percentage of automated tests that pass. |

These metrics help teams identify bottlenecks, improve reliability, and measure delivery performance.

---

## Example CI/CD Decision Guide

| Question | Recommended Approach |
| --- | --- |
| Do you need frequent automated validation of code changes? | Implement Continuous Integration. |
| Do you want every successful change to be ready for release? | Implement Continuous Delivery. |
| Do you want every successful change to reach production automatically? | Implement Continuous Deployment. |
| Do production releases require approval or compliance checks? | Use Continuous Delivery with approval gates. |
| Do you have strong automated tests and monitoring? | Continuous Deployment may be appropriate. |
| Do you need to reduce deployment risk? | Use canary, blue-green, rolling deployments, feature flags, and automated rollback. |

---

## Summary

CI/CD is an automated approach to building, testing, releasing, deploying, and monitoring software.

The overall process can be represented as:

    Code
      │
      ▼
    Build
      │
      ▼
    Test
      │
      ▼
    Validate
      │
      ▼
    Package
      │
      ▼
    Release
      │
      ├── Continuous Delivery
      │       └── Manual Approval → Production
      │
      └── Continuous Deployment
              └── Automatic Deployment → Production
      │
      ▼
    Monitor and Improve

The key distinction is:

- **Continuous Integration** validates code changes frequently.
- **Continuous Delivery** keeps validated software ready for release.
- **Continuous Deployment** automatically releases validated software to production.

In simple terms:

    Continuous Integration = Integrate and validate code frequently
    Continuous Delivery     = Keep software ready to deploy
    Continuous Deployment   = Deploy software automatically