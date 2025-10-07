# DVA Internal Onboarding — Discussion & Clarification Document

**Purpose**

This document consolidates open questions, assumptions, and technical considerations gathered during the initial DVA onboarding and multi-tenant design discussion. Its goal is to guide internal alignment across Siftia and Adaptive teams regarding architecture, roles, environments, and delivery expectations for the MVP hardening phase.

## **1\. User Management**

**Proposed approach**

* Use Firebase Auth and Google Cloud Identity Platform to enable a multi-tenant setup with at least two tenants: **Admin Platform** and **User App** (final names still to be defined).  
* Each *physical* tenant should have its own identity providers (email/password, 2FA, SAML, etc.) and separate user bases.  
* Accounts between Identity Platform tenants are not shared or mixed.

**Open questions**

* Is a tenant admin account created only after the Super Admin sends an invitation, following the tenant’s creation on the platform?  
* What is the distinction between Adaptive users and other user types? Are Adaptive users required from the very beginning?  
* What are the policies for user creation and invitation? Should invitations have an expiration period? When does the user set their password—upon invitation or first login?  
* Each user should be linked to the tenant of the admin who invited them. A single email can only exist in one tenant — what happens if another admin tries to invite the same email?  
* Can one admin create another admin within the same tenant? How deep should RBAC go for tenant users during MVP?

**Account deactivation and deletion**

* Deactivation will be logical (flag \+ metadata).   
* Physical deletion may occur after N days or manually by Super Admin.   
* Deletion always requires prior deactivation.

**Clarifications needed:** 

* Should users receive deactivation notifications?   
* When a user is removed, do their assets remain?

## **2\. RBAC and Roles**

* Permissions are **role-based**, not **user-based**.

**Initial role proposal:** 

* Tenant Admin (manage users, complete surveys, upload assets, view reports, enable API exports);   
* Regular User (view reports only).

**Next steps:** 

* Identify all reports, screens, and actions that require RBAC validation (e.g., viewing reports, submitting surveys, uploading documents).  
* We assume there are screens with mixed permissions; e.g., all roles can view the report, but only some roles can take certain actions.

## **3\. Data Handling (Surveys, Documents, Assets)**

**Open questions:** 

* Are surveys and uploaded documents shared across all users within a tenant? How is overwriting managed if multiple users edit the same survey or upload the same document (filename named the same)?  
* Can surveys or documents have multiple versions over time?

**Assumptions**: 

* Each submission is traced with user, tenant, plan, timestamp, and role for auditability.

## **4\. AI Usage and Token Consumption**

* The AI usage is the single major cost of the application, and will vary depending on user consumption. 

**Open questions:** 

* How will AI token consumption be tracked per tenant and per user?   
* Should there be quotas by plan or role?

**Assumptions:** 

* Prompt metadata, model version, latency, client\_id, and timestamp logged for all AI operations.

## **5\. Data Upload & Storage Architecture**

* The application will have a private bucket to store templates and assets for internal use.

**Open questions:** 

* When do we need SFTP/API uploads vs. web uploads (file size, data volume, format)?

**Storage options:** 

* Single bucket with tenant subfolders vs. dedicated bucket per tenant.

## **6\. API Integration**

**Open questions:** 

* Is API access tied to specific tenant plans?   
* Should we use JWT/OAuth2 or simpler API keys per tenant?  
* How will rate limiting and API consumption tracking be handled?

## **7\. Plans and Subscription Logic**

**Open questions:** 

* What are the plan definitions and limits for MVP?  
* Should Freemium users see disabled features of higher plans?  
* What happens when downgrading from Premium to Freemium (data retention, user access, API access)?

## **8\. CI/CD and Environments**

**Open questions:** 

* How is the current Git repos structure? One per FE and one per BE?


**Proposed structure:** 

* One GCP project per environment (DEV, STAGE, PROD).  
* Existing repos become the new DEV baseline.

**Repositories:** 

* DVA User-App FE (current),   
* DVA User-App BE (current),   
* DVA Admin-Platform FE (new),   
* DVA Admin-Platform BE (new).

## **9\. Stripe / Payment Integration**

* A Firebase extension may support payments and subscriptions with Strip payment service.   
* Need to verify its freshness and provider status before adoption.

## **10\. Analytics and Logging**

* Use Google Tag Manager and GA4 for application usage tracking and visualization logging. It can track whatever action and options selected by the user, session time, flow completions, scroll percentage, etc.  
* GA4 integrates with BigQuery and Looker Studio for the Product Owner dashboard and tenant admin dashboard if needed.

## **11\. Development Collaboration — Siftia & Adaptive**

**Concern:** 

* During DVA App update (multi-tenant and session capabilities), how to coordinate dev work between Siftia and Adaptive to avoid Git conflicts.

**Action:** 

* Define branching/merging strategy, environment access, deployment rights, and test workflows.

## **12\. Next Steps and Alignment Items**

1. Final Auth and tenant isolation model decision.  
2. Role structure and RBAC depth for MVP.  
3. Storage model and AI token monitoring approach.  
4. Stripe extension validation and payment flow.  
5. Plan tiers and downgrade behavior.  
6. API key vs. OAuth2 decision and rate-limiting policy.  
7. Git collaboration protocol between teams.