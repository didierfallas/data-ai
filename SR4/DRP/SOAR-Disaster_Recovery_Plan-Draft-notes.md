# SOAR Disaster Recovery Plan - Draft

## 1. Introduction

### 1.1 Purpose
The purpose of this Disaster Recovery Plan (DRP) is to establish a comprehensive framework for ensuring the continuity and rapid recovery of the RecoveryLink SOAR EHR SaaS platform in the event of a disaster or significant service disruption.

### 1.2 Scope
This plan covers all critical systems, services, and infrastructure components of the SOAR platform hosted on Google Cloud Platform (GCP), including but not limited to:
- Frontend applications (React SPA)
- Backend services (GraphQL API, Cloud Functions)
- Data stores (Firestore, Cloud SQL, BigQuery)
- Infrastructure components (Compute Engine, Cloud Run, Storage)
- Supporting services (Monitoring, Logging, Security)

### 1.3 Document Status
**Version:** 1.0 - Draft
**Date:** September 30, 2025
**Status:** Work in Progress

## 2. Executive Summary

### 2.1 Business Impact
SOAR (RecoveryLink SOAR EHR SaaS platform) is a critical digital application for addiction recovery clinics. Extended downtime could:
- Disrupt patient care and treatment continuity
- Impact regulatory compliance requirements
- Cause financial loss for both RecoveryLink and client clinics
- Damage reputation and client relationships

### 2.2 Recovery Priorities
1. **Critical Services:** Patient data access, appointment scheduling, treatment records
2. **Important Services:** Reporting, analytics, administrative functions
3. **Secondary Services:** Historical data analysis, business intelligence

## 3. Disaster Recovery Team

### 3.1 Primary Contact Team

| Role | Name | Contact Information | Primary Responsibilities |
|------|------|-------------------|-------------------------|
| Pending | Jason Bell | jason@myrecoverylink.com, Slack | Overall DR coordination, business decisions |
| Principal Contact | Paul Fervoy | paul@siftia.tech, Slack, WhatsApp +506 7011-8045 | Senior decision maker, client communication |
| Account Manager | Tom Fervoy | tom@siftia.tech, Slack, WhatsApp +1 (646) 408-0368 | Client relations, commercial aspects |
| Technical Lead | Carlos Pravia | carlos@siftia.tech, Slack, WhatsApp +506 8819-8987 | Technical recovery coordination |
| Infrastructure Lead | Didier Fallas | didier@siftia.tech, Slack, WhatsApp +506 7013-3085 | Infrastructure recovery, GCP services |

### 3.2 Technical Response Team

| Role | Name | Contact Information | Primary Responsibilities |
|------|------|-------------------|-------------------------|
| Data Engineer | Eulices Nicot | eulices@siftia.tech, Slack | Data model recovery, Database recovery, data integrity |
| Lead Front-End Engineer | Carlos Valverde | cvalverde@siftia.tech, Slack | Frontend service recovery |
| Cloud Engineer | Clever Serrano | clever@siftia.tech, Slack | Backend services recovery, Cloud infrastructure, GCP services |
| Project Manager | Yarelis Fallas | yarelis@siftia.tech, Slack | Communication, coordination, documentation |

## 4. SOAR Architecture Overview

### 4.1 Environment Strategy
SOAR operates four managed environments:
- **PROD:** `recoverylink-err-platform` (Production)
- **STAGE:** `recoverylink-err-stage` (Staging)
- **DEV:** `recoverylink-err-dev` (Development)
- **QA:** `recoverylink-qa-platform` (Quality Assurance)

### 4.2 Core Components

#### 4.2.1 Frontend
- **Technology:** React SPA
- **Hosting:** Firebase Hosting

#### 4.2.2 Backend Services
- **GraphQL API:** Cloud Run, Node.js/Express
- **Cloud Functions:** Firebase Functions (1st and 2nd generation)
- **Microservices:** ~20 services on Cloud Run
- **Compute Engine:** RStudio, legacy services, microservices

#### 4.2.3 Data Stores
- **Firestore:** Real-time app data, configurations
- **Cloud SQL:** MySQL 8.0 (core structured data), SQL Server
- **BigQuery:** Historical data, analytics, reporting
- **Cloud Storage:** Document uploads, backups

#### 4.2.4 Supporting Services
- **Monitoring:** Cloud Monitoring, Logging
- **Security:** Firebase Auth, Secret Manager
- **CI/CD:** Cloud Build, GitHub Actions

### 4.3 Regional Distribution
- **Primary Region:** us-central1
- **BigQuery:** US multi-region
- **Data Residency:** United States

## 5. Risk Assessment and Business Impact Analysis

### 5.1 Risk Assessment

#### 5.1.1 Natural Disasters
- **Risk:** Regional outages (weather, seismic)
- **Probability:** Low
- **Impact:** High
- **Mitigation:** Multi-region deployment for critical services

#### 5.1.2 Cybersecurity Incidents
- **Risk:** Ransomware, data breaches, DDoS attacks
- **Probability:** Medium
- **Impact:** Critical
- **Mitigation:** Security monitoring, backup isolation, access controls

#### 5.1.3 Infrastructure Failures
- **Risk:** GCP service outages, hardware failures
- **Probability:** Medium
- **Impact:** High
- **Mitigation:** Redundant deployments, health monitoring

#### 5.1.4 Human Error
- **Risk:** Accidental deletion, misconfiguration
- **Probability:** Medium
- **Impact:** Medium to High
- **Mitigation:** Access controls, change management, backups

#### 5.1.5 Data Corruption
- **Risk:** Database corruption, sync failures
- **Probability:** Low
- **Impact:** Critical
- **Mitigation:** Regular backups, integrity checks, point-in-time recovery

### 5.2 Business Impact Analysis

| Service | RTO | RPO | Business Impact | Priority |
|---------|-----|-----|----------------|----------|
| Patient Data Access | Pending | Pending | Critical - Patient care affected | P0 |
| Authentication System | Pending | Pending | Critical - No system access | P0 |
| Core API Services | Pending | Pending | Critical - Application functions | P0 |
| Cloud SQL Databases | Pending | Pending | Critical - Patient records | P0 |
| Firestore Database | Pending | Pending | Critical - Real-time data | P0 |
| Frontend Application | Pending | Pending | Critical - User interface | P0 |
| BigQuery Analytics | Pending | Pending | Important - Reporting | P1 |
| File Storage (Cloud Storage) | Pending | Pending | Important - Documents | P1 |
| Monitoring/Logging | Pending | Pending | Important - Operations | P1 |

## 6. Disaster Recovery Strategies

### 6.1 Backup Strategy

#### 6.1.1 Cloud SQL (MySQL)
- **Automated Backups:** Daily automated backups with 7-day retention
- **Point-in-Time Recovery:** Enabled for all instances
- **Cross-Region Replicas:** For production critical databases
- **Backup Verification:** Weekly restore testing

#### 6.1.2 Firestore
- **Automated Exports:** Daily exports to Cloud Storage
- **Retention:** 30 days for daily backups, 90 days for weekly
- **Cross-Region Storage:** Backups stored in separate region

#### 6.1.3 BigQuery
- **Automated Backups:** Native 7-day automatic backup
- **Table Snapshots:** Manual snapshots for critical datasets
- **Cross-Region Replication:** For critical tables

#### 6.1.4 Cloud Storage
- **Versioning:** Enabled on all buckets
- **Object Lifecycle:** Automatic archiving to Coldline
- **Cross-Region Replication:** For critical buckets

### 6.2 High Availability Architecture

#### 6.2.1 Multi-Zone Deployment
- **Cloud Run:** Services distributed across multiple zones
- **Cloud SQL:** High availability configuration with automatic failover
- **Load Balancing:** HTTP(S) Load Balancer with health checks

#### 6.2.2 Redundancy
- **MinInstances:** Production services maintain minimum instances
- **Health Checks:** Comprehensive health monitoring
- **Circuit Breakers:** Implemented for external dependencies

### 6.3 Infrastructure as Code
- **Terraform:** Infrastructure codified and version controlled
- **Cloud Build:** Automated deployment pipelines
- **Environment Parity:** Consistent configurations across environments

## 7. Disaster Recovery Procedures

### 7.1 Incident Identification and Notification

#### 7.1.1 Monitoring and Alerting
- **Cloud Monitoring:** 24/7 monitoring of all critical services
- **Alert Thresholds:** Configured for rapid detection
- **Notification Channels:** Slack, email, SMS for critical alerts

#### 7.1.2 Incident Classification
- **P0 - Critical:** System-wide outage, complete service unavailability
- **P1 - High:** Major functionality impacted, significant user impact
- **P2 - Medium:** Partial functionality impacted, limited user impact
- **P3 - Low:** Minimal impact, workarounds available

#### 7.1.3 Notification Procedure
1. **Automatic Alert:** Monitoring system detects anomaly
2. **On-call Engineer:** Initial assessment (15 minutes)
3. **DR Coordinator:** Notification and classification (30 minutes)
4. **Full Team Activation:** Based on severity level

### 7.2 Disaster Declaration

#### 7.2.1 Declaration Criteria
- Service outage exceeding 30 minutes for critical functions
- Data corruption or loss confirmed
- Security breach affecting data integrity
- Regional infrastructure failure
- Multiple component failures indicating systemic issue

#### 7.2.2 Authority Levels
- **P0 Incidents:** DR Coordinator or Technical Lead can declare
- **P1 Incidents:** Technical Lead with DR Coordinator approval
- **Full Disaster:** Principal Contact approval required

### 7.3 Recovery Procedures

#### 7.3.1 Phase 1: Assessment and Isolation (0-1 hour)
1. **Incident Assessment:** Determine scope and impact
2. **Communication:** Initial notification to stakeholders
3. **Isolation:** Prevent further damage or data loss
4. **Documentation:** Begin incident logging

#### 7.3.2 Phase 2: Recovery Execution (1-4 hours)

##### 7.3.2.1 Database Recovery
**Cloud SQL Recovery:**
1. Evaluate automated backup availability
2. Initiate point-in-time recovery to last known good state
3. Verify data integrity and consistency
4. Update application connection strings if needed
5. Conduct smoke testing

**Firestore Recovery:**
1. Identify last successful export
2. Restore from Cloud Storage backup
3. Verify data consistency
4. Update indexes if required

##### 7.3.2.2 Application Services Recovery
**Cloud Run Services:**
1. Redeploy services from last known good container image
2. Verify health checks passing
3. Update load balancer configuration
4. Conduct integration testing

**Cloud Functions:**
1. Redeploy functions from source control
2. Verify triggers and configurations
3. Test critical function paths

##### 7.3.2.3 Frontend Recovery
**Firebase Hosting:**
1. Redeploy from last successful build
2. Verify CDN distribution
3. Test critical user flows
4. Clear browser caches if needed

#### 7.3.3 Phase 3: Verification and Validation (4-6 hours)
1. **End-to-End Testing:** Verify complete user journeys
2. **Performance Testing:** Confirm system performance
3. **Data Validation:** Verify data integrity across systems
4. **Security Review:** Ensure no security compromises
5. **Documentation:** Complete recovery procedure documentation

### 7.4 Communication Plan

#### 7.4.1 Internal Communication
- **Slack Channel:** PENDING CHANNEL
- **Frequency:** Every 30 minutes during active recovery
- **Content:** Status updates, ETA, blockers

#### 7.4.2 External Communication
- **Initial Notification:** Within 1 hour of incident detection
- **Regular Updates:** Every 2 hours or as status changes
- **Channels:** Email, client portal, direct contact for key clients
- **Templates:** Pre-approved communication templates

#### 7.4.3 Stakeholder Communication
- **Executive Team:** Real-time updates via dedicated channel
- **Technical Team:** Detailed technical information
- **Clients:** Business impact and resolution status
- **Regulatory Bodies:** As required by compliance obligations

## 8. Backup and Recovery Testing

### 8.1 Testing Schedule
- **Monthly:** Automated backup verification
- **Quarterly:** Partial recovery testing (sandbox environment)
- **Semi-Annual:** Full disaster recovery drill
- **Annual:** Complete DRP review and update

### 8.2 Testing Procedures
1. **Backup Validation:** Verify backup completeness and integrity
2. **Recovery Simulation:** Test recovery procedures in isolated environment
3. **Documentation Review:** Update procedures based on test results
4. **Team Training:** Conduct training based on test scenarios

### 8.3 Success Criteria
- **RTO Compliance:** Recovery within target timeframes
- **RPO Compliance:** Minimal data loss within objectives
- **Functionality:** All critical features operational
- **Performance:** System performance meets baseline metrics

## 9. Plan Maintenance and Training

### 9.1 Document Maintenance
- **Quarterly Reviews:** Update contact information and procedures
- **Annual Updates:** Complete plan review and revision
- **Change-Triggered Updates:** Update after significant infrastructure changes
- **Version Control:** Maintain document history and change logs

### 9.2 Team Training
- **Initial Training:** All team members complete DRP training
- **Annual Refresher:** Mandatory yearly training sessions
- **Scenario-Based Training:** Tabletop exercises and simulations
- **New Hire Onboarding:** Include DRP training in onboarding process

### 9.3 Continuous Improvement
- **Post-Incident Reviews:** Analyze all incidents for improvement opportunities
- **Metric Tracking:** Monitor recovery time and success rates
- **Technology Updates:** Evaluate new disaster recovery technologies
- **Best Practices:** Incorporate industry best practices

## 10. Appendices

### Appendix A: Service Dependencies

| Service | Dependencies | Criticality |
|---------|-------------|-------------|
| Frontend App | GraphQL API, Firebase Auth | Critical |
| GraphQL API | Cloud SQL, BigQuery, Firestore | Critical |
| Cloud Functions | Firestore, Cloud SQL, External APIs | Critical |
| Data Pipelines | BigQuery, Cloud Storage | Important |
| Monitoring | All GCP Services | Important |

### Appendix B: Critical Vendor Contacts

| Service | Vendor | Contact Information | SLA |
|---------|--------|-------------------|-----|
| Google Cloud Platform | Google | 24/7 Support | 99.95% |
| [Add others as needed] | | | |

### Appendix C: Communication Templates

#### C.1 Initial Incident Notification
**Subject:** SOAR Service Incident - [SEVERITY]

**Message:**
We are investigating a [severity] incident affecting the SOAR platform. Our team has been mobilized and is working to resolve the issue. We will provide updates every [frequency] until the issue is resolved.

Impact: [describe impact]
Next update: [time]

### Appendix D: Recovery Checklists

#### D.1 Pre-Recovery Checklist
- [ ] Incident scope and impact assessed
- [ ] DR team notified and assembled
- [ ] Communication channels established
- [ ] Backup integrity verified
- [ ] Recovery environment prepared

#### D.2 Post-Recovery Checklist
- [ ] All services operational
- [ ] Data integrity verified
- [ ] Performance metrics normal
- [ ] Security review completed
- [ ] Documentation updated
- [ ] Post-incident review scheduled

### Appendix E: Glossary

- **RTO:** Recovery Time Objective - Target time for service restoration
- **RPO:** Recovery Point Objective - Maximum acceptable data loss
- **HA:** High Availability - System design for minimal downtime
- **DR:** Disaster Recovery - Processes for service restoration
- **SLA:** Service Level Agreement - Performance guarantees
- **P0/P1/P2/P3:** Priority levels for incident classification

### Appendix F: Document Change Log

| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0 | 2025-09-30 | Initial draft version | Claude Code |

---

**Document Control:**
This document is confidential and proprietary to RecoveryLink. Distribution is restricted to authorized personnel only.

**Next Review Date:** December 30, 2025
