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

Overview

The GitHub Hardening Strategy focusses on securing the repository environment, protecting sensitive data, and promoting secure development methods. We make sure the repository follows best practices while lowering the risks of vulnerabilities and data breaches by using GitHub's built-in tools and procedures.

Key Components

1- Secret Scanning
Set up to automatically identify private data in pull requests and commits, such as API keys, passwords, and tokens.
Looks out on every branch and notifies developers when anything needs to be fixed. By preventing sensitive information from unintentionally entering the codebase, secret scanning lowers possible risks.

2- Push Protection
Stops contributors from submitting commits containing secrets.
It also notifies users when secrets are discovered and allows overrides only in appropriate situations. This proactive security technique avoids issues before they happen. 

3- CodeQL Scanning
A codeql.yml workflow was added to check the codebase for faults and vulnerabilities.
It ensures early identification of any security problems by running automatically on every change and pull request. Early detection of code problems lowers the possibility that vulnerabilities may find their way into production.

4- OSSF Scorecard
Set up the OSSF Scorecard workflow to assess repository security procedures, including dependency updates and branch protection.
It creates reports that show areas for development and security strengths. The OSSF scorecard aids in setting priorities for improvements and offers a measurable analysis of the repository's security measures. 

5- CODEOWNERS
A CODEOWNERS file was implemented in order to designate reviewers for particular codebase sections.
It makes sure that before merging, important regions are examined by necessary team members. This guarantees excellent code reviews and establishes open responsibility.


- **GitHub Hardening Strategy**: [GitHub Hardening Strategy URL]

---

## Secrets Management Strategy

This section outlines the approach taken to securely manage and store secrets, such as API keys, passwords, and certificates, to prevent unauthorized access.

- **Secrets Management Strategy**: [Secrets Management Strategy URL]

---

## Implemented Security Guides

This section provides a description of the 10 security guides that have been implemented to ensure the security of the development, deployment, and production environments.

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
