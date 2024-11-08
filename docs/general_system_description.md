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

- Define and document at least 5 SLOs, including:
  - Objective 1: [Description of the objective]
  - Objective 2: [Description of the objective]
  - Objective 3: [Description of the objective]
  - Objective 4: [Description of the objective]
  - Objective 5: [Description of the objective]

### Service Level Indicators (SLIs)

- For each SLO, document the corresponding SLIs and metrics to measure:
  - SLO 1: [SLI Description and Metrics]
  - SLO 2: [SLI Description and Metrics]
  - SLO 3: [SLI Description and Metrics]
  - SLO 4: [SLI Description and Metrics]
  - SLO 5: [SLI Description and Metrics]

### Azure Services Utilized

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