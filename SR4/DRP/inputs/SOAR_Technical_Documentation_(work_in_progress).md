# **1\. Deployment & Environments**

## **1.1 Environment Strategy**

SOAR operates four managed environments aligned to Git branching and gated releases:

* **PROD** – `recoverylink-err-platform`

* **STAGE** – `recoverylink-err-stage`

* **DEV** – `recoverylink-err-dev`

* **QA** – `recoverylink-qa-platform`

Promotion path: updates flow through **DEV → STAGE (and occasionally QA) → PROD**, with acceptance tests and PM approval. There are **no ephemeral/preview channels**; validation occurs on shared pre-production tiers.

**Promotion gates**: Deployments to PROD are tied to Jira tickets. Tickets are reviewed and tested by the PM before approval for release.

## **1.2 Repositories & Deployment Model**

* **Frontend (React SPA)** – `soar.dev.client`  
   Deployed to **Firebase Hosting** within the environment’s GCP project (e.g., DEV → `recoverylink-err-dev`).

* **Backends**

  * `soar.stage.functions` – **Firebase Cloud Functions** (mix of 1st and 2nd gen). Branch-based deployments target the correct GCP project via **Cloud Build YAMLs**.

  * `soar.prod.server` – **GraphQL API**, deployed via Cloud Build to multiple environments, using branches \+ project mapping.

* **Data Definitions** – `soar.prod.bigquerysource`  
   Managed with **Dataform** (BigQuery). Branches and **GitHub Actions** handle deployment to the correct GCP environment.

**Note:** DEV and QA share repos with PROD/STAGE but rely on branch-to-project mappings in pipelines.

## **1.3 Regions**

* **Cloud Functions & Cloud Run**: `us-central1`

* **BigQuery**: US multi-region datasets (all environments)

  ## **1.4 Runtime & Platform Mix**

* **BigQuery** – analytics, logging, reporting

* **Cloud SQL (MySQL)** – structured core domain entities (enterprises, organizations, roles, memberships, programs, locations, participants, staff)

* **Cloud Storage** – uploaded documents (participants/staff)

* **Firebase Cloud Functions (gen1 \+ gen2)** – API & event-driven logic (deployed via Firebase CLI/Cloud Build)

* **Cloud Run** – \~20 microservices; PROD keeps **minInstances=1** to reduce cold starts, non-prod uses **0** to save cost

* **Compute Engine VMs**:

  * *RStudio–ISR* (always-on, for ISR calculations)

  * *Firestore sync* (on-demand, for large data sync jobs)

  * *Microservices instances* (always-on, legacy workloads)

* **Firebase Hosting** – per-environment frontend delivery

  ## **1.5 Network Exposure & Security**

* **Public endpoints**: All services are exposed as public HTTP endpoints.

* **Edge enforcement**: Firebase Auth \+ Hosting rewrites enforce authentication at the edge before routing traffic to backends.

* **No IP allowlists or WAF**: Currently, ingress is unrestricted beyond auth checks.

# **2\) Core Services / Components**

## 2.1 Service Catalog

* **Frontend Client** – React SPA (Firebase Hosting), GraphQL \+ REST clients  
    
* **GraphQL API Server** – Cloud Run, Node.js/Express \+ GraphQL  
    
* **Cloud Functions** – Firebase Functions (REST APIs, triggers, MFA, sessions)  
    
* **Data Definitions** – Dataform \+ BigQuery SQL pipelines  
    
* **Compute Engine Services** – RStudio/Shiny (ISR), Firestore sync VM, legacy microservices

## 2.2 Languages & Frameworks

* **Frontend**: React, Redux Toolkit, Apollo, PrimeReact, Formik/Yup, Twilio SDKs, Mapbox, Chart.js

* **GraphQL API (Cloud Run)**: Node.js, Express, GraphQL, MySQL, BigQuery, JWT, Axios, Lodash, node-cron

* **Cloud Functions**: Node.js, Firebase Functions, Firestore, MySQL, BigQuery, JWT, QR code generation

* **Data Definitions**: SQL (BigQuery dialect), Dataform framework

* **Compute Engine**: R (Shiny), Node.js/Python scripts

## 2.3 Interfaces & Communication

* **Frontend** → GraphQL API (Apollo, GraphQL/HTTP)

* **Frontend** → Cloud Functions (REST endpoints)

* **API** → MySQL/BigQuery

* **Functions** → Firestore triggers

* **Data pipelines** → Dataform → BigQuery

* **Real-time comms**: SignalR (WebSockets), Twilio (voice/video)

## 2.4 Batch & Scheduled Jobs

* **refresh\_lt\_all**: every 15 min (work hours), hourly off-hours → Firestore → BigQuery sync

* **Bulk Delete**: 5am on 1st & 15th of each month

* **Dataform workflows**: commit-based & scheduled BigQuery transformations

**3\) Data Stores & State**

## 3.1 Primary Databases

* **Firestore** – Real-time app data, configs, org/enterprise setups, indexed via composite indexes

* **Cloud SQL** – MySQL 8.0 (core structured entities), SQL Server 2017–2022 Web (specialized microservices)

* **BigQuery** – Historical repository \+ reporting (via Hevo \+ Dataform)

* **Redis/Memorystore** – Not used

## 3.2 Data Residency

* US multi-region (BigQuery), us-central1 (Firestore, SQL). No residency constraints defined.

## 3.3 Multi-Tenancy

* Managed via MySQL membership IDs. No tenant isolation in Firebase Authentication.

## 3.4 Files & Media

* Cloud Storage per environment for user uploads, staff notes, and database/Firestore backups.

## 3.5 Analytics & Pipelines

* **refresh\_lt\_all** – Firestore → BigQuery sync

* Materialized reporting datasets in BigQuery (for BI/reporting users)

## 3.6 Search & Indexing

* Firestore composite indexes. No external full-text search used.

# **4\) Integration & Messaging**

18. **Eventing**: Pub/Sub topics/subscriptions (names/purposes). Any dead-letter topics?

19. **Task orchestration**: Cloud Tasks queues (names/uses, retry/TTL)?

20. **Third-party integrations**: Mail providers, payment, identity providers, Slack/Teams, webhooks (inbound/outbound)?

21. **Webhooks**: Which external systems call SOAR? Which webhooks does SOAR send out?

# **5\) Networking, Security & Secrets**

22. **Networking**: Any VPC, Serverless VPC Access, private IP for Cloud SQL, egress controls?

23. **AuthN/AuthZ**: Firebase Auth providers? Custom tokens? Role model (RBAC/ABAC), how enforced (middleware, Firestore rules, backend checks)?

24. **IAM**: Key service accounts and least-privilege notes (who can read/write which resources)?

25. **Secrets & config**: Secret Manager keys (names/purposes), runtime config strategy (env vars, build-time, parameter store)?

26. **Data protection**: CMEK? At-rest/in-transit encryption specifics; PII handling; audit logging?

# **6\) Reliability, Scaling & Cost**

27. **SLO/SLA targets**: Availability/latency goals for critical endpoints?

28. **Autoscaling**: Cloud Run min/max instances, concurrency, CPU allocation? Functions memory/timeouts?

29. **Backups & DR**: Backup cadence (SQL/Firestore exports), restore procedures, RPO/RTO?

30. **Quotas & limits**: Any known hotspots (Firestore writes/sec, Pub/Sub throughput, Cloud Run cold starts)?

31. **Cost controls**: Budgets/alerts, cost-sensitive design choices (batching, caching)?

# **7\) CI/CD & Quality**

32. **Repos & branching**: Monorepo or multi-repo? Branch strategy (main/develop/feature/\*)?

33. **CI/CD**: GitHub Actions/Cloud Build pipelines (build, test, deploy steps) per service/env?

34. **Testing**: Unit/e2e/load tests? Staging smoke tests? Canary or blue/green?

35. **Infrastructure as Code**: Terraform/Google Config Controller? What resources are codified?

# **8\) Observability**

36. **Logging**: Cloud Logging log-based metrics? Structured logging conventions?

37. **Metrics & tracing**: Cloud Monitoring dashboards, uptime checks, Error Reporting, OpenTelemetry?

38. **Alerts**: What alerts exist (channels, thresholds) for incidents?

# **9\) Edge & Clients**

39. **Front-end delivery**: Firebase Hosting sites/channels? CDN, custom domains, redirects, headers (HSTS/CSP)?

40. **Clients**: Web (React?), mobile (iOS/Android/Flutter?), service worker/Push?

41. **Config delivery**: Remote Config/feature flags? App Check?

# **10\) High-Level Data Flows (for diagrams)**

42. **Auth flow**: From client sign-in → token issuance → backend enforcement.

43. **Core business flow A**: Choose your most important end-to-end flow (e.g., “org admin creates workspace → members invited → events streamed to BigQuery”). Outline steps/services.

44. **Core business flow B**: Second high-value flow (e.g., “user action → event → Pub/Sub → processor → Firestore write → webhook to third-party”).

45. **Error paths & retries**: Where do retries/compensation happen (Cloud Tasks/Pub-Sub DLQ/Idempotency keys)?

