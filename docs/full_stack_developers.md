---
layout: default
title: "Full Stack Developers Documentation"
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

# Full Stack Developers Documentation

Welcome to the Full Stack Developer's section of the IE BANK documentation. Below you will find the key sections that describe the strategies and workflows involved in the frontend and backend development of IE BANK.

## Table of Contents
- [Git Feature Branch Strategy](#git-feature-branch-strategy)
- [Continuous Integration (CI) Workflow for Frontend](#continuous-integration-ci-workflow-for-frontend)
- [Continuous Integration (CI) Workflow for Backend](#continuous-integration-ci-workflow-for-backend)
- [Test/Behavior Driven Development Strategy](#test-behavior-driven-development-strategy)
- [Release Strategy](#release-strategy)
- [Continuous Delivery (CD) Workflow for Frontend](#continuous-delivery-cd-workflow-for-frontend)
- [Continuous Delivery (CD) Workflow for Backend](#continuous-delivery-cd-workflow-for-backend)

---

## Git Feature Branch Strategy

This section covers the Git feature branch strategy, describing how the team manages feature branches and the configuration applied in GitHub to implement this strategy.

- **Git Feature Branch Strategy**: [Git Feature Branch Strategy URL]

---

## Continuous Integration (CI) Workflow for Frontend

The CI workflow for the IE Bank frontend outlines the build steps involved in the process, explaining the purpose of each step to ensure that the code is built and tested continuously.

- **CI Workflow for Frontend**: [CI Workflow for Frontend URL]

---

## Continuous Integration (CI) Workflow for Backend

This section details the CI workflow for the backend, highlighting the build steps that ensure the backend code is continuously tested and integrated.

- **CI Workflow for Backend**: [CI Workflow for Backend URL]

### Trigger Events
- push to any branch
- pull_request to the main branch
- workflow_dispatch (manual trigger)

### Permissions
- contents: read
- id-token: write

### Environment Variables
- BACKEND_WEBAPP_DEV: Name of the development web app
- BACKEND_WEBAPP_UAT: Name of the UAT web app
- ACR_NAME_DEV: Azure Container Registry name for development
- ACR_NAME_UAT: Azure Container Registry name for UAT
- IMAGE_NAME: Docker image name

### Build Job
- *Runs on*: ubuntu-latest
- *Environment Variables*: ENV: ghci
- *Steps*:
  1. Checkout the repository.
  2. Set up Python 3.11.
  3. Upgrade pip.
  4. Install dependencies from requirements.txt.
  5. Lint the code using flake8.
  6. Run tests using pytest with coverage.
  7. Upload the build artifact for deployment jobs.

---

## Test/Behavior Driven Development Strategy

The Test/Behavior Driven Development (TDD/BDD) strategy defines how the team designs tests and selects User Stories to drive development through testing.

- **TDD/BDD Strategy**: [TDD/BDD Strategy URL]

---

## Release Strategy

The release strategy outlines the process, tools, and techniques used to release updates for both the frontend and backend of IE Bank.

- **Release Strategy**: [Release Strategy URL]

---

## Continuous Delivery (CD) Workflow for Frontend

This section explains the CD workflow for the frontend, detailing the deployment steps and their purpose in ensuring continuous delivery.

- **CD Workflow for Frontend**: [CD Workflow for Frontend URL]

---

## Continuous Delivery (CD) Workflow for Backend

The CD workflow for the backend describes the deployment pipeline and its steps for delivering backend updates continuously.

- **CD Workflow for Backend**: [CD Workflow for Backend URL]

### Deploy to Development Environment
- *Runs on*: ubuntu-latest
- *Needs*: build
- *Environment*: Development
- *Steps*:
  1. Download the build artifact from the build job.
  2. Log in to Azure.
  3. Get ACR credentials from the Dev Key Vault.
  4. Build and push the Docker image to the development ACR.
  5. Deploy the Docker image to the Azure Web App for Development.

### Deploy to UAT Environment
- *Runs on*: ubuntu-latest
- *Needs*: build
- *Environment*: UAT
- *Steps*:
  1. Download the build artifact from the build job.
  2. Log in to Azure.
  3. Get ACR credentials from the UAT Key Vault.
  4. Build and push the Docker image to the UAT ACR.
  5. Deploy the Docker image to the Azure Web App for UAT.

### Deploy to Production Environment
- *Runs on*: ubuntu-latest
- *Needs*: build
- *Environment*: Production
- *Steps*:
  1. Download the build artifact from the build job.
  2. Log in to Azure.
  3. Get ACR credentials from the Prod Key Vault.
  4. Build and push the Docker image to the production ACR.
  5. Deploy the Docker image to the Azure Web App for Production.

### Run Postman Tests on UAT Environment
- *Runs on*: ubuntu-latest
- *Needs*: deploy-uat
- *Environment*: UAT
- *Steps*:
  1. Checkout the repository.
  2. Set up Node.js.
  3. Install Newman (Postman CLI).
  4. Fetch the Postman collection.
  5. Fetch the Postman environment.
  6. Run the Postman tests using Newman.

---

Feel free to explore each section for detailed documentation.

<div class="previous-section-link"> 
  <a href="cloud_architect.html">Previous</a>
</div>

<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="infrastructure_developers.html">Next</a>
</div>

