---
layout: default
title: "General System Description"
---

<style>

.back-home-link {
  position:fixed;
  bottom: 5px;
  left: 20px;
  color: white;
  padding: 10px;
  border-radius: 5px;
  text-decoration: none;
  font-weight: normal;
}

.back-home-link:hover {
  background-color: #D3D3D3;
}

.next-section-link {
  position: fixed;
  bottom: 20px;
  right: 20px; 
  color: white;
  padding: 10px;
  border-radius: 5px;
  text-decoration: none;
  font-weight: bold;
  }

.next-section-link:hover {
  background-color: #D3D3D3;
}

.previous-section-link {
  position:fixed;
  bottom: 20px;
  left: 20px;
  color: white;
  padding: 10px;
  border-radius: 5px;
  text-decoration: none;
  font-weight: bold;
}

.previous-section-link:hover {
  background-color: #D3D3D3;
}

#table-of-contents {
  margin-bottom: 20px;
}
</style>

# General System Description

This section provides an overview of the general system architecture and its components for the IE BANK project.

## Table of Contents
- [System Context](#system-context)
- [Infrastructure Architecture Design](#infrastructure-architecture-design)
- [Environments Design](#environments-design)
- [Release Strategy](#release-strategy)
- [Monitoring Strategy](#monitoring-strategy)
  - [Service Level Agreements (SLAs)](#service-level-agreements-slas)
  - [Service Level Objectives (SLOs)](#service-level-objectives-slos)
  - [Service Level Indicators (SLIs)](#service-level-indicators-slis)
  - [Azure Services Utilized](#azure-services-utilized)
  - [Monitoring Strategy](#monitoring-strategy-1)
  - [Service Mapping Design](#service-mapping-design)
- [Well Architected Framework Design](#well-architected-framework-design)
  - [1. Reliability](#1-reliability)
  - [2. Security](#2-security)
  - [3. Cost Optimization](#3-cost-optimization)
  - [4. Performance Efficiency](#4-performance-efficiency)
  - [5. Operational Excellence](#5-operational-excellence)
- [12-Factor App Design](#12-factor-app-design)


## System Context

The **IE Bank Application** is a cloud-native banking platform designed to provide a secure, scalable, and user-friendly experience for managing financial accounts and transactions. Built on Microsoft Azure, the application follows a modular architecture to ensure flexibility and alignment with modern DevOps practices.

---

#### **Users and Roles**

1. **End Users**:
   - Access the system via a responsive Vue.js frontend to view account balances, manage transactions, and track financial activities.
2. **Admins**:
   - Use the admin interface to manage user accounts, oversee transactions, and ensure compliance with security and operational standards.

---

#### **System Components**

1. **Frontend**:
   - Hosted on Azure Static Web Apps, the Vue.js frontend provides a fast, reliable user interface that is globally distributed for performance and scalability.
2. **Backend**:
   - A Python-based API hosted on Azure App Service for Containers, responsible for business logic, user authentication, and transaction processing.
3. **Database**:
   - Azure Database for PostgreSQL serves as the primary data store, offering fault tolerance, automatic backups, and high performance for financial data.
4. **Monitoring and Security**:
   - Application Insights provide system observability and telemetry for proactive issue resolution.
   - Azure Key Vault ensures the secure storage of sensitive credentials, such as database connection strings and API keys.
5. **Infrastructure Components**
  - Infrastructure as Code (IaC): The infrastructure is provisioned using Azure Bicep templates, enabling consistent, modular, and automated deployments across environments.
  - The system is deployed in isolated Development, Testing, Acceptance, and Production environments, ensuring controlled progression through the software lifecycle.
  - Container Management: Azure Container Registry (ACR) securely stores and manages Docker images for the backend API, with seamless integration into CI/CD pipelines.

---

#### **Interactions and Flows**

- Users and admins interact with the system via secure HTTPS endpoints, authenticated using Azure AD or token-based authentication.
- The backend communicates with the database to retrieve and update account and transaction details, ensuring data consistency and security.

---
### Sumary
By leveraging Azure services and adhering to the Azure Well-Architected Framework, the IE Bank Application delivers a robust, efficient, and scalable solution for modern banking needs.


## Infrastructure Architecture Design
The infrastructure for the IE Bank MVP has been carefully designed to ensure scalability, security, and cost-effectiveness while meeting the functional and non-functional requirements of the application. We have adopted a cloud-native approach, leveraging Microsoft Azure services to create a robust DTAP (Development, Testing, Acceptance, Production) environment strategy. This design aligns with industry best practices and the Azure Well-Architected Framework.

### Key Azure Services and Architecture Components
1. **Frontend Hosting** : **Azure Static Web Apps:**
  - A lightweight and cost-effective service to host the Vue.js frontend.
  - Provides automatic CI/CD integration via GitHub Actions
  - Enables global scalability and quick deployment.
2. **Backend Hosting**: **Azure App Service for Containers**
  - Hosts the Python backend as a containarized service. 
  - Proivides seamless scalling, reliabilit, and integration with Azure monitoring tools.
3. **Database: Azure Database for PostreSQL**
  - A managed relational database service chosen for secure and scalable data storage.
  - Utilizes Flexible Server mode for optimal cost and performance.
4. **Container Management: Azure Container Registry (ACR):**
  - Hosts Docker container images for backend services
  - Integrated with Key Vault for secure credential management.
5. **Secrets Management: Azure Key Vault**
  - Ensures secure storage of secrets like PostgreSQL credentials and ACR authentication keys.
  - Integrated with the backend and deployment pipelines for automated secret retrieval.
6. **Monitoring and Logging: Azure Monitor and Log Analytics Workspace**
  - Centralized log collection and metric analysis for infrastructure and application layers.
  - Azure Application Insights:
  - Provides in-depth performance monitoring and telemetry for the frontend and backend.

### Environment Setup: DTAP Approach
We have implemented a **DTAP** (Development, Testing, Acceptance, Production) environment strategy to ensure isolated and controlled stages for the application lifecycle.
1. **Development Environment:**
  - Deployed in a dedicated Azure Resource Group (BCSAI2024-DEVOPS-STUDENTS-A-DEV).
  - Accessible to the team for experimentation and feature development.
  - Configured for real-time CI/CD deployments triggered by feature branch commits.
2. **Testing Environment:**
  - Integrated with the UAT Resource Group(BCSAI2024-DEVOPS-STUDENTS-A-UAT).
  - Facilitates automated functional tests via GitHub Actions.
  - Simulates production workloads for stakeholder demonstrations.
3. **Production Environment:**
  - Hosted in a Production Resource Group (BCSAI2024-DEVOPS-STUDENTS-A-PROD).
  - Configured for high availability and optimal performance for end-users.
  - Deployments occur only after successful tests in UAT.

### Infrastructure-as-Code (IaC)
The infrastructure is defined using **Azure Bicep**, a modular IaC approach that simplifies deployment and management.
1. **Modularization:**
 - Each Azure service (e.g., App Service, PostgreSQL, Key Vault) is defined as an independent Bicep module.
 - These modules are reusable and parameterized to support the DTAP environment strategy.
2. **Main Bicep File:**
  - Acts as the orchestrator for deploying all modules.
  - Environment-specific configurations (e.g., database tiers, region settings) are handled via parameter files.
3. **Parameter Files:**
- Separate parameter files for Development, UAT, and Production.
- Enables consistent deployment across all environments with minimal changes.


## Environments Design

### Overview

The environment design ensures a structured and consistent approach to deploying and managing the IE Bank application across its lifecycle. By adopting the **DTAP (Development, Testing, Acceptance, Production)** strategy, we maintain clear boundaries between environments, enabling controlled deployments, thorough testing, and high confidence in production stability. Each environment is configured to reflect its unique purpose, from experimentation in Development to secure and optimized setups in Production.

---

### DTAP Environments and Configurations

Each environment is deployed within its respective Azure Resource Group, with configurations tailored to its specific role. Below are the key characteristics and services for each environment:

**1. Development Environment**
- **Purpose**: For developers to experiment, implement, and validate features.
- **Resource Group**: `BCSAI2024-DEVOPS-STUDENTS-A-DEV`
- **Services**:
  - **Azure Static Web Apps**: Hosts the frontend for feature testing.
  - **Azure App Service**: Runs the containerized backend with frequent updates.
  - **Azure Database for PostgreSQL**: Basic configuration for cost-effectiveness.
  - **Azure Key Vault**: Stores secrets (e.g., database credentials).
  - **Azure Monitor**: Tracks performance metrics and logs during development.
- **Deployment**:
  - Triggered by GitHub feature branch commits using CI pipelines.
  - Frequent deployments ensure real-time validation of new code.

---

**2. Testing/UAT Environment**
- **Purpose**: Facilitates functional, integration, and acceptance testing.
- **Resource Group**: `BCSAI2024-DEVOPS-STUDENTS-A-UAT`
- **Services**:
  - **Azure Static Web Apps**: Hosts a near-production frontend for stakeholder previews.
  - **Azure App Service**: Deploys a stable backend container for testing.
  - **Azure Database for PostgreSQL**: Uses a configuration that mirrors production settings.
  - **Azure Key Vault**: Securely stores credentials for the UAT setup.
  - **Azure Monitor**: Captures logs and metrics for test validation.
  - **Application Insights**: Collects telemetry for backend/frontend performance testing.
- **Deployment**:
  - Triggered by Pull Requests to the main branch.
  - Tests are executed as GitHub status checks, and only passing tests allow a merge.

---

**3. Production Environment**
- **Purpose**: Serves the live application to end-users with high reliability and performance.
- **Resource Group**: `BCSAI2024-DEVOPS-STUDENTS-A-PROD`
- **Services**:
  - **Azure Static Web Apps**: Fully optimized for end-user traffic.
  - **Azure App Service**: Scaled container backend for reliability under high loads.
  - **Azure Database for PostgreSQL**: High-availability configuration with backups.
  - **Azure Key Vault**: Enforces stringent access policies for secrets management.
  - **Azure Monitor and Log Analytics Workspace**: Provides centralized logging and alerting.
  - **Application Insights**: Monitors application health, latency, and errors in real time.
- **Deployment**:
  - Triggered by merging successfully tested code from UAT.
  - Deployment follows automated CI/CD workflows with rollback capabilities.

---

### Configuration Differentiation

Environment-specific configurations are managed through Azure Bicep parameter files. These parameter files ensure consistency in deployment while allowing flexibility for each environment's unique needs.

| **Service**         | **Development**          | **UAT**                         | **Production**                     |
|----------------------|--------------------------|----------------------------------|-------------------------------------|
| **App Service Plan** | Basic Tier               | Standard Tier                   | Premium Tier                       |
| **PostgreSQL DB**    | Single Zone             | Zone-Redundant                  | Zone-Redundant with Backups        |
| **Key Vault Policies** | Developer Access        | Limited Stakeholder Access       | Restricted Production Access       |
| **Scaling Rules**    | Manual Scaling          | Auto-Scaling with Alerts        | Auto-Scaling with Redundancy       |
| **Monitoring**       | Minimal Logs            | Logs + Metrics                  | Full Monitoring + Alerts           |

---

### CI/CD Integration Across Environments

- **Development**: 
  - Feature branch commits automatically trigger builds and deploy to the Development environment.
- **UAT**:
  - Pull requests trigger test workflows and deploy to UAT for approval.
- **Production**:
  - Merges to the main branch trigger deployments to Production after passing all automated checks.

---

### Security and Isolation

- Each environment operates in its own Azure Resource Group, ensuring isolation.
- Access policies vary across environments, with stricter controls in UAT and Production.
- Secrets are stored securely in Azure Key Vault, with automated rotation and limited access per environment.

---

### Benefits of the DTAP Approach

- **Consistency**: Ensures repeatable and predictable deployments.
- **Reduced Risk**: Isolated environments prevent testing or development issues from affecting Production.
- **Scalability**: Enables gradual scaling and tuning as code progresses from Development to Production.
- **Stakeholder Confidence**: UAT provides a near-live preview of features before deployment.

---

### Summary

The DTAP environment strategy ensures a robust and methodical deployment process, minimizing risks and maximizing quality. By maintaining environment-specific configurations and leveraging Azure's cloud capabilities, the IE Bank MVP is poised for secure and seamless operations at every stage.


## Release Strategy

This updated release strategy ensures that all deployments across Development, UAT, and Production environments are executed securely, reliably, and efficiently. It integrates environment-specific designs, aligns with the DevOps Checklist from Azure Architecture Center, and incorporates best practices from DevSecOps with GitHub Security.

### Environment Design in the Release Strategy
The release strategy follows our **DTAP (Development, Testing, Acceptance, Production)** approach, ensuring isolated and purpose-driven environments. Each environment plays a specific role in the lifecycle:

**Development Environment**
- **Purpose**: Active development, experimentation, and unit testing.
- **Configuration**:
  - Lightweight App Service plans and database tiers to reduce costs.
  - Integration with feature branch CI pipelines.
- **Deployment Trigger**: Commits to feature branches.

**UAT Environment**
- **Purpose**: Validation of functionality, stakeholder feedback, and pre-production testing.
- **Configuration**:
  - Closer parity with Production, including App Service scaling and database settings.
  - Automated functional tests and manual QA processes.
- **Deployment Trigger**: Pull Requests (PRs) to the main branch.

**Production Environment**
- **Purpose**: Final live environment for end-users.
- **Configuration**:
  - High-availability services and redundancy (e.g., zone-redundant PostgreSQL).
  - Secure configurations and monitoring (Key Vault, Azure Monitor).
- **Deployment Trigger**: Successful tests in UAT and approved PRs merged into the main branch.

### Decisions Based on the DevOps Checklist

The **DevOps Checklist** from the Azure Architecture Center has been reviewed and incorporated to ensure best practices in the release strategy:

**Source Control**
- All code, including IaC, is stored in GitHub repositories.
- Feature branching with branch policies (e.g., PR reviews, status checks).

**Continuous Integration/Delivery**
- Automated CI pipelines for building, testing, and deploying applications.
- Continuous Delivery pipelines configured with environment-specific gates:
  - Feature branches → Development
  - PRs → UAT
  - Main branch merges → Production

**Testing**
- **Unit tests**: `pytest` for backend, Postman for APIs in CI workflows.
- **Automated functional tests**: Required for UAT deployments as status checks.
- **Deployment strategies**: Canary or blue-green strategies for critical Production updates.

**Infrastructure as Code (IaC)**
- Infrastructure modularized using Azure Bicep.
- Parameterized templates for environment-specific configurations.

**Monitoring and Logging**
- Centralized logging with Log Analytics Workspace.
- Alerts and dashboards configured for proactive issue detection.

### Review and Decisions Based on DevSecOps with GitHub Security

The **DevSecOps best practices** from Azure Architecture Center and GitHub Security are integrated into the release strategy to secure the pipeline and application:

**GitHub Security Features**
- **CodeQL**: Automated code scanning for vulnerabilities in backend (Python) and frontend (Vue.js).
- **Dependabot**: Monitors and updates dependencies to patch known vulnerabilities.
- **Secret Scanning**: Prevents sensitive information like API keys from being committed.
- **Push Protection**: Blocks the addition of secrets to the repository.

**Infrastructure Security**
- Secrets (e.g., PostgreSQL credentials) managed via Azure Key Vault.
- App Service and database configured with strict access controls and encrypted connections.

**CI/CD Pipeline Security**
- GitHub branch protection policies enforce PR reviews, status checks, and passing tests before merging.
- Deployment credentials stored securely in Key Vault and retrieved dynamically during builds.
- Least privilege access for pipeline Service Principal (SP) accounts.

**Application Security**
- End-to-end encryption for data at rest (Azure-managed keys) and in transit (HTTPS/TLS).
- Role-based access control (RBAC) ensures proper permissions in Azure environments.

### Updated Deployment Workflow

This release strategy incorporates secure and efficient deployment workflows:

**Development**
- Linting, building, and unit tests on every commit.
- Immediate deployment to Development.

**UAT**
- Triggered by PR creation.
- Automated functional tests must pass to proceed.

**Production**
- Final deployment triggered by merging a PR.
- Production monitoring activated to verify deployment success.

### Summary

The updated release strategy tightly integrates secure, efficient, and scalable practices while aligning with the Azure DevOps Checklist and DevSecOps principles. This approach ensures that every release is not only functional but also secure, robust, and auditable, minimizing risks while maximizing delivery speed and confidence.


## Monitoring Strategy

### Service Level Agreements (SLAs)

- Define the SLA you want to provide in production:
  - SLA of all Azure Services hosting your production workload.
  - Configuration applied to the hosting infrastructure in production.
  - Dependencies between your components (service mapping).
  - Use cases affecting user experience. small change
  - Documented SLIs and SLOs.

### Service Level Objectives (SLOs)

  - Objective 1 - User Authentication Response Time:  99% of user login requests will be processed in under 2 seconds
  - Objective 2 - Transaction Processing Time - 95% of money transfer transactions will be completed within 3 seconds
  - Objective 3 - Database Query Performance: 90% of database queries executed against the PostgreSQL database will complete in under 500 milliseconds
  - Objective 4 - HTTP Requests: 95% of HTTP requests for the IE Bank static website will be processed in under 2 seconds.
  - Objective 5 - System Availability: The overall system (frontend and backend) will maintain an uptime of 99.9% over any given month

### Service Level Indicators (SLIs)

- **SLO 1**: **SLI Type**: Latency  
  **SLI Specification**: Proportion of user login requests processed in < 2 seconds.  
  **SLI Formula**:  
  `SLI = (Number of successful login requests processed in < 2 seconds) / (Total number of login requests)`

- **SLO 2**: **SLI Type**: Latency  
  **SLI Specification**: Proportion of money transfer transactions completed in < 3 seconds.  
  **SLI Formula**:  
  `SLI = (Number of successful transactions completed in < 3 seconds) / (Total number of transactions)`

- **SLO 3**: **SLI Type**: Latency  
  **SLI Specification**: Proportion of database queries completed in < 500 milliseconds.  
  **SLI Formula**:  
  `SLI = (Number of successful queries completed in < 500 milliseconds) / (Total number of queries)`

- **SLO 4**: **SLI Type**: Availability  
  **SLI Specification**: Proportion of successful HTTP requests.  
  **SLI Formula**:  
  `SLI = (Number of successful HTTP requests) / (Total number of HTTP requests)`

- **SLO 5**: **SLI Type**: Availability  
  **SLI Specification**: System uptime maintained at or above 99.9%.  
  **SLI Formula**:  
  `SLI = (Total uptime minutes) / (Total minutes in the month)`

- Outline the Azure services that will be used for the monitoring strategy:
  - Azure Monitor
  - Log Analytics Workspace
  - Application Insights
  - Azure Workbooks
  - [Any additional services]

### Monitoring Strategy

- Document the strategy for Application Monitoring, Capability Monitoring, and Fault Tolerance:
  - **Data Needs**: [Describe data requirements]
  - **Collection Points**: [Identify data collection points]
  - **Analysis Process**: [Outline the analysis process]
  - **Management Controls**: [Define management controls]
  - **Decision Approach**: [Describe the decision-making process]
  - **Automation Orchestration**: [Detail orchestration strategies]
  - **Communication Model**: [Outline the communication model for services]

### Service Mapping Design

- [Provide a brief description of the service mapping design.]

-

## Incident Response Design
Incident Response Design

Incident Response Design for IE Bank Application

Version: 1.0

Effective Date: 08/11/2024

Last Reviewed: 27/11/2024

1\. Purpose

This document defines the incident response plan for the IE Bank application, detailing the detection, response, and resolution processes for incidents. The main goal is to minimize downtime, adhere to SLA commitments, and ensure customer satisfaction.

2\. Incident Response Objectives

Minimize downtime: Maintain 99.9% system uptime.

Ensure SLO adherence: Address login latency, transaction processing, and database query performance.

Rapid resolution: Detect and resolve incidents efficiently to mitigate customer impact.

Effective communication: Keep internal teams and stakeholders informed during incidents.

3\. Detection

Tools:

-   Application Insights: Detect infrastructure and latency issues in login, transaction processing, and HTTP requests.

-   Log Analytics Workspace: Collect database query performance metrics.

-   Diagnostic Settings: Send logs from App Services, PostgreSQL, and Container Registry to Log Analytics Workspace.

Real-Time Alerts:

-   User login latency exceeds 2 seconds.

-   Money transfer processing time exceeds 3 seconds.

-   Database query execution time exceeds 500ms.

-   System uptime drops below 99.9%.

-   HTTP error rate spikes.

4 Incident Response Steps

Detection:

-   Real-time alert triggered by Azure Monitor or Application Insights.

-   Example: Application Insights logs "Money transfer latency exceeds 3 seconds."

Notification:

-   Notification sent via Slack (integrated with Azure Alerts)

Triage:

-   Assess incident severity using real-time dashboards and logs.

-   Identify the impacted component (frontend, backend, database, or monitoring).

Response:

-   Critical Incidents:

-   Restart affected App Services or database services.

-   Use Azure Resource Health to confirm Azure platform stability.

-   High/Medium Incidents:

-   Address slow-performing queries or API endpoints.

-   Use Runbooks to scale infrastructure or optimize resources.

Resolution:

-   Fix the issue and verify normal operations.

Post-Incident Review:

-   Conduct a retrospective to document root cause, impact, and resolution.

-   Implement measures to prevent recurrence (e.g., adjust thresholds or add load testing).

5\. External Communication

If there were to be a problem, we would notify customers via email or in-app alerts for Critical/High incidents.

Example:

We are experiencing an issue with our money transfer system. Our team is working to resolve this and restore service as quickly as possible. Thank you for your patience.

6\. Roles and Responsibilities

Role  Responsibilities

On-Call Engineer  Respond to alerts, investigate the issue, and implement fixes.

Incident Manager  Oversee response efforts and coordinate communication with stakeholders.

DevOps Engineer  Resolve infrastructure-level issues (e.g., scaling, container registry).

Database Admin  Address database performance issues (e.g., slow queries, connection errors).

SRE Team Lead  Conduct incident retrospectives and implement process improvements.

7\. Key Tools and Automation

7.1 Tools

-   Application Insights: Monitors application performance and error rates.

-   Log Analytics Workspace: Stores diagnostic logs for database and application monitoring.

-   Azure Workbooks/Dashboards: Visualizes real-time metrics and incident status.

7.2 Automation

-   Slack Integration: Notify teams of incidents and escalate unacknowledged alerts.

-   Azure Resource Health: Confirm Azure service health during incidents.

8\. Metrics for Measuring Incident Response

Metric  Description

-   Time to Detect (TTD): Time taken to detect an incident after it occurs.

-   Time to Acknowledge (TTA):  Time taken for an on-call engineer to acknowledge the incident.

-   Time to Resolve (TTR): Time taken to fully resolve the incident.

9\. Post-Incident Review Process

Root Cause Analysis:

-   Identify the root cause (e.g., database query inefficiency, container crash).

Impact Analysis:

-   Assess the impact on SLOs and SLAs (e.g., downtime or latency breaches).

Preventive Measures:

-   Update alert thresholds or implement new monitoring techniques.

-   Additionally, update any necessary documentation to keep things up to date and prevent it from happening again

10\. Review, Revision and Acceptance

As same as the SLA, this incident response plan will be reviewed quarterly. 

By using this plan, devious IE bank ensures an effective response to incidents, minimizing disruptions and adhering to SLA commitments.

## Well Architected Framework Design

The design of the IE Bank application leverages the Microsoft Azure Well-Architected Framework to ensure it meets high standards of reliability, security, performance, cost efficiency, and operational excellence. Each design decision has been carefully evaluated to address both functional and non-functional requirements while ensuring scalability and resilience.

### 1. Reliability

Reliability is critical to ensure the IE Bank MVP performs its intended functions without failure, especially in Production.

**Design Features:**
- **Azure App Service Plan**:
  - Uses a zone-redundant configuration for high availability in Production.
  - Autoscaling enabled based on CPU and memory utilization to handle peak loads.
- **Azure Database for PostgreSQL**:
  - Configured in zone-redundant mode for fault tolerance.
  - Automatic backups with point-in-time recovery enabled.
- **Monitoring and Alerts**:
  - Log analytics provide real-time insights into application performance.
  - Alerts notify teams of potential issues, enabling swift remediation.

### 2. Security

Security ensures the protection of sensitive data, such as user credentials and financial transactions.

**Design Features:**
- **Azure Key Vault**:
  - Manages secrets, connection strings, and sensitive credentials.
  - Integrated with App Services and GitHub workflows for secure CI/CD pipelines.
- **GitHub Advanced Security**:
  - CodeQL scans for vulnerabilities in backend (Python) and frontend (Vue.js).
  - Dependabot keeps dependencies up-to-date, reducing exposure to known vulnerabilities.
- **Azure Networking**:
  - Restricts inbound traffic using Application Gateway and Network Security Groups (NSGs).
- **Encryption**:
  - Data at rest is encrypted with Azure-managed keys in PostgreSQL.
  - Data in transit uses HTTPS and TLS for frontend-backend communication.

### 3. Cost Optimization

Cost optimization ensures efficient use of Azure resources while maintaining performance and reliability.

**Design Features:**
- **Resource Scaling**:
  - Development and UAT environments use lower-cost service tiers.
  - Production leverages autoscaling to adjust resource usage based on traffic demands.
- **Static Web Hosting**:
  - Vue.js frontend is hosted on Azure Static Web Apps, minimizing hosting costs.
- **Efficient Resource Utilization**:
  - Consolidated logging and monitoring using a single Log Analytics Workspace.
  - Scheduled database scaling during non-peak hours for Development and UAT.

### 4. Performance Efficiency

Performance efficiency ensures the application can handle current and future workloads effectively.

**Design Features:**
- **Azure App Service Plan**:
  - Configured for autoscaling based on CPU and memory utilization.
  - Optimized for container workloads with Linux App Services.
- **Azure Database for PostgreSQL**:
  - Uses optimized query execution plans and indexing to reduce latency.
- **Application Insights**:
  - Tracks application performance metrics (e.g., response times, request rates).
  - Identifies bottlenecks in real-time for both frontend and backend.


### 5. Operational Excellence

Operational excellence ensures smooth application deployment and maintenance, minimizing downtime and maximizing development productivity.

**Design Features:**
- **CI/CD Pipelines**:
  - GitHub Actions automate deployments across Development, UAT, and Production.
  - Includes tests for code quality, security, and functionality.
- **Infrastructure as Code (IaC)**:
  - Bicep templates modularize and automate resource provisioning.
- **Monitoring and Incident Response**:
  - Azure Monitor and Application Insights provide real-time visibility.
  - Alerts integrated with Slack via ChatOps for rapid incident response.

### Design Tradeoffs

Some design decisions involve tradeoffs to balance between the framework pillars:
- **Cost vs. Reliability**:
  - UAT and Production environments prioritize reliability with higher-tier resources.
  - Development uses cost-effective options like basic-tier PostgreSQL and App Services.
- **Performance vs. Cost**:
  - Autoscaling ensures optimal performance during peak loads, but may incur additional costs.

### Unnadressed Pillar - Sustainability 
**Why Not Addressed?**
Sustainability was not a primary focus during the MVP phase, as the project prioritized performance, security, and cost management. The effort required to evaluate and optimize environmental impact will be deferred to later stages.

**Future Plans:**
- Incorporate tools like Azure Sustainability Calculator to evaluate the carbon footprint of the application.
- Optimize resource usage further, such as reducing idle resource consumption in non-production environments and leveraging green regions where available.

### Summary

The IE Bank application infrastructure adheres to the Azure Well-Architected Framework, ensuring a secure, reliable, and efficient system. By leveraging Azure's robust services and best practices, the design supports scalability, performance, and operational excellence, meeting both current needs and future growth.

## 12-Factor App Design

### Overview

The 12-Factor App methodology provides a set of best practices for building modern, scalable, and maintainable cloud-native applications. The IE Bank MVP adheres to these principles to ensure reliability, scalability, and ease of deployment across environments. Below is how each of the 12 factors is applied in the design and implementation of the product.

---

### 1. Codebase
**A single codebase tracked in version control, with multiple deployments.**  
**Implementation**:
- 2 GitHub repositories contains the code for the frontend (Vue.js), backend (Python Flask).
- Modular infrastructure code is stored in the a separate repository, leveraging Azure Bicep.
- **Branching strategy**: Feature branches for development; main for production.

---

### 2. Dependencies
**Explicitly declare and isolate dependencies.**  
**Implementation**:
- Backend dependencies are managed with `pip` and `requirements.txt`.
- Frontend dependencies are managed with `npm` and `package.json`.
- Containers ensure isolated environments, with images built using Docker.

---

### 3. Configuration
**Store configuration in the environment, not in the code.**  
**Implementation**:
- Sensitive credentials (e.g., database connections, API keys) are stored in Azure Key Vault.
- Environment-specific configurations are handled via Bicep parameter files.
- Application settings (e.g., UAT vs. Production) are managed using Azure App Service settings.

---

### 4. Backing Services
**Treat backing services (e.g., databases, queues) as attached resources.**  
**Implementation**:
- The PostgreSQL database is provisioned as a managed Azure resource.
- Secrets for database and other external services are integrated through Key Vault.
- Backend services connect dynamically to resources based on the environment.

---

### 5. Build, Release, Run
**Separate the build and run stages for deployment.**  
**Implementation**:
- **Build**: CI pipelines build Docker images for the backend and frontend.
- **Release**: Release artifacts are deployed to UAT for validation.
- **Run**: After validation, production deployments are triggered automatically.

---

### 6. Processes
**Execute the app as one or more stateless processes.**  
**Implementation**:
- The backend is stateless and scalable, with session data stored in the database.
- Frontend interactions rely on APIs for dynamic data, with no local storage of state.

---

### 7. Port Binding
**Expose services via port binding.**  
**Implementation**:
- Backend runs on a containerized App Service, exposing an HTTP endpoint.
- Azure Static Web Apps serve the frontend, communicating with the backend via RESTful APIs.

---

### 8. Concurrency
**Scale out via the process model.**  
**Implementation**:
- Autoscaling is enabled for the App Service and PostgreSQL database in Production.
- Azure's built-in load balancer supports concurrent requests without manual configuration.

---

### 9. Disposability
**Maximize robustness with fast startup and graceful shutdown.**  
**Implementation**:
- Containers ensure consistent and fast startups.
- Graceful termination signals (e.g., SIGTERM) are handled to ensure clean resource release.

---

### 10. Dev/Prod Parity
**Keep development, staging, and production as similar as possible.**  
**Implementation**:
- DTAP environments are provisioned using the same Bicep templates for consistency.
- Azure Monitor and Application Insights provide similar telemetry in all environments.

---

### 11. Logs
**Treat logs as event streams.**  
**Implementation**:
- Application and infrastructure logs are centralized in Log Analytics Workspace.
- Application Insights captures performance and error telemetry for both frontend and backend.

---

### 12. Admin Processes
**Run admin/management tasks as one-off processes.**  
**Implementation**:
- Database migrations are executed as one-off commands in the CI/CD pipeline.
- Monitoring and incident responses leverage Azure CLI and automated scripts.

---

### Benefits for IE Bank MVP

- **Scalability**: The 12-Factor methodology supports horizontal scaling and seamless environment transitions.
- **Maintainability**: Clear separation of concerns simplifies debugging and onboarding.
- **Resilience**: Decoupling of services and statelessness ensures robust failover mechanisms.

---

### Summary

By aligning with the 12-Factor App principles, the IE Bank MVP achieves a cloud-native design optimized for modern application development. This foundation ensures the application is scalable, maintainable, and well-suited for continuous integration and delivery.


<div class="previous-section-link"> 
  <a href="assumptions_constraints.html">Previous</a>
</div>

<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="functional_requirements.html">Next</a>
</div>
