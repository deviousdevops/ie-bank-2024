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
- [Performance Efficiency](#performance-efficiency-design)
- [Cost Opimisation and FinOps](#cost-opimisation-design)
- [Operational Excellence and Release Engineering](#operation-excellence-&-release-engineering-design)
- [Site Reliability Engineering Design](#reliability-design)

---

## Service Level Agreement (SLA)

-----------------------------------

Effective Date: 08/11/2024\
Version: 1.0

### 1\. Introduction

This Service Level Agreement (SLA) outlines the service commitments provided by IE Bank regarding the availability, performance, and support of its banking application hosted on Azure. This agreement is applicable to all users accessing the application through the IE Bank platform.

### 2\. Scope of Services

This SLA covers the following components of the IE Bank application:

-   Frontend: Azure Static Website

-   Backend: Linux Container App Service

-   Database: PostgreSQL

-   Credentials Management: Azure Key Vault

-   Monitoring: Azure Log Analytics Workspace and Azure Application Insights

-   Container Management: Docker Container Registry

*NOTE*: These services are interconnected, and any degradation in one component may affect the overall system performance. The availability and performance metrics in this SLA are contingent on the proper functioning of all dependencies, including all Azure Services used.

3\. Service Availability

IE Bank commits to the following availability standards:

-   Overall System Availability: 99.9% uptime per month.

-   Frontend (Azure Static Website): 99.9% uptime per month.

-   Backend (Linux Container App Service): 99.9% uptime per month.

-   Database (PostgreSQL): 99.9% uptime per month.

-   Credentials Management (Azure Key Vault): 99.9% uptime per month.

-   Monitoring Services (Azure Log Analytics and Application Insights): 99.9% uptime per month.

### 4\. Performance Metrics

IE Bank will strive to meet the following performance metrics:

-   User Authentication Response Time: 99% of login requests will be processed in under 2 seconds.

-   Transaction Processing Time: 95% of money transfer transactions will be completed within 3 seconds.

-   CPU Usage: Ensure CPU usage stays below 80% for 99% of the time over a given period.

-   HTTP Requests: 95% of HTTP requests for the IE Bank static website will be processed in under 5 seconds.

-   HTTP Error Rate: 99% of HTTP requests for the IE Bank website will be processed without errors (status code 4xx or 5xx).

### 5\. Penalties for Non-Compliance

If IE Bank fails to meet the specified availability or performance metrics, customers may be eligible for service credits as follows:

-   For each hour of downtime beyond the SLA of 99.9% availability, users will receive a 5% credit on their monthly fees, up to a maximum of 50%.

-   If any performance metric falls below the defined SLOs for two consecutive months, customers are entitled to request a service review and may receive service credits proportional to the impact, up to 30% of monthly fees.

### 7\. Monitoring and Reporting

-   IE Bank will utilise Azure Log Analytics Workspace and Azure Application Insights to monitor service performance and availability.

-   A monthly report will be generated and shared with stakeholders, detailing uptime percentages, performance metrics, and any incidents that occurred.

### 8\. Review and Revision of SLA

This SLA will be reviewed quarterly, or upon significant changes to service offerings or infrastructure. Any amendments to this SLA will be communicated to all stakeholders.

### 9\. Acceptance

By using the IE Bank application, users agree to the terms outlined in this SLA;

* * * * *

Signatures

Customer: _______________        IE_Bank_CEO:  _______________

---

## Service Level Objectives (SLO)

-   Objective 1 - User Authentication Response Time: 99% of user login requests processed in under 2 seconds

-   Objective 2 - Transaction Processing Time: 95% of money transfer transactions completed within 2 seconds

-   Objective 3 - CPU USAGE: Ensure CPU usage stays below 80% for 99% of the time over a given period.

-   Objective 4 - HTTP Requests: 95% of HTTP requests for the IE Bank static website processed in under 5 seconds.

-   Objective 5 - HTTP Error Rate: 99% of HTTP requests for the IE Bank website processed without errors (4xx or 5xx).
---

## Service Level Indicators (SLI)

SLO 1: SLI Type: Latency\
SLI Specification: (Number of login requests <2s) / (Total login requests) ≥ 99%

SLO 2: SLI Type: Latency\
SLI Specification: (Number of transfers <2s) / (Total transfers) ≥ 95%

SLO 3: SLI Type: Resource Utilization\
SLI Specification: (Time CPU<80%) / (Total time) ≥ 99%

SLO 4: SLI Type: Latency\
SLI Specification: (HTTP requests <5s) / (Total requests) ≥ 95%

SLO 5: SLI Type: Error Rate (Reliability)\
SLI Specification: (Successful HTTP req [non-4xx/5xx])/(Total HTTP req) ≥ 99%



## Monitoring Strategy

Goal: Ensure high availability, performance, and fault tolerance through proactive detection of issues, performance optimization, and support incident management for rapid response.

Azure Services for Monitoring:

-   Log Analytics Workspace: Centralized logging and analytics for logs and metrics. Tracking will focus primarily on the database performance, like checking how long it may take to execute some queries and storing logs. Alerts will also be applied in case there are any performance problems.

-   Application Insights: Plays a crucial role in our monitoring strategy by offering comprehensive performance tracking for both the frontend (Vue.js) and backend (Python) of our application. By integrating its SDKs into our codebase, we can monitor key metrics like page load times, response times, error rates, and user interactions. This real-time data is essential for quickly detecting issues and ensuring we meet our Service Level Objectives (SLOs), such as processing 99% of user login requests in under 2 seconds and completing 95% of money transfer transactions within 2 seconds. Track HTTP error rates, ensuring 99% of requests are processed without errors (4xx or 5xx status codes). This will support proactive error detection and resolution.

-   Azure Workbooks: Enhance our ability to visualize and analyze the collected metrics and logs. Our workbook will display critical data on user activities, system performance, and transaction success rates, mostly being focused on our SLOs so it can be presented as a visualiser to stakeholders. This helps us monitor user behavior, track the performance of key functionalities like the money transfer process, and make data-driven decisions for optimization and capacity planning.

Monitoring Methods:

#### 1\. Application Monitoring: Ensure the application's frontend (Vue.js) and backend (Python) are functioning optimally.

-   Data Needs:

-   Frontend: Page load times, navigation events, potential errors.

-   Backend: Response times, error rates, database query times.

-   Implementation:

-   Integrate Application Insights into both frontend and backend code.

-   Track key metrics such as response time, error rates, and user interactions.

-   Configure logging for user actions, page load times, and API calls.

#### 2\. Capability Monitoring: Monitor user activities and key functionalities such as the "money transfer process."

-   Metrics to Monitor:

-   Transaction success rates, user session counts, session durations, User actions during the money transfer process, HTTP error rate, CPU usage trends.

-   Implementation:

-   Use Application Insights custom events to track user journeys.

-   Set up custom events and metrics in Application Insights to monitor CPU usage and HTTP error rates. Use alerts to detect when thresholds are not met, ensuring rapid response.

-   Create Azure Workbooks to visualize user behavior analytics.

#### 3\. Fault Tolerance and Infrastructure Monitoring: Monitor system health, resource utilisation, and fault tolerance.

-   Metrics to Monitor:

-   CPU and memory utilization, network bandwidth, disk space, container health.

-   Implementation:

-   Use Azure Monitor and Log Analytics to track infrastructure metrics.

-   Monitor CPU usage, memory consumption, network latency, and disk I/O.

Data Collection & Analysis: All data is collected through Azure log analytics and Application Insights. Logs from Python application to A.I. and Log Analytics. Diagnostic settings for App Service monitor CPU usage and HTTP error rates. We've implemented comprehensive logging across our stack, from PostgreSQL database metrics to Container Registry events, ensuring full visibility of our application's health. Our alert system, powered by a Logic App with Slack integration, evaluates metrics every minute within 5-minute windows - a balance chosen to minimize false positives while maintaining responsive incident detection. Data is visualised via our workbook and insights.

Management Controls

-   Access to monitoring tools and data will be restricted to authorized personnel only.

-   Quarterly audits will be conducted to ensure compliance with data privacy policies.

-   Service Level Agreement will be reviewed on a quarterly basis. 

Decision Approach

-   Many of the important and necessary decisions such as scaling or infrastructure changes will be based on historical data trends and predictive analytics that are determined using Azure Monitoring services and the workbooks provided to stakeholders. 

-   Real-time alerts will notify engineers if CPU usage exceeds 80% or if HTTP error rates surpass acceptable thresholds.

-   Monthly reviews of monitoring reports will guide optimizations and capacity planning.

Service Mapping:

![Imagen de WhatsApp 2024-12-08 a las 18 18 19_7d447fb5](https://github.com/user-attachments/assets/cb39bfe1-cad7-485a-ab4e-1d5fc06cfb96)

## Incident Response Design

Version: 1.0

Effective Date: 08/11/2024

Last Reviewed: 27/11/2024

1\. Purpose

This document defines the incident response plan for the IE Bank application, detailing the detection, response, and resolution processes for incidents. The main goal is to minimize downtime, adhere to SLA commitments, and ensure customer satisfaction.

2\. Incident Response Objectives

Minimize downtime: Maintain 99.9% system uptime.

Ensure SLO adherence: Address login latency, transaction processing, and correct CPU utilisation.

Rapid resolution: Detect and resolve incidents efficiently to mitigate customer impact.

Effective communication: Keep internal teams and stakeholders informed during incidents.

3\. Detection

Tools:

-   Application Insights: Detect infrastructure and latency issues in login, transaction processing, and HTTP requests.

-   Log Analytics Workspace: Collect logs and performance metrics.

-   Diagnostic Settings: Send logs from App Services, PostgreSQL, and Container Registry to Log Analytics Workspace.

Real-Time Alerts:

User login latency exceeds 2 seconds

-   Implemented as Login-Response-Time-Alert

-   Triggers when request duration > 2000ms

-   Monitored through Application Insights

  HTTP error rate spikes

-   Implemented as HTTP-Error-Rate-Alert

-   Triggers when HTTP 4xx errors > 1%

-   Monitored on the Web App

  CPU Usage Alert

-   Triggers when CPU usage > 80%

-   Monitored on the App Service Plan

<img width="539" alt="Screenshot 2024-12-08 at 18 25 05" src="https://github.com/user-attachments/assets/993a8c59-4502-493a-b950-ba30b4bc7bc4">

Image demonstrates alerts being handled and sent to Slack channel for intervention


4 Incident Response Steps

Detection:

-   Real-time alert triggered by Azure Monitor or Application Insights.

-   Example: Application Insights logs "CPU usage has exceeded 80%"

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

On-Call Engineer (Andres)  Respond to alerts, investigate the issue, and implement fixes.

DevOps Engineer (Sofia)  Resolve infrastructure-level issues (e.g., scaling, container registry).

Database Admin (Luis)  Address database performance issues (e.g., slow queries, connection errors).

SRE Team Lead (Edou)  Conduct incident retrospectives and implement process improvements.

6\. Key Tools and Automation

6.1 Tools

-   Application Insights: Monitors application performance and error rates.

-   Log Analytics Workspace: Stores diagnostic logs for database and application monitoring.

-   Azure Workbooks/Dashboards: Visualizes real-time metrics and incident status.

6.2 Automation

-   Slack Integration: Notify teams of incidents and escalate unacknowledged alerts.

-   Azure Resource Health: Confirm Azure service health during incidents.

7\. Metrics for Measuring Incident Response

Metric  Description

-   Time to Detect (TTD): Time taken to detect an incident after it occurs.

-   Time to Acknowledge (TTA):  Time taken for an on-call engineer to acknowledge the incident.

-   Time to Resolve (TTR): Time taken to fully resolve the incident.

8\. Post-Incident Review Process

Root Cause Analysis:

-   Identify the root cause (e.g., database query inefficiency, container crash).

Impact Analysis:

-   Assess the impact on SLOs and SLAs (e.g., downtime or latency breaches).

Preventive Measures:

-   Update alert thresholds or implement new monitoring techniques.

-   Additionally, update any necessary documentation to keep things up to date and prevent it from happening again

9\. Review, Revision and Acceptance

As same as the SLA, this incident response plan will be reviewed quarterly. 

---

## Capacity Design 
--------------------

Overview: The capacity design ensures that the IE Bank application can handle current and projected workloads efficiently, meet performance targets, and remain cost-effective. This includes analyzing compute, database, and supporting services, defining scaling policies, and applying cost controls.

Initial Cost Estimation & Resources: All costs were determined from the Azure website, using US location as Central Spain wouldn't always show prices.

Compute Resources (App Service Plan - B1 Tier):\
    Cost per instance: ~$13/month\
    Initial capacity: 1 instance\
    Projected scaling (if increased demand for our bank): Up to 3 instances based on load.

Database Resources (PostgreSQL Flexible Server Standard_B1ms):\
    Base cost: ~$14/month\
    Backup storage: Included for 7 days

Supporting Services:

-   Application Insights: 5GB/month ingestion, 90-day prod retention, 30-day non-prod retention

-   Container Registry (Basic): ~$5/month

-   Static Web App: Free tier (dev), Standard tier (production)

Resource Optimization Strategies:

Code Performance Optimization: 

-   General Optimizations: Reduce DB hits with in-memory caching (e.g., Azure Redis), optimize hot paths (login/transaction), async/await for I/O-bound ops. These optimisations would have to be discussed with engineers.

  Infrastructure Optimization:

App Service:

-   Always On in production only to ensure responsiveness in prod, reduce costs in non-prod.

-   Auto-scale based on CPU metrics: Scale out when CPU > 75% for 10 min, scale in when CPU < 25% for 30 min.

-   Min Instances: 1, Max: 3, Cool-down: 10 min.

  Database:

-   Connection pooling to maximize efficiency.

-   Use query performance insights to optimize slow queries.

-   Enable automatic tuning for indexes and consider higher tiers if sustained CPU >80%, connection >80% limit, or storage >80%.

Capacity Monitoring & Alerts:

Performance Metrics:

-   Login Response <2s (SLO), alert if >1s for 5 min.

-   Database connections: monitor failed connections, pool exhaustion, slow queries.

  Scaling Thresholds:

-   App Service: Scale out at CPU>75%/10min, Scale in at CPU<25%/30min, max 3 instances.

-   PostgreSQL: Upgrade if CPU>80%, connections>80%, storage>80%.

Capacity Model Maintenance:

-   Weekly: Monitor utilization vs SLOs, track costs.

-   Monthly: Capacity planning reviews, adjust resource sizing.

-   Quarterly: Full cost model review, update forecasts, evaluate scaling strategies.

* * * * *

## Performance Efficiency Design 
----------------------------------

Performance Targets & Requirements:

-   User Experience Targets:

-   Login Flow: Response <2s, up to 100 concurrent users/instance, 30-min session timeout

-   Transaction Processing: API response <1s, DB query <500ms, Max 50 concurrent transactions/instance

Resource-Specific Requirements:

-   App Service: Memory<80%, CPU<75%, Request queue<10, 2xx>99%, 5xx<0.1%

-   Application Insights: Retention 90 days (prod), 30 days (non-prod), real-time metrics

Performance Optimization Strategies:

Frontend (Vue.js + CDN):

-   Azure CDN for static assets, enable compression, caching static resources.

-   Client-side caching, optimize bundle sizes, lazy loading for components.

  Backend (Python APIs):

-   Response compression, async/await patterns, API response caching.

-   Connection pooling, index optimization, query tuning, data partitioning.

Environment-Specific Configurations:

-   Dev: Basic diagnostics, reduced logging, basic performance monitoring.

-   UAT: Full monitoring, performance testing, synthetic transactions.

-   Prod: Advanced diagnostics, real-time alerts, SLO dashboard.

Performance Monitoring & Testing:

-   Application Performance: Request duration, dependency tracking, exceptions, custom counters.

-   Resource Monitoring: CPU, memory, network, disk I/O.

-   Load Testing: Baseline, peak, endurance, stress testing.

-   Continuous Testing: Integration with CI/CD, automated performance regression tests.

Performance Optimization Lifecycle:

-   Weekly: Analyze metrics, identify bottlenecks.

-   Monthly: Trend analysis, capacity updates, optimization recommendations.

-   Quarterly: Full performance audit, architecture review, technology stack updates.

-   Short-Term Optimizations: Query tuning, cache optimization, scaling.

-   Long-Term: Architecture enhancements, technology upgrades, infra modernization.

* * * * *

## Cost Optimization Design 
-----------------------------

Cost Model & Financial Responsibility:

-   Direct Infrastructure Costs: App Service, PostgreSQL Flexible Server, Container Registry, Application Insights, Static Web App, Log Analytics Workspace (running queries).

-   Indirect Costs: Dev & maintenance, support, training, monitoring.

-   Cost Monitoring: Use Azure Cost Management + Billing, 90-day production data retention, 30-day non-prod.

Environment-Specific Cost Controls:

-   Dev: Reduced logging, minimal redundancy, auto-shutdown off-hours.

-   UAT: Shared resources where possible, on-demand scaling, limited retention.

-   Prod: Full monitoring with optimized retention, cost-effective scaling rules, SLO monitoring considering cost.

Cost Optimization Lifecycle:

-   Weekly: Resource utilization analysis, unused resource identification, cost anomaly detection.

-   Monthly: Budget vs actual analysis, resource optimization opportunities, scaling pattern analysis.

-   Quarterly: Full cost model review, long-term commitment evaluation, technology stack cost assessment.

Continuous Improvement (CI):

-   Short-Term: Resource right-sizing, immediate cost reductions, performance-cost trade-offs.

-   Long-Term: Reserved instance evaluation, regional pricing optimization

-   Cost Guardrails:Set spending limits and alert thresholds.

-   Monitoring: Metrics (utilization, cost/transaction), daily cost tracking, trend analysis, forecast vs actual.

* * * * *

## Operational Excellence & Release Engineering Design 
--------------------------------------------------------

DevOps Culture & Team Structure:

-   Core Dev Team: Frontend, Backend, Infrastructure, QA engineers.

-   Support: DevOps engineers, Security team, DBAs, Release managers.

-   Collaboration: Daily standups, weekly tech sync, monthly architecture reviews, quarterly planning.

-   Knowledge Sharing: Technical docs, internal wikis, pair programming, cross-training.

Development Standards:

-   Code Management: GitHub repos, trunk based branching, code reviews.

-   Quality Gates: unit test >80% coverage (however, this depends on the fullstack), integration tests, security scans.

-   Documentation: Architecture diagrams, API specs, DB schemas, infrastructure docs, runbooks, incident response, deployment guides, recovery procedures.

Release Engineering:

Environment Strategy:

-   Dev: Individual dev instances, shared CI.

-   UAT: Integration, performance, security testing.

-   Prod: Blue-green deployment, rollback procedures, production monitoring.

  Deployment Pipeline (CI/CD):

-   Build: Compile code, bundle assets, create container images, validate IaC.

-   Test: Unit, integration, security, performance tests.

-   Deploy: Dev→UAT→Prod with approvals, post-deployment validation.

Monitoring & Observability:

-   Application Monitoring: Performance metrics, error rates, resource utilization, user experience.

-   Business Metrics: Transaction volumes, user activity, feature usage, error patterns.

-   Infrastructure Monitoring: CPU, memory, network, storage, security events, compliance metrics.

-   Security Monitoring: Access patterns, vulnerability scanning.

-   Dashboards & Alerts: Unified, real-time views, Slack/email notifications.

Incident Management:

-   Severity-based classification, escalation paths, communication templates.

-   Resolution Steps: Assess, investigate, remediate, verify.

-   Post-Incident Review: RCA, corrective measures, doc updates, process improvements.

Automation Strategy:

-   Infrastructure as Code (IaC): Resource provisioning, configuration management, secret management, network configuration.

-   Operational Tasks: Automated backups, scaling, health checks, maintenance tasks.

-   Deployment Automation: Automated builds using the workflows, tests, scripts, validation checks, rollback procedures.

Continuous Improvement:

-   Post-deployment reviews, incident retrospectives, performance reviews, customer feedback.

-   Process Optimization: Automation opportunities, tool evaluations, training needs.

* * * * *

## Reliability Design 
-----------------------

Business Requirements & Reliability Targets:

-   Availability SLOs: Overall 99.9%, Core banking 99.95%, Non-critical 99.5%.

-   Performance Targets: Transaction <2s, API <1s, DB query <500ms.

-   Recovery Objectives: RTO=4h (critical), 8h (non-critical); RPO=5m (transactions),1h(user),24h(analytics).

Resilience Strategy:

-   Component Redundancy: Multiple app instances, load balancing, cross-region deployment.

-   Database Layer: Primary-secondary replication, point-in-time backups, geographic redundancy.

-   Fault Isolation: Circuit breakers for external calls, bulkhead patterns for resource isolation.

Recovery Design:

-   Backup Strategy: Transaction logs every 5min, full DB daily, config backup on change.

-   Disaster Recovery: Automated/manual failover, data consistency validation, system restoration steps, DR drills.

-   Failover Process: Automated triggers, manual procedures, verify data integrity.

Operational Reliability:

-   Monitoring & Alerting: Health (system vitals, performance metrics, error rates), Alert Management (severity, notification), Incident Response (initial assessment, mitigation, communication, RCA).

-   Post-Incident: RCA, corrective measures, doc updates, process improvement.

Testing & Validation:

-   Reliability Testing: Unit, integration, load, stress tests.

-   Chaos Engineering: Failure injection, network degradation, resource exhaustion, overload scenarios.

-   Recovery Testing: Backup restore validations, DR drills measuring RTO/RPO, performance validation post-restore.

Continuous Improvement:

-   Performance Optimization: Resource utilization, query tuning, caching, pooling.

-   Capacity Planning: Growth projections, scaling resources, infrastructure expansion.

-   Process Enhancement: Updated runbooks, best practices, lessons learned, training exercises.

Compliance & Security:

-   Data Protection: Encryption at rest/in transit, access controls, audit logging, data retention policies.

-   Security Measures: Authentication, authorization, threat detection, vulnerability management.

-   Business Continuity: Impact analysis, risk assessment, mitigation strategies, crisis management, stakeholder communication, emergency response.

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
