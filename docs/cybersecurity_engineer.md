---
layout: default
title: "Cybersecurity Engineer Documentation"
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

# Cybersecurity Engineer Documentation

Welcome to the Cybersecurity Engineer's section of the IE BANK documentation. Below you will find the key sections detailing the strategies and guides implemented to ensure the security of IE BANK's systems and data.

## Table of Contents
- [GitHub Hardening Strategy](#github-hardening-strategy)
- [Secrets Management Strategy](#secrets-management-strategy)
- [Implemented Security Guides](#implemented-security-guides)

---

## GitHub Hardening Strategy

- **GitHub Hardening Strategy**: [GitHub Hardening Strategy URL]

Overview

The GitHub Hardening Strategy focusses on securing the repository environment, protecting sensitive data, and promoting secure development methods. We make sure the repository follows best practices while lowering the risks of vulnerabilities and data breaches by using GitHub's built-in tools and procedures.

Key Components

1- Secret Scanning:
Set up to automatically identify private data in pull requests and commits, such as API keys, passwords, and tokens.
Looks out on every branch and notifies developers when anything needs to be fixed. By preventing sensitive information from unintentionally entering the codebase, secret scanning lowers possible risks.

2- Push Protection:
Stops contributors from submitting commits containing secrets.
It also notifies users when secrets are discovered and allows overrides only in appropriate situations. This proactive security technique avoids issues before they happen. 

3- CodeQL Scanning:
A codeql.yml workflow was added to check the codebase for faults and vulnerabilities.
It ensures early identification of any security problems by running automatically on every change and pull request. Early detection of code problems lowers the possibility that vulnerabilities may find their way into production.

4- OSSF Scorecard:
Set up the OSSF Scorecard workflow to assess repository security procedures, including dependency updates and branch protection.
It creates reports that show areas for development and security strengths. The OSSF scorecard aids in setting priorities for improvements and offers a measurable analysis of the repository's security measures. 

5- CODEOWNERS:
A CODEOWNERS file was implemented in order to designate reviewers for particular codebase sections.
It makes sure that before merging, important regions are examined by necessary team members. This guarantees excellent code reviews and establishes open responsibility.



---

## Secrets Management Strategy

- **Secrets Management Strategy**: [Secrets Management Strategy URL]

Overview

Protecting sensitive information from unauthorised access, such as database passwords, access tokens, and API keys, requires effective secret management. The Secrets Management Strategy guarantees that secrets are handled effectively across environments, kept safely, and accessible only by authorised systems.

Key Components

1- Azure Key Vault:
Its is the central solution for securely storing and managing sensitive information. It ensures:
- Centralized Storage: All secrets, including API tokens, container registry access keys, and database credentials, are safely kept in one location.
- Access Control: To make sure that only authorised users and services may access secrets, Role-Based Access Control, or RBAC, is implemented. 
- Rotating secrets automatically lowers the possibility of using out-of-date or hacked credentials.

2- Bicep Templates:
Secures environment deployment and configuration are automated using Bicep templates, which include:
- Establishing Key Vault access rules to guarantee safe access and storage.
- Providing infrastructure across environments (e.g., dev, uat, and prod) with uniform security settings.
- Automating the setup procedure to enforce standard practices.

3. Integration with GitHub Actions:
CI/CD pipelines safely include secrets kept in Azure Key Vault:
- Secrets are dynamically obtained while the pipeline is running.
- To prevent them from being hardcoded in the codebase or revealed in plain text, these secrets are sent to programs through environment variables.


---

## Implemented Security Guides

Overview

This section details the security guides and practices implemented to ensure a robust and secure environment for IE BANK’s development processes. Each guide highlights its purpose, implementation, and the specific files or settings where it has been applied.

Key Components

1- Secret Scanning:

Purpose:
Detect and prevent sensitive information, such as API keys and passwords, from being committed to the repository.

Implementation:
Enabled Secret Scanning in the GitHub repository. Actively monitors all branches for exposed secrets and sends alerts when sensitive data is detected.
File/Setting Link:
Secret Scanning Configuration

2. Dependency Updates
Purpose:
Keep dependencies secure by regularly updating libraries and packages to the latest versions.

Implementation:

Configured Dependabot to automatically check for and notify about dependency vulnerabilities.
Enabled automated pull requests for resolving vulnerabilities.
File/Setting Links:

Dependabot Configuration
Example Alert
3. Code Scanning:
Purpose:
Identify vulnerabilities in the codebase using automated tools.
Implementation:
Set up CodeQL to perform security and quality analysis on every commit and pull request.
Configured workflows to run scans automatically and provide detailed reports.
File/Setting Links:

CodeQL Workflow
Example CodeQL Run
4. Branch Protection
Purpose:
Safeguard the main branch by enforcing rules such as mandatory pull request reviews.

Implementation:

Enabled Branch Protection Rules to ensure secure collaboration and prevent unauthorized changes.
File/Setting Link:
Branch Protection Settings

5. OSSF Scorecard
Purpose:
Evaluate the repository’s security health using industry-recognized metrics.

Implementation:

Configured the OSSF Scorecard workflow to regularly evaluate repository security and recommend improvements.
File/Setting Links:

OSSF Scorecard Workflow
Example OSSF Scorecard Run

- **Implemented Security Guides**: [Implemented Security Guides URL]

---

Feel free to explore each section for detailed documentation.

<div class="previous-section-link"> 
  <a href="infrastructure_developers.html">Previous</a>
</div>

<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="site_reliability_engineers.html">Next</a>
</div>
