# DVA Internal Onboarding Discussion - Key Aspects

Based on the DVA Internal Onboarding document, here are the key aspects you should check, add, and evaluate:

## Critical Technical Decisions to Resolve

1. **Auth & Tenant Isolation Model:**
   - Confirm: Single Firebase project with multiple tenants vs. separate projects
   - Decide: How user accounts are isolated between Admin Platform vs User App tenants
   - Validate: Google Cloud Identity Platform can support your exact multi-tenant requirements

2. **Storage Architecture:**
   - Choose: Single bucket with tenant prefixes vs. dedicated buckets per tenant
   - Evaluate: Cost implications and access control complexity for each approach
   - Define: Data retention and deletion policies (especially for deactivated users)

3. **API Authentication:**
   - Decide: JWT/OAuth2 vs. API keys per tenant
   - Design: Token consumption tracking and quota enforcement per tenant/user
   - Plan: Rate limiting strategy at tenant/user level

## Business Logic Gaps to Address

1. **User Lifecycle Management:**
   - Define: Invitation workflow and expiration policies
   - Specify: Password creation flow (invitation vs first login)
   - Handle: Duplicate email scenarios across tenants
   - Design: User promotion/demotion between roles

2. **Plan & Subscription Model:**
   - Define: MVP plan tiers with specific limits
   - Specify: Downgrade behavior (data retention, feature access)
   - Plan: Freemium vs paid feature visibility
   - Validate: Stripe integration approach (extension vs custom)

3. **Data Ownership & Sharing:**
   - Define: Survey/document ownership within tenants
   - Specify: Versioning requirements for documents/surveys
   - Handle: Concurrent editing and overwrite policies
   - Plan: Asset migration if users change tenants

## Architecture & Scalability Considerations

1. **AI Usage Tracking:**
   - Design: Real-time token consumption monitoring
   - Plan: Quota enforcement and alerting
   - Specify: Data logging for cost allocation per tenant

2. **Multi-tenant Data Isolation:**
   - Verify: Database schema supports tenant isolation
   - Plan: Cross-tenant data leakage prevention
   - Design: Tenant-specific configuration management

3. **Performance & Monitoring:**
   - Plan: Tenant-specific rate limiting
   - Design: Multi-tenant analytics and reporting
   - Specify: SLA requirements per plan tier

## Operational & Security Items

1. **CI/CD Pipeline:**
   - Define: Multi-repo branching strategy
   - Plan: Deployment coordination between teams
   - Specify: Automated testing for multi-tenant features

2. **RBAC Implementation:**
   - Map: Specific permissions to each role
   - Design: Permission inheritance and delegation
   - Plan: Audit logging for sensitive operations

3. **Compliance & Security:**
   - Validate: Data encryption at rest/in transit
   - Plan: Multi-tenant security boundary testing
   - Specify: Data export and deletion compliance

## Immediate Actions

1. Schedule technical validation sessions for Firebase Identity Platform capabilities
2. Create detailed data models for multi-tenant architecture
3. Define MVP scope vs. phase 2 features
4. Establish decision timeline for technical architecture choices
5. Plan proof-of-concept implementations for critical architecture decisions

The document covers high-level concerns well, but you need detailed technical specifications for the multi-tenant implementation, especially around data isolation, AI cost management, and user lifecycle flows.