---
layout: default
title: "Site Reliability Engineer Documentation"
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

# Site Reliability Engineer Documentation

Welcome to the Site Reliability Engineer's section of the IE BANK documentation. Below you will find the key sections that describe the service level agreements, objectives, monitoring strategies, and incident response designs that are essential for ensuring the reliability and availability of IE BANK's systems.

## Table of Contents
- [Service Level Agreement (SLA)](#service-level-agreement-sla)
- [Service Level Objectives (SLO)](#service-level-objectives-slo)
- [Service Level Indicators (SLI)](#service-level-indicators-sli)
- [Monitoring Strategy](#monitoring-strategy)
- [Incident Response Design](#incident-response-design)
- [Capacity Design](#capacity-design)
- [Performance Efficiency](#performance-efficiency)
- [Cost Opimisation and FinOps](#cost-opimisation-finops)
- [Operational Excellence and Release Engineering](#operation-excellence)
- [Site Reliability Engineering Design](#site-reliability-engineering-design)

---

## Service Level Agreement (SLA)

This section defines the Service Level Agreement (SLA) for the current version of the IE BANK application, detailing the level of service the system guarantees to users.

- **SLA Contract**: [SLA Contract URL]

---

## Service Level Objectives (SLO)

  - Objective 1 - User Authentication Response Time:  99% of user login requests will be processed in under 2 seconds
  - Objective 2 - Transaction Processing Time - 95% of money transfer transactions will be completed within 3 seconds
  - Objective 3 - Database Query Performance: 90% of database queries executed against the PostgreSQL database will complete in under 500 milliseconds
  - Objective 4 - HTTP Requests: 95% of HTTP requests for the IE Bank static website will be processed in under 2 seconds.
  - Objective 5 - System Availability: The overall system (frontend and backend) will maintain an uptime of 99.9% over any given month

---

## Service Level Indicators (SLI)


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

---

## Monitoring Strategy

This section explains the design of the monitoring strategy, including the tools and processes used to ensure continuous monitoring of the system to meet the defined SLIs and SLOs.

- **Monitoring Strategy Design**: [Monitoring Strategy Design URL]

---

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

---

## Site Reliability Engineering Design

This section provides an overview of the Site Reliability Engineering (SRE) design, including best practices, tools, and strategies used to ensure the system’s reliability, scalability, and performance.

- **SRE Design**: [SRE Design URL]

---

Feel free to explore each section for detailed documentation.

<div class="previous-section-link"> 
  <a href="cybersecurity_engineer.html">Previous</a>
</div>

<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="index.html">Next</a>
</div>
