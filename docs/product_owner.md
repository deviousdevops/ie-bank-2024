---
layout: default
title: "Product Owner Documentation"
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

# Product Owner Documentation

Welcome to the Product Owner's section of the IE BANK documentation. Below you will find the key sections that describe the responsibilities, vision, and strategy that guide the product development process.

## Table of Contents
- [Product Vision & Mission Statements](#product-vision--mission-statements)
- [Product Vision Board](#product-vision-board)
- [Minimum Viable Product (MVP) and Requirements](#minimum-viable-product-mvp-and-requirements)
- [Objectives and Key Results (OKRs)](#objectives-and-key-results-okrs)
- [Scrum Methodology](#scrum-methodology)
- [Collaboration Strategy](#collaboration-strategy)

---

## Product Vision & Mission Statements

The Product Owner is responsible for articulating the vision and mission of the IE BANK product. These statements are key to aligning the team and stakeholders with the long-term goals and purpose of the product.

- **Product Vision**: Our product envisions a secure, transparent, and intuitive digital banking ecosystem that empowers users to take control of their financial health effortlessly. Over the next five to ten years, we aim to become the trusted standard in ethical, user-first banking, delivering meaningful value through simple, accessible experiences that make everyday financial management seamless, confident, and positive.
- **Product Mission**: Our mission is to create and continuously refine a focused, outcome-based web application that streamlines banking operations for both customers and administrators. By prioritizing user needs, ensuring responsible data handling, offering big-picture capabilities—from secure login and intuitive account management to transparent money transfers and efficient user administration—we commit to delivering measurable improvements in user satisfaction, operational efficiency, and business growth. Through regular validation, adaptive planning, and shared understanding among all stakeholders, we strive to maintain a living vision that stays connected to user outcomes, validates assumptions, and drives sustainable success.

---

## Product Vision Board

The Product Vision Board provides a clear and concise visualization of the product's goals, market, and customers.

![Product Vision Board](images/product_vision_board.png)

- **Vision**:
  IE Bank by Devious Devops **envisions secure, intuitive online banking** where customers confidently manage their finances, **securely and comfortably. Over the next decade,** we aim to set the standard for **transparent, ethical, and user-first** banking by **reducing complexity, empowering users, and delivering lasting value.** Our shared ambition inspires and unites our team to create **positive change,** **handle data responsibly,** and ensure **no harm to people or the planet,** guiding us toward a future of **sustainable innovation.**
  ✅ Inspiring ✅ Shared ✅ Ethical ✅ Concise ✅ Ambitious ✅ Enduring


- **Target Group**:
  Our core target group consists of **tech-savvy adults aged 25-45** who regularly use online financial services. They prefer **digital self-service** experiences, value **robust security,** and seek **simplicity** in their day-to-day banking. This group's members share **common behavioral traits:** frequent online transactions, and a strong desire to reduce time spent managing finances.
  ✅ Clear ✅ Specific ✅ Cohesive

- **Needs**:
  These customers primarily want a banking experience that **saves time and reduces frustration.** They need a **secure way to log in, quickly review account balances, understand transaction histories, and complete transfers with minimal effort.** Their definition of success is measured by the **ease and reliability** of these tasks. We specify and focus on the main benefit: **making account management and transfers quick, worry-free, and transparent.**
  ✅ Outcome-based ✅ Specific ✅ Focused ✅ Prioritized

- **Product**:
  IE Bank's product is a straightforward, **browser-based web application** that serves as a digital gateway to account management. It **differentiates itself** through a **user experience** that places **clarity and security above all else.** By offering a clean set of capabilities—**user registration with automatic account creation, a secure login process, an intuitive account dashboard, reliable money transfers, and an admin portal for managing users**—the product avoids overwhelming complexity. These big-picture features stand as core pillars that set us apart from alternatives, ensuring our product remains focused on **delivering value**, not feature bloat.
  ✅ Type ✅ Differentiated ✅ Focused ✅ Big

- **Business Goals**:
  We aim to reduce manual customer support by **20%** in the first year, boosting overall customer satisfaction to consistently **above 4/5,** and cutting **operational overhead** through the admin portal, compared to our first iteration. Our goals remain **measurable, specific, prioritized, and connected to tangible business impact.**

- **Competitors**:
  Our main competitors are established digital banking platforms known for their **broad feature sets** and **brand recognition.** While they excel at offering extensive product lines and trusted security measures, **they often struggle with overly complex user interfaces and slower adaptation to emerging user needs.** We differentiate ourselves by maintaining a **narrow focus** on **simplicity,** ensuring our product stands out through **streamlined experiences, faster iteration,** and a **user-first** design philosophy.
  ✅ Outcome-based ✅ Specific ✅ Prioritized 

- **Revenue Streams**:
  We plan to **monetize** by providing premium banking services, such as **low-cost international transfers, higher interest savings accounts,** and **tiered subscription models** for advanced capabilities. By aligning our revenue strategy with the **value provided to users,** we ensure that our income generation is tied to improved **customer satisfaction** and the **consistent delivery of meaningful features.**

- **Cost Factors**:
  Key cost factors include **technology infrastructure, cloud hosting, transactional fees, compliance and security certifications, and customer support resources.** We regularly **assess and optimize** these expenses to maintain a **lean operation,** maximizing **cost efficiency** without sacrificing **quality, reliability, or security.**

- **Channels**:
  We will **market and sell** the product primarily through **digital channels,** leveraging **search engine marketing, social media ads, content marketing, and partnerships with reputable financial bloggers and fintech comparison sites.** These existing channels enable us to reach the target audience effectively, while ongoing search engine optimization and user referrals **ensure sustained growth.**


---

## Minimum Viable Product (MVP) and Requirements


**Context & Goals:**  
The Devious Devops group is building the IE Bank, a fintech startup aiming to deliver an intuitive and secure online banking platform. The MVP focuses on essential features that allow customers to manage their accounts, view transactions, register as new users, and perform basic financial operations. Simultaneously, the MVP must also accommodate administrative functions such as user management, ensuring that an internal administrator can effectively control and maintain the system. The overarching goal is to provide a stable, secure, and functional product that can be released to production with confidence, serving as the foundation for future enhancements.

In the inital iteration, a user was able to create bank accounts with different details such as Name, Currency, Country and Balance. The functionality was limited to a single user, and there was no authentication or authorization. 

The initial iteration was also only developed by a single person, so lots of the improvements in the MVP are to make the product maintainable and scalable by multiple developers, introducing a CI/CD pipeline and a proper Agile SCRUM project structure.

### Core Functionalities

**1. Multi-Account Management:**  
From the initial iteration, the system already supports basic CRUD (Create, Read, Update, Delete) operations for user accounts

In this MVP, this functionality remains intact and is extended with introducing authentication, user registration, login, and account operation capabilities. Each user can have one or more bank accounts, each identified by a unique account number.

**2. Administrator Portal – User Management (Admin Portal):**  
The MVP introduces an administrator portal designed for internal bank administrators, to provide a straightforward, secure management interface to maintain user integrity and respond to operational needs.
- **Default Admin Account (FR 1):** A predefined admin user (with a secure default username and password) will be available. This admin account must be able to log in to the admin portal.  
- **Admin User CRUD Operations (FR 2):** Once logged in, the admin can view a list of all registered bank users. The admin can create new users, update existing user information (including resetting passwords), and delete users who no longer need access.  

**3. User Portal – Account Management System (User Portal):**  
The MVP refines the user-facing portal where customers interact with their personal accounts:  
- **User Registration (FR 3):** Prospective bank customers can register through a simple form. Upon successful registration, the user automatically receives a default bank account with a randomly generated account number. This ensures every new user can start banking right away without manual account creation steps.  
- **User Login & Account Viewing (FR 4):** Registered users can securely log in using their chosen username and password. After authentication, they can view only their own accounts, along with associated transaction histories and balances. Unauthorized access to other users’ accounts is strictly prohibited.  
- **Money Transfers (FR 5):** Within their account management portal, users can initiate transfers to other existing accounts in the bank. The amount transferred cannot exceed the current account balance. This fundamental transaction feature empowers users with a basic yet critical financial operation.

### Non-Functional Requirements

**1. Basic Authentication & Security (NFR 1):**  
- **Authentication Simplicity:** Use a basic username/password authentication method.  
- **Secure Credential Storage:** All user credentials (including the admin’s) are hashed and stored securely in the database. No advanced authentication methods like biometrics, tokens, or OAuth were implemented at this stage.  
- **Data Integrity & Privacy:** Communications between the client and server occur over secure channels (e.g., HTTPS) to maintain confidentiality and integrity, even though the MVP may not fully focus on advanced encryption techniques.

**2. Simple Frontend User Interface (NFR 2):**  
- **Minimal Aesthetics:** The front-end is functional and straightforward, focusing on clarity rather than design complexity. While the interface is usable, there is no requirement for advanced styling, cross-browser responsiveness, or dynamic animations.  
- **Ease of Use:** The UI clearly presents essential actions (login, registration, account viewing, transaction history) without confusing flows or extraneous elements.

### DevOps Practices & Methodologies

**Agile & Scrum Processes:**  
- **Product Backlog Management:** The product owner will maintain a prioritized backlog of features and improvements, ensuring that the team’s focus aligns with delivering maximum value to end-users.  
- **Sprint Planning & Regular Meetings:** Each development iteration (sprint) will have a planning session to select backlog items for implementation. Short, regular scrum meetings (at least once per week) will monitor progress and address roadblocks.  
- **Sprint Review & Retrospective:** At the end of each sprint, the team will review completed work with stakeholders (sprint review) and reflect on processes and improvements (sprint retrospective).

**Test-Driven Development (TDD):**  
- **Acceptance Criteria & Testing:** All user stories will have clear acceptance criteria. Tests (unit, integration, and possibly end-to-end) will be written prior to code development. Code will only be considered complete once it passes these tests.  
- **Quality Assurance:** High-level test coverage ensures that functionalities introduced during the MVP phase are reliable and meet the defined requirements.

**Feature Branching CI/CD Strategy:**  
- **Branching Model:**  
  - **Protected main branch:** Main is always stable and only updated after successful testing, and deployment checks.  
  - **Short-living Feature Branches and Trunk-based Development:** Each new feature or bug fix is developed on a dedicated feature branch. Once the feature is complete and tested, it is integrated back into main via a pull request.
- **Automated Deployments:**  
  - **Dev Environment:** Any push to a feature branch triggers a build, test, and deployment sequence to the Development environment. This environment is for internal testing and experimentation.  
  - **UAT Environment:** Pull requests targeting the main branch automatically deploy a preview to the UAT environment. The team and stakeholders review and test the changes in this environment. After successful validation and stakeholder sign-off, the merge is completed.  
  - **Prod Environment:** Merging into the main branch triggers a production deployment. This final step puts the MVP in front of real end-users.

### DTAP Environment Setup

This part is better documented in the [Cloud Architect Documentation](cloud_architect.md), but for clarity, the following environments are used:

**Development Environment:**  
- **Azure Resource Group:** The Development environment will reside in a resource group (e.g., BCSAI2024-DEVOPS-STUDENTS-A-DEV or BCSAI2024-DEVOPS-STUDENTS-B-DEV) where the team has contributor permissions. This allows the team to experiment, troubleshoot, and test configurations directly within Azure services.

**User Acceptance Testing (UAT) Environment:**  
- **Azure Resource Group:** The UAT environment lives in a resource group (e.g., BCSAI2024-DEVOPS-STUDENTS-A-UAT or BCSAI2024-DEVOPS-STUDENTS-B-UAT) where the team only has reader permissions, meaning changes here are solely managed through CI/CD workflows. This environment gives stakeholders a realistic preview of the application without manual interventions.

**Production Environment:**  
- **Azure Resource Group:** The production environment (e.g., BCSAI2024-DEVOPS-STUDENTS-A-PROD or BCSAI2024-DEVOPS-STUDENTS-B-PROD) is also managed exclusively via GitHub Actions. Following a successful UAT review, the final MVP version is pushed into production for end-users.

**Service Principal for Deployment:**  
- **Azure Integration:** A designated Service Principal (e.g., BCSAI2024-DEVOPS-STUDENTS-A-SP or BCSAI2024-DEVOPS-STUDENTS-B-SP) with owner permissions manages deployments. Credentials for this principal are securely stored and used by CI/CD workflows to authenticate and interact with Azure resources. This ensures automated, secure, and traceable deployments.

### Outcomes & Future Considerations

With this MVP, IE Bank will have a foundational product that:  
- Enables internal administrators to control user access and maintain a clean user directory.  
- Provides basic but essential banking functionalities—registration, login, viewing accounts, and performing transfers—to customers.  
- Adopts a structured DevOps and TDD workflow, ensuring quality, stability, and easier scaling as the product matures.

The MVP lays the groundwork for potential future enhancements, such as:  
- Improved UI/UX, making the portal more user-friendly across devices.  
- Additional security layers (multi-factor authentication, OAuth integration).  
- Expanded banking features like bill payment scheduling, credit management, or financial analytics.  
- Performance optimizations and comprehensive monitoring of system health.

In summary, the MVP is the product’s first tangible, deployable state, delivering critical value to end-users and administrators alike. It embodies best practices in software engineering, ensures a secure foundation, and paves the way for more sophisticated and customer-centric features in subsequent iterations.



---

## Objectives and Key Results (OKRs)

Below is a set of five high-level objectives aligned with a product’s growth and quality improvement, each supported by five measurable key results. These OKRs are designed for a product team working on a banking MVP. They focus on improving user experience, system reliability, delivery speed, administrative efficiency, and user engagement within the next quarter. These objectives and key results describe both the work that is done in the MVP and the work that will be done in the post-MVP iterations.

---

### Objective 1: Improve the Customer Onboarding Experience  
**Key Results:**  
1. Increase the percentage of successful user registrations (without errors) from 85% to 95%.  
2. Reduce the average time to complete the registration process from 3 minutes to under 2 minutes.  
3. Achieve at least a 4.0/5.0 average satisfaction score from new users (as measured by a post-onboarding survey).  
4. Decrease new user onboarding-related bad server responses by 30%.  
5. Increase security measures on onboarding to decrease the number of fraudulent registrations by 50%.

---

The objectives here can be better suplemented in the [Site Reliability Engineering Documentation](site_reliability_engineers.md).

### Objective 2: Enhance System Reliability and Performance  
**Key Results:**  
1. Increase the percentage of successful login requests from 90% to 99%.
2. Decrease the average time for a money transfer to complete from 3 seconds to under 2 seconds.
3. Increase the number of concurrent users the application can handle from 100 to 1,000 with an average response time under 2 seconds.
4. Decrease the number of critical error logs in production by 50%.
5. Decrease the average page load time on the user portal from 2.5s to under 1.5s.

---

### Objective 3: Accelerate Feature Delivery and Deployment Pipeline  
**Key Results:**  
1. Increase release frequency to the Production environment from once per month to once per week.  
2. Reduce the average build time in CI from 10 minutes to under 5 minutes.  
3. Achieve at least 90% automated test coverage of critical features.  
4. Decrease the lead time from code commit to production deployment from 24 hours to under 2 hours.  
5. Reduce the rollback rate of production deployments due to defects from 10% to under 3%.

---

### Objective 4: Improve Admin Portal Efficiency & Effectiveness  
**Key Results:**  
1. Decrease the average time for an admin to create/update a user profile from 5 minutes to under 2 minutes.  
2. Achieve a 4.5/5.0 internal satisfaction rating from admins using the portal (measured via internal feedback survey).  
3. Reduce admin escalations to the development team by 50% (indicating admins can resolve most user issues independently).  
4. Achieve a 95% first-contact resolution rate for user account management issues handled by admins.  
5. Provide comprehensive admin portal training, ensuring 100% of admins complete onboarding materials and pass a basic competency quiz.

---

### Objective 5: Increase End-User Engagement & Transaction Volume  
**Key Results:**  
1. Increase the number of monthly active users (MAU) by 20% compared to the previous quarter.  
2. Increase the average number of successful transactions per active user per month by 15%.  
3. Decrease monthly user churn (account closures) from 5% to under 3%.  
4. Achieve a 70% adoption rate for the internal money transfer feature among active users.  
5. Attain a Net Promoter Score (NPS) of at least 40, indicating improved user satisfaction and likelihood to recommend the service.

---

**OKR Usage:**  
- **Regular Review:**  Our team will assess progress against these key results every two weeks. Adjust strategies if metrics are not trending in the right direction.  
- **Cross-Functional Collaboration:** Our product owner, cloud architect, full stack developers, infrastructure engineers, site reliability engineers, and security engineer will ensure that everyone’s efforts are aligned with achieving these OKRs.  
- **Incremental Improvement:** If targets seem consistently easy or hard to meet, our team will calibrate accordingly in the next cycle.

---

## Scrum Methodology

Scrum is an agile framework that helps teams deliver high-quality software products incrementally and iteratively. Rather than trying to plan and execute every detail of a product upfront, Scrum focuses on continuous improvement, flexibility, and close collaboration between team members and stakeholders. The goal is to respond to change quickly, deliver value frequently, and ensure that the final product truly meets user needs.

As the product owner and scrum master, I have the following responsibilities:

1. **Product Owner (PO):**  
   - Define the product vision and long-term strategy.  
   - Maintain and prioritize the product backlog (a list of desired product changes, features, and fixes).  
   - Act as the voice of the customer, ensuring that what the team builds aligns with business objectives and user requirements.

2. **Scrum Master:**  
   - Facilitate the Scrum process, ensuring the team follows agile principles.  
   - Remove impediments that block the team’s progress.  
   - Coach the team on continuous improvement and help maintain a healthy, productive work environment.

**Key Artifacts:**

1. **Product Backlog:**  
   - A prioritized list of features, enhancements, bug fixes, and other work needed to improve the product.  
   - Continuously refined by the Product Owner and the team to ensure clarity, detail, and priority are always up-to-date.

2. **Sprint Backlog:**  
   - A subset of the product backlog items selected for completion in the current sprint.  
   - Represents the team’s commitment for what they aim to deliver by the end of the sprint.  
   - Updated daily by the development team to reflect current progress and any changes.

**Key Events:**

1. **Sprint Planning:**  
   - Was held at the start of each sprint (a time-boxed iteration, typically 1–4 weeks).  
   - The Product Owner presented the highest-priority items from the product backlog.  
   - The development team selected which items they could realistically complete within the sprint and created the sprint backlog.

2. **Daily Scrum (Stand-up):**  
   - A short, time-boxed meeting (usually 15 minutes) held every day.  
   - The development team members share what they did since the last Daily Scrum, what they plan to do today, and any impediments they face.  
   - Ensures continuous alignment and quick issue resolution.

3. **Sprint Review:**  
   - Held at the end of the sprint to inspect the Increment and adapt the product backlog if needed.  
   - The team demonstrated the work completed to stakeholders, gathered feedback, and discussed next steps.  
   - Encourages transparency and helps ensure the product evolves in the right direction.

4. **Sprint Retrospective:**  
   - Occurs right after the Sprint Review, before the next Sprint Planning.  
   - The team reflected on how the sprint went, focusing on processes, tools, and collaboration.  
   - Identified opportunities for improvement and committed to at least one actionable change to enhance efficiency and quality in the next sprint.

---

## Collaboration Strategy

**Overview:**  
Our DevOps collaboration strategy is designed to enable fast, frequent releases and continuous improvement. At the core of this approach are agile methodologies, test-driven development (TDD), trunk-based development, and a suite of integrated tools connected through Slack. By making Slack the central hub of communication and information sharing, teams can rapidly respond to feedback, coordinate releases, and maintain high-quality code. This synergy enhances transparency, shortens feedback loops, and fosters a culture of continuous delivery and iteration.

**Key Practices:**

1. **Agile & Scrum Methodology:**  
   We follow Scrum to manage our work in sprints, maintain a prioritized product backlog, and ensure we regularly review and improve our processes. Scrum ceremonies (sprint planning, daily stand-ups, sprint reviews, retrospectives) are conducted via Zoom/Slack and integrated tools, ensuring the team remains aligned and productive.

2. **Test-Driven Development (TDD):**  
   TDD ensures that tests are written before the code is implemented, guaranteeing that each feature or fix is thoroughly validated. Slack channels receive automated notifications about test results from CI pipelines, enabling immediate visibility into code quality. If a build or test fails, the team is alerted in real-time, and developers can address issues promptly.

3. **Trunk-Based Development:**  
   Our code integration strategy is based on trunk-based development. Short-lived feature branches are merged into the main branch (trunk) frequently and with minimal friction. This ensures that the codebase remains stable, integration challenges are minimized, and new features can be released rapidly. With Slack notifications set up, each merge and build result is communicated in relevant channels, giving all team members real-time insights into the development progress.

**Slack as a Central Collaboration Hub:**
- **#alerts:** General system alerts and notifications not specific to any single repository
- **#backend:** Updates, discussions, and GitHub notifications specific to the backend repository
- **#frontend:** Updates, discussions, and GitHub notifications specific to the frontend repository
- **#fullstack:** Combined updates and discussions covering both frontend and backend development
- **#general:** Team-wide announcements and general communication
- **#infra:** Infrastructure repository updates, deployment notifications, and cloud resource discussions
- **#product-and-architecture:** Product planning, architectural decisions, and technical roadmap discussions
- **#reliability-security:** Security alerts, reliability metrics, and related discussions
- **#slo-alerts:** Service Level Objective monitoring and alerts
- **#social:** Team social interactions and non-work discussions

**Integrations:**

1. **Azure DevOps Boards + Slack:**
   - Backlog items updates appear directly in Slack.
   - Sprint planning and daily stand-ups are enriched with live data, keeping the team focused on the highest-value work.
   - Ensures that what’s being tested and built always aligns with the prioritized backlog.
   ![Azure DevOps Boards Slack Integration](images/devopslack.png)

2. **Slack + GitHub (CI/CD notifications):**
   - CI pipelines run tests written as part of TDD before code integration.
   - Slack notifications on build completions, test results, and deployment status to Dev, UAT, and Prod environments.
   - Enables developers to maintain fast feedback cycles and identify integration issues early.
![GitHub Slack Integration](images/githubslack.png)


3. **Slack + Zoom:**
   - Instant video conferencing for pairing sessions, sprint planning, or incident response.
   - Developers can jump on a call to resolve test failures faster or discuss trunk-based branching strategies in real-time.
![Slack Zoom Integration](images/zoomslack.png)

4. **Azure Monitoring + Slack:**
   - SLO alerts (latency, error rates) and resource utilization notifications appear in #operations-monitoring.
   - Quick response to production issues, ensuring continuous reliability and stability of the system.
   - Enables SREs and developers to rapidly address issues before they impact end-users.
![Azure Monitoring Slack Integration](images/azureslack.png)


---

Feel free to explore each section for detailed documentation.


<div class="back-home-link">
  <a href="index.html">Back to home</a>
</div>

<div class="next-section-link">
  <a href="cloud_architect.html">Next</a>
</div>
