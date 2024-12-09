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

This section covers the Git feature branch strategy, describing how the team manages feature branches and the configuration applied in GitHub to implement this strategy. Our strategy consits of:

- Protecting the main branch with GitHub branch policies

- Use short-living feature branches for new code development (give each feature branch a name representative of the new code being developed)

- Integrate the code soon via Pull Request to the main branch. Other person in the team needs to review a approve.

- **Git Feature Branch Strategy**: [[Git Feature Branch Strategy URL](https://github.com/deviousdevops/ie-bank-fe-2024/settings/rules/2893529)]

### Branch Protection Strategy

This strategy ensures the integrity, security, and quality of the codebase while facilitating collaboration. Below are the enabled protections and their purposes.

### Enabled Settings

### 1. Restrict Deletions
- **Description**: Only users with bypass permissions can delete the branch.
- **Purpose**: Prevents accidental or unauthorized deletion of critical branches.

### 2. Require Linear History
- **Description**: Disallows merge commits, enforcing a linear Git history.
- **Purpose**: Maintains a clean and readable commit history.

### 3. Require Merge Queue
- **Description**: Merges are processed sequentially through a queue.
- **Purpose**: Prevents conflicting changes and ensures orderly integration.

### 4. Require Signed Commits
- **Description**: All commits must have verified signatures.
- **Purpose**: Verifies the authenticity of commits to enhance security.

### 5. Require a Pull Request Before Merging
- **Description**: All changes must be submitted as pull requests.
- **Purpose**: Ensures every change is reviewed for quality and accuracy.

#### Pull Request Sub-settings:
- **Request Pull Request Review from Copilot**: Automatically requests reviews from Copilot when applicable.

### 6. Allowed Merge Methods
- **Description**: Supports Merge Commit, Squash, and Rebase methods.
- **Purpose**: Provides flexibility for integrating changes effectively.

### 7. Block Force Pushes
- **Description**: Prevents force pushes to the branch.
- **Purpose**: Protects branch history from being overwritten or altered.

---

### Benefits
- **Security**: Verified commits and blocked force pushes protect against unauthorized changes.
- **Code Quality**: Mandatory pull requests ensure peer review.
- **History Clarity**: Linear history and merge flexibility maintain a clean commit log.

This strategy safeguards the codebase while supporting team productivity and collaboration.


---

## Continuous Integration (CI) Workflow for Frontend
This section details the CI workflow for the frontend, highlighting the build steps that ensure the frontend code is continuously tested and integrated.

- **CI Workflow for Frontend**: [[CI Workflow for Frontend URL](https://github.com/deviousdevops/ie-bank-fe-2024/blob/main/.github/workflows/ie-bank-frontend.yml)]
  
### Trigger Events
- push to any branch deploys dev
- pull_request to the main branch deploys dev, uat and prod
- workflow_dispatch (manual trigger)
  
### Environment Variables
- KeyVault_DEV: Name of Azure Key Vault for Development
- KeyVault_UAT: Name of the Azure Key Vault for UAT
- KeyVault_PROD: Name of the Azure Key Vault for Production

### Build Job
Each environment has a separate build job that:
- *Runs on*: ubuntu-latest
- *Steps*:
  1. **Checks out the code**: Retrieves the latest code from the repository to ensure the workflow operates on the most up-to-date version of the application.
  2. **Sets up the required Node.js environment**: Configures the Node.js runtime environment to match the application's requirements, including version and caching for dependencies.
  3. **Installs dependencies and builds the application using environment-specific .env files**: Downloads all required libraries and packages, and compiles the frontend application with environment-specific configurations (e.g., Development, UAT, or Production).
  4. **Uploads the build artifacts for use in the corresponding deployment job**: Saves the compiled application files (e.g., dist-dev, dist-uat, dist-prod) as artifacts to be used in the subsequent deployment step for each environment.


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

The Test/Behavior Driven Development (TDD/BDD) strategy defines how the team designs tests and selects User Stories to drive development through testing. This section of the document provides an overview of the unit and functional tests for the IE Bank backend project. The tests are written using pytest and cover various aspects of the application's models, including user creation, account creation, and transactions.

- **TDD/BDD Strategy**: [TDD/BDD Strategy URL]

## Unit Tests

### Test Files
- test_model.py: Contains tests for the models in the application.

### Test Functions

#### 

#### test_create_multiple_accounts(init_database, sample_user)
- **User Story**:
  1. As a bank user, I want the ability to create and manage multiple bank accounts associated with my profile so that I can organize my finances and update account details as needed.

- **Description**: Tests creating multiple accounts for a single user.
- **Steps**:
  1. Retrieve the test user.
  2. Create two accounts for the user.
  3. Commit the accounts to the database.
  4. Retrieve the accounts and verify their details.
  5. Assert that the user has two accounts.

#### 

#### test_account_balance_default(init_database, sample_user)
- **User Story**:
  1. As a new user, I want to register for the application by providing my details so that I can create an account and start using the bank's services.


- **Description**: Tests the default balance of an account.
- **Steps**:
  1. Retrieve the test user.
  2. Create an account without specifying a balance.
  3. Commit the account to the database.
  4. Retrieve the account and assert that the balance is `0.0`.

#### 

#### test_account_creation_date(init_database, sample_user)


- **Description**: Tests the creation date of an account.
- **Steps**:
  1. Retrieve the test user.
  2. Create an account.
  3. Commit the account to the database.
  4. Retrieve the account and assert that the creation date is set and is a datetime object.

#### 

#### test_create_transaction(init_database, sample_user)
- **User Story**:
  1. As a bank user, I want to transfer money to other accounts by entering the recipient’s account number and the transfer amount so that I can manage payments or send funds. The system should ensure that the transfer amount does not exceed the available balance in my account.

- **Description**: Tests creating a transaction.
- **Steps**:
  1. Retrieve the test user.
  2. Create two accounts for the transaction.
  3. Commit the accounts to the database.
  4. Create a transaction between the two accounts.
  5. Commit the transaction to the database.
  6. Retrieve the transaction and verify its details.

#### 

#### test_create_user(init_database)


- **Description**: Tests creating a user.
- **Steps**:
  1. Create a user with specified details.
  2. Commit the user to the database.
  3. Retrieve the user and verify its details.

#### 

#### test_user_unique_constraints(init_database)


- **Description**: Tests that username and email must be unique.
- **Steps**:
  1. Create and commit the first user.
  2. Attempt to create another user with the same username and email.
  3. Assert that an IntegrityError is raised due to the unique constraints.

### Fixtures
- init_database: A fixture that initializes the database for testing.
- sample_user: A fixture that provides a sample user for testing.

## Functional Tests

### Test Files
- test_routes.py: Contains tests for the routes in the application.

### Test Functions

#### 

#### test_register(test_client, init_database)


- **Description**: Tests the registration of a new user.
- **Steps**:
  1. Send a POST request to the `/register` endpoint with user details.
  2. Assert that the response status code is `200`.
  3. Verify the response data contains the correct username and email.

#### 

#### test_login_user(test_client, init_database, sample_user)


- **Description**: Tests logging in a user.
- **Steps**:
  1. Send a POST request to the `/login` endpoint with user credentials.
  2. Assert that the response status code is `200`.
  3. Verify the response data contains a token and user details.

#### 

#### test_user_portal(test_client, init_database, sample_user)


- **Description**: Tests accessing the user portal.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Create accounts and transactions for the user.
  3. Send a GET request to the `/user_portal` endpoint with the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the correct accounts and transactions.

#### 

#### test_admin_portal(test_client, init_database, admin_user)


- **Description**: Tests accessing the admin portal.
- **Steps**:
  1. Log in the admin user and retrieve the token.
  2. Send a GET request to the `/admin_portal` endpoint with the token.
  3. Assert that the response status code is `200`.
  4. Verify the response data contains the list of users.

#### 

#### test_create_account(test_client, init_database, sample_user)


- **Description**: Tests creating a new account.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Send a POST request to the `/accounts` endpoint with account details and the token.
  3. Assert that the response status code is `200`.
  4. Verify the response data contains the correct account details.

#### 

#### test_get_account(test_client, init_database, sample_user)


- **Description**: Tests getting a specific account by ID.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Create a new account.
  3. Send a GET request to the `/accounts/{account.id}` endpoint with the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the correct account details.

#### 

#### test_update_account(test_client, init_database, sample_user)


- **Description**: Tests updating a specific account by ID.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Create a new account.
  3. Send a PUT request to the `/accounts/{account.id}` endpoint with updated account details and the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the updated account details.

#### 

test_delete_account(test_client, init_database, sample_user)


- **Description**: Tests deleting a specific account by ID.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Create a new account.
  3. Send a DELETE request to the `/accounts/{account.id}` endpoint with the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the deleted account details.

#### 

#### test_create_transaction(test_client, init_database, sample_user)


- **Description**: Tests creating a new transaction.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Create two accounts.
  3. Send a POST request to the `/transactions` endpoint with transaction details and the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the correct transaction details.

#### 

#### test_get_transactions(test_client, init_database, sample_user)


- **Description**: Tests getting all transactions for the logged-in user.
- **Steps**:
  1. Log in the user and retrieve the token.
  2. Create accounts and transactions.
  3. Send a GET request to the `/transactions` endpoint with the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the list of transactions.

#### 

#### test_create_user(test_client, init_database, admin_user)


- **Description**: Tests creating a new user by admin.
- **Steps**:
  1. Log in the admin user and retrieve the token.
  2. Send a POST request to the `/admin/users` endpoint with user details and the token.
  3. Assert that the response status code is `200`.
  4. Verify the response data contains the correct user details.

#### 

#### test_update_user(test_client, init_database, admin_user)


- **Description**: Tests updating a user by admin.
- **Steps**:
  1. Log in the admin user and retrieve the token.
  2. Create a user to update.
  3. Send a PUT request to the `/admin/users/{user.id}` endpoint with updated user details and the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the updated user details.

#### 

#### test_delete_user(test_client, init_database, admin_user)


- **Description**: Tests deleting a user by admin.
- **Steps**:
  1. Log in the admin user and retrieve the token.
  2. Create a user to delete.
  3. Send a DELETE request to the `/admin/users/{user.id}` endpoint with the token.
  4. Assert that the response status code is `200`.
  5. Verify the response data contains the deleted user details.

### Fixtures
- test_client: A fixture that provides a test client for making requests to the application.
- init_database: A fixture that initializes the database for testing.
- sample_user: A fixture that provides a sample user for testing.
- admin_user: A fixture that provides an admin user for testing.

### Running the Tests
To run the tests, use the following command:
```sh
pytest
```

This will execute all the test functions in the test_routes.pyfile and provide a summary of the test results.

---

## Release Strategy

The release strategy outlines the process, tools, and techniques used to release updates for both the frontend and backend of IE Bank.

- **Release Strategy**: [[Release Strategy URL](https://deviousdevops.github.io/ie-bank-2024/cloud_architect.html#release-strategy)]

### Inner Loop

The inner loop refers to the development cycle where developers make changes to the codebase, run tests locally, and ensure that their changes work as expected before committing the code. This loop is focused on rapid feedback and iteration to improve code quality and functionality.

1. *Code Changes*: Developers make changes to the codebase.
2. *Local Testing*: Developers run tests locally to verify their changes.
3. *Commit and Push*: Once satisfied, developers commit their changes and push them to the remote repository.

### Outer Loop
The outer loop refers to the CI/CD pipeline that takes over once the code is pushed to the remote repository. This loop ensures that the code is built, tested, and deployed in an automated and consistent manner across different environments.

1. *Trigger Events*: The workflow is triggered by push events, pull requests to the main branch, or manual dispatches.
2. *Build Job*: The code is checked out, dependencies are installed, and the code is linted and tested.
3. *Artifact Upload*: The build artifacts are uploaded for use in deployment jobs.
4. *Deploy to Development*: The build artifacts are downloaded, and the application is deployed to the Development environment.
5. *Deploy to UAT*: The build artifacts are downloaded, and the application is deployed to the UAT environment.
6. *Run Postman Tests*: Postman tests are run on the UAT environment to verify the deployment.
7. *Deploy to Production*: The build artifacts are downloaded, and the application is deployed to the Production environment.

### Outer Loop
The outer loop automates the CI/CD pipeline for building, testing, and deploying the frontend to Azure Static Web Apps across environments.

1. **Trigger Events**: Triggered by push, pull requests to main, or manual dispatch (workflow_dispatch).
2. **Build Jobs**:
   - Check out code, set up Node.js, install dependencies, build with .env files, and upload artifacts (dist-dev, dist-uat, dist-prod).
3. **Deploy to Development**:
   - Download artifact (node-app-dev), fetch deployment token from Development Key Vault, and deploy to Azure Static Web App.
4. **Deploy to UAT**:
   - After build-uat and deploy-dev, download artifact (node-app-uat), fetch UAT token, and deploy.
5. **Deploy to Production**:
   - After build-prod and deploy-uat, download artifact (node-app-prod), fetch Production token, and deploy.
6. **Output URLs**: Log Static Web App URLs for each environment.

---

## Continuous Delivery (CD) Workflow for Frontend

The CD workflow for the frontend details the deployment pipeline for delivering updates to the frontend application continuously. After the build jobs are complete, the workflow deploys the application to the development, user acceptance testing (UAT), and production environments.

- **CD Workflow for Frontend**: [[CD Workflow for Frontend URL](https://github.com/deviousdevops/ie-bank-fe-2024/blob/main/.github/workflows/ie-bank-frontend.yml)]
### Deploy to Development Environment
- *Runs on*: ubuntu-latest
- *Needs*: build-dev
- *Environment*: Development
- *Outputs*: static_webapp_url - The Static Web App URL for the development environment.
- *Steps*:
  1. Download Artifact: Downloads the built artifact (node-app-dev) from the build-dev job.
  2. Log in to Azure: Authenticates using the AZURE_CREDENTIALS GitHub secret.
  3. Fetch Deployment Token: Retrieves the deployment token for the development environment from the Development Key Vault.
  4. Deploy to Azure Static Web App: Uploads the application to the development Static Web App.
  5. Output Web App URL: Outputs the Static Web App URL to the workflow logs for easy reference.
  
### Deploy to UAT Environment
- *Runs on*: ubuntu-latest
- *Needs*: build-uat, deploy-dev
- *Environment*: UAT
- *Outputs*: static_webapp_url - The Static Web App URL for the UAT environment.
- *Steps*:
  1. **Download Artifact**: Downloads the built artifact (node-app-uat) from the build-uat job.
  2. **Log in to Azure**: Authenticates using the AZURE_CREDENTIALS GitHub secret.
  3. **Fetch Deployment Token**: Retrieves the deployment token for the UAT environment from the UAT Key Vault.
  4. **Deploy to Azure Static Web App**: Uploads the application to the UAT Static Web App.
  5. **Output Web App URL**: Outputs the Static Web App URL to the workflow logs for easy reference.

### Deploy to Production Environment
- *Runs on*: ubuntu-latest
- *Needs*: build-prod, deploy-uat
- *Environment*: Production
- *Outputs*: static_webapp_url - The Static Web App URL for the production environment.
- *Steps*:
  1. **Download Artifact**: Downloads the built artifact (node-app-prod) from the build-prod job.
  2. **Log in to Azure**: Authenticates using the AZURE_CREDENTIALS GitHub secret.
  3. **Fetch Deployment Token**: Retrieves the deployment token for the production environment from the Production Key Vault.
  4. **Deploy to Azure Static Web App**: Uploads the application to the production Static Web App.
  5. **Output Web App URL**: Outputs the Static Web App URL to the workflow logs for easy reference.

---

## Continuous Delivery (CD) Workflow for Backend

The CD workflow for the backend describes the deployment pipeline and its steps for delivering backend updates continuously. After the build job is done, it the workflow deploys to the development, user acceptance testing, and production environments simultaneously.

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

