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
  - [Reliability](#reliability)
  - [Security](#security)
  - [Cost Optimization](#cost-optimization)
  - [Operational Excellence](#operational-excellence)
  - [Performance Efficiency](#performance-efficiency)

## System Context

- 

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

- 

## Environments Design

- 

## Release Strategy

- 

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

    - SLO 1: SLI Type: Latency

           SLI Specification: Proportion of user login requests processed in < 2 seconds.

           SLI = (Number of successful login requests processed in < 2 seconds) / (Total number of login requests)

      - SLO 2: SLI Type: Latency
          
           SLI Specification: Proportion of money transfer transactions completed in < 3 seconds.

           SLI = (Number of successful transactions completed in < 3 seconds) / (Total number of transactions)

      - SLO 3: SLI Type: Latency

           SLI Specification: Proportion of database queries completed in < 500 milliseconds.

           SLI = (Number of successful queries completed in < 500 milliseconds) / (Total number of queries)

      - SLO 4: SLI Type: Availability
           
           SLI Specification: Proportion of successful HTTP requests.

           SLI = (Number of successful HTTP requests) / (Total number of HTTP requests)

      - SLO 5: SLI Type: Availability
           
           SLI Specification: System uptime maintained at or above 99.9%.

           SLI = (Total uptime minutes) / (Total minutes in the month)

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

## Well Architected Framework Design

### Reliability

- 

### Security

- 

### Cost Optimization

- 

### Operational Excellence

- 

### Performance Efficiency

- 

<div class="previous-section-link"> 
  <a href="assumptions_constraints.html">Previous</a>
</div>

<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="functional_requirements.html">Next</a>
</div>