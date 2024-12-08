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

The infrastructure for **devious_devops bank** is modularized using **Azure Bicep** templates. Each major resource is encapsulated in its respective module to ensure reusability, scalability, and maintainability across different environments.

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

### **Azure App Service and App Service Plan**

| **Environment** | **App Service Plan** | **Frontend Name**     | **Backend Name**      |
|------------------|----------------------|-----------------------|-----------------------|
| Development     | `devious-asp-dev`    | `devious-fe-dev`      | `devious-be-dev`      |
| UAT             | `devious-asp-uat`    | `devious-fe-uat`      | `devious-be-uat`      |
| Production      | `devious-asp-prod`   | `devious-fe-prod`     | `devious-be-prod`     |

---

### **Azure Database for PostgreSQL**

| **Environment** | **Server Name**       | **Database Name**     |
|------------------|-----------------------|-----------------------|
| Development     | `devious-dbsrv-dev`   | `devious-db-dev`      |
| UAT             | `devious-dbsrv-uat`   | `devious-db-uat`      |
| Production      | `devious-dbsrv-prod`  | `devious-db-prod`     |

---

### **Azure Key Vault**

| **Environment** | **Key Vault Name**    |
|------------------|-----------------------|
| Development     | `devious-kv28-dev`    |
| UAT             | `devious-kv28-uat`    |
| Production      | `devious-kv28-prod`   |

---

### **Azure Log Analytics Workspace**

| **Environment** | **Workspace Name**    |
|------------------|-----------------------|
| Development     | `devious-law-dev`     |
| UAT             | `devious-law-uat`     |
| Production      | `devious-law-prod`    |

---

### **Azure Application Insights**

| **Environment** | **Application Insights Name** |
|------------------|-------------------------------|
| Development     | `devious-ai-dev`              |
| UAT             | `devious-ai-uat`              |
| Production      | `devious-ai-prod`             |

---

### **Azure Static Web Apps**

| **Environment** | **Static Web App Name** |
|------------------|-------------------------|
| Development     | `devious-swa-dev`       |
| UAT             | `devious-swa-uat`       |
| Production      | `devious-swa-prod`      |

---

### **Azure Container Registry (ACR)**

| **Environment** | **Registry Name**     |
|------------------|-----------------------|
| Development     | `deviousacrdev`       |
| UAT             | `deviousacruat`       |
| Production      | `deviousacrprod`      |

---

## **3. Infrastructure Release Strategy**

The **Infrastructure Release Strategy** leverages **Azure Bicep** templates and **GitHub Actions** to ensure automated, reliable, and consistent deployments across environments.

### **Release Workflow**

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
