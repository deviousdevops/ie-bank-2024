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