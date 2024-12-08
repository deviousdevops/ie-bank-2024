---
layout: default
title: "Infrastructure Developer Documentation"
---

# Infrastructure Developer Documentation

Welcome to the **Infrastructure Developer Documentation** for **devious_devops bank**. This document provides a comprehensive overview of the **Infrastructure as Code (IaC)** strategy, explains the employed **Azure services** with detailed configurations, and describes the **infrastructure release process** for environments: **Development**, **UAT**, and **Production**.

---

## **Table of Contents**

1. [Modularization Strategy](#modularization-strategy)
2. [Azure Services and Configurations](#azure-services-and-configurations)
    - [Azure App Service and App Service Plan](#azure-app-service-and-app-service-plan)
    - [Azure Database for PostgreSQL](#azure-database-for-postgresql)
    - [Azure Key Vault](#azure-key-vault)
    - [Azure Log Analytics Workspace](#azure-log-analytics-workspace)
    - [Azure Application Insights](#azure-application-insights)
    - [Azure Static Web Apps](#azure-static-web-apps)
    - [Azure Container Registry](#azure-container-registry)
3. [Infrastructure Release Strategy](#infrastructure-release-strategy)

---

## **1. Modularization Strategy**

### **Description of Modularization Strategy**

The infrastructure for **devious_devops bank** is organized into modular **Bicep templates**. Each resource is encapsulated in its respective module, ensuring clean separation, reusability, and maintainability across different environments.

---

### **Key Principles**
- **Separation of Concerns**: Each Bicep module focuses on a specific Azure service (ex: App Service, Key Vault, Database).
- **Reusability**: Modules are designed to work across **Development**, **UAT**, and **Production** environments.
- **Maintainability**: Updates are isolated to individual modules, ensuring reduced risk of breaking dependencies.
- **Scalability**: Additional services can be added seamlessly without modifying the entire infrastructure.

---

### **Bicep Modules Overview**

| **Module Name**           | **Purpose**                                      | **File**                  |
|---------------------------|-------------------------------------------------|---------------------------|
| App Service               | Deploys App Service Plan, frontend, and backend.| `app-service.bicep`       |
| Azure Key Vault           | Manages secrets and sensitive credentials.      | `key-vault.bicep`         |
| PostgreSQL Database       | Configures managed PostgreSQL database.         | `postgresql-db.bicep`     |
| Azure Container Registry  | Stores and manages Docker container images.     | `docker-registry.bicep`   |
| Azure Log Analytics       | Centralized logging and monitoring.             | `log-analytics.bicep`     |
| Azure Static Web Apps     | Deploys globally distributed static content.    | `static-web-frontend.bicep`|
| Azure Application Insights| Monitors application performance and telemetry. | `app-insights.bicep`      |

---

## **2. Azure Services and Configurations**

This section details the Azure services provisioned using **Bicep templates**, including their configurations and how they are applied in **Development**, **UAT**, and **Production**.

---

### **Azure App Service and App Service Plan**

**Purpose**:  
Azure App Service hosts both the **frontend application** and the **backend API**.

| **Environment** | **Frontend Name**     | **Backend Name**      | **App Service Plan SKU** |
|------------------|-----------------------|-----------------------|--------------------------|
| Development     | `devious-fe-dev`      | `devious-be-dev`      | B1 (Basic)               |
| UAT             | `devious-fe-uat`      | `devious-be-uat`      | B1 (Basic)               |
| Production      | `devious-fe-prod`     | `devious-be-prod`     | B1 (Basic)               |

**Configuration**:
- **Frontend**: Deployed using Node.js 18-LTS.
- **Backend**: Deployed as a containerized application pulled from **Azure Container Registry (ACR)**.


---

### **Azure Database for PostgreSQL**

---
**Purpose**:  
Provides relational database management for the backend API.

**Configuration**:
- **Version**: PostgreSQL 15.
- **Storage**: 32 GB.
- **Backup Retention**: 7 days.
- **Security**: Firewall allows only Azure services.

| **Environment** | **Server Name**       | **Database Name**     |
|------------------|-----------------------|-----------------------|
| Development     | `devious-dbsrv-dev`   | `devious-db-dev`      |
| UAT             | `devious-dbsrv-uat`   | `devious-db-uat`      |
| Production      | `devious-dbsrv-prod`  | `devious-db-prod`     |

---

### **Azure Key Vault**

| **Environment** | **Key Vault Name**    |
|------------------|-----------------------|
| Development     | `devious-kv29-dev`    |
| UAT             | `devious-kv29-uat`    |
| Production      | `devious-kv29-prod`   |

**Purpose**:  
Secures sensitive information like database credentials, API secrets, and encryption keys.

**Features**:
- Stores secrets like `DBPASS` and `SECRET_KEY`.
- Integrated with **Azure RBAC** for access control.
- Auditing enabled via Log Analytics.

---

### **Azure Log Analytics Workspace**

| **Environment** | **Workspace Name**    |
|------------------|-----------------------|
| Development     | `devious-law-dev`     |
| UAT             | `devious-law-uat`     |
| Production      | `devious-law-prod`    |

**Purpose**:  
Aggregates logs from various resources (App Service, PostgreSQL, and Key Vault) for centralized monitoring.

**Configuration**:
- **Retention**: 30 days.
- Enables querying and insights for resource performance and diagnostics.

---

### **Azure Application Insights**

| **Environment** | **Application Insights Name** |
|------------------|-------------------------------|
| Development     | `devious-ai-dev`              |
| UAT             | `devious-ai-uat`              |
| Production      | `devious-ai-prod`             |

**Purpose**:  
Provides telemetry and performance monitoring for the applications.

**Key Features**:
- Real-time application performance tracking.
- Error logging and telemetry insights.

---

### **Azure Static Web Apps**

| **Environment** | **Static Web App Name** |
|------------------|-------------------------|
| Development     | `devious-swa-dev`       |
| UAT             | `devious-swa-uat`       |
| Production      | `devious-swa-prod`      |

**Purpose**:  
Deploys the frontend static application globally with CI/CD workflows.

**Features**:
- Automatic builds and deployments using GitHub Actions.
- Free SSL certificates and CDN integration for global availability.

---

### **Azure Container Registry (ACR)**

---
**Purpose**:  
Stores Docker container images used by the backend API.

| **Environment** | **Registry Name**     |
|------------------|-----------------------|
| Development     | `deviousacrdev`       |
| UAT             | `deviousacruat`       |
| Production      | `deviousacrprod`      |

---

## **3. Infrastructure Release Strategy**

The **Infrastructure Release Strategy** leverages **Azure Bicep** templates and **GitHub Actions** to ensure automated, reliable, and consistent deployments across environments.

---

### **Release Workflow**


Below is the **simplified infrastructure diagram** with arrows showing resource relationships:

```plaintext
          +---------------------------+
          |   Azure Static Web Apps   | <-- Node.js Frontend
          +---------------------------+
                          |
                          v
          +---------------------------+
          |     Azure App Service     | <-- Python Backend (FastAPI)
          +---------------------------+
                          |
                          v
          +---------------------------+        +--------------------+
          |   Azure Container Registry| <----> |   Docker Images    |
          +---------------------------+        +--------------------+
                          |
                          v
          +---------------------------+
          |  Azure Database (PostgreSQL)| <-- Managed Identity (Secure Access)
          +---------------------------+
                          ^
                          |
          +---------------------------+
          |       Azure Key Vault      | <-- Secrets Management
          +---------------------------+
                          |
                          v
          +---------------------------+
          |  Azure Log Analytics       | <-- Logging & Diagnostics
          +---------------------------+
                          |
                          v
          +---------------------------+
          |  Azure Application Insights| <-- Monitoring & Telemetry
          +---------------------------+
```
1. **Environment-Specific Configurations**:  
   Each environment is configured using dedicated parameter files:
   - `dev.parameters.json`
   - `uat.parameters.json`
   - `prod.parameters.json`

2. **CI/CD Automation**:  
   GitHub Actions automates:
   - **Validation** of Bicep templates.
   - **Deployment** using Azure CLI.

### **Deployment Commands**

The following commands are used to deploy the infrastructure across environments:

- **Development**:
   ```bash
   az deployment group create \
     --resource-group devious-devops-law-dev \
     --template-file main.bicep \
     --parameters @dev.parameters.json
- **UAT**:
   ```bash
   az deployment group create \
     --resource-group devious-devops-law-dev \
     --template-file main.bicep \
     --parameters @dev.parameters.json
- **Production**:
   ```bash
   az deployment group create \
     --resource-group devious-devops-law-dev \
     --template-file main.bicep \
     --parameters @dev.parameters.json


3. **Rollback Mechanisms**:
   - Idempotent templates ensure safe re-deployment.
   - Previous configurations are retained for rollback scenarios.

---

Feel free to explore each section for detailed documentation.

<div class="previous-section-link"> 
  <a href="full_stack_developers.html">Previous</a>
</div>

<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="cybersecurity_engineer.html">Next</a>
</div>

