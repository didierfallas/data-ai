# Review of DVA Internal Onboarding — Discussion & Clarification Document

## Key Clarifications Needed
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:11` Tenant model: document who provisions new tenants, how Super Admin invitations interact with billing activation, and whether tenant-specific IdPs require custom domains or metadata exchange.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:17` Invitation lifecycle: expiration rules, password setup flows, duplicate-email handling, and recovery for deactivated accounts need explicit UX and support playbooks.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:31` Account removal: define what happens to owned assets, shared surveys, and analytics history; note retention obligations and legal hold exceptions.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:40` RBAC scope: split roles by product (Admin Platform vs User App), outline minimum permissions per screen or API, and cover elevated capabilities such as billing management and API key rotation.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:52` Tenant data collaboration: clarify concurrency rules, locking or versioning strategy for surveys, and name-collision logic for documents.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:65` AI metering: define authoritative usage source, reconciliation with Stripe or billing, alerting thresholds, and treatment of failed or partial generations.

## Additions to Consider
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:25` Add audit log requirements (who can read logs, retention, tamper resistance) and incident response expectations.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:74` Storage: cover encryption at rest and in transit, bucket-per-tenant trade-offs (IAM isolation, lifecycle policies), backup or restore SLAs, and data residency constraints.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:88` API integration: document versioning, schema change policy, quota units, error handling, and sandbox or test credentials.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:96` Plans: list feature flags per tier, limit metrics (users, AI tokens, storage), downgrade grace periods, and proration or refund rules.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:119` Stripe extension: validate PCI implications, webhook processing flow, dunning, tax handling, and contingency if the extension is deprecated.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:124` Analytics: confirm PII governance, consent or cookie banners, ability to honor regional privacy regulations, and operational dashboards (error rates, latency).
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:131` Collaboration: expand on shared backlog tooling, release cadence, QA responsibilities, and escalation paths.
- `DVA_Internal_Onboarding_Discussion_EN_v2.md:139` Overall roadmap: add dependencies (for example legal review, security assessment), definition of done per item, and ownership matrix.

## Recommended Next Steps
1. Facilitate a workshop with product, security, and support to resolve tenant and user lifecycle questions and document invitation plus deactivation flows.
2. Build a draft RBAC matrix and feature-to-plan mapping to validate with stakeholders before implementation.
3. Engage architecture or infrastructure teams to decide storage isolation, AI metering pipeline, and monitoring stack; capture resulting non-functional requirements.
4. Coordinate with finance or legal teams to vet the Stripe extension, pricing tiers, tax obligations, and contract-level commitments.
5. Establish a collaboration playbook: branching strategy, release calendar, tooling ownership, and communication rituals between Siftia and Adaptive.
6. Translate agreed decisions into backlog epics with acceptance criteria so the MVP hardening plan can be scheduled and tracked.
