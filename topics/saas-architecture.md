# SaaS Architecture

A production SaaS application needs more than authentication and a database. The architecture should account for tenants, permissions, data isolation, billing, reliability, and operational visibility.

## Typical Architecture

```text
User
 ↓
Frontend
 ↓
API / Server
 ↓
Authentication
 ↓
Authorization
 ↓
Business Logic
 ↓
Database
 ↓
External Services
```

## Multi-Tenant Design

A common approach is to associate application data with a tenant or organization.

```text
Organization
    ↓
Users
    ↓
Projects
    ↓
Resources
```

Every protected query should enforce the correct tenant boundary.

## Core Components

* Authentication
* Role-based authorization
* Tenant isolation
* Database constraints
* Billing
* Email notifications
* Audit logging
* Background jobs
* Error monitoring
* Backups

## Authorization

Authentication answers:

> Who is this user?

Authorization answers:

> What is this user allowed to do?

Checking permissions only in the frontend is not sufficient. Sensitive operations must be protected on the server.

## Database Design

Before creating tables, identify:

1. Core entities
2. Relationships
3. Required fields
4. Unique constraints
5. Common query patterns
6. Transaction boundaries

Use database constraints to protect important invariants instead of relying entirely on application code.

## Billing

Payment state should be synchronized through verified payment-provider webhooks.

```text
Checkout
   ↓
Payment Provider
   ↓
Verified Webhook
   ↓
Database
   ↓
Application State
```

Webhook handlers should be designed to safely handle duplicate events.

## Production Checklist

* [ ] Tenant boundaries enforced
* [ ] Authorization checked server-side
* [ ] Database constraints configured
* [ ] Important actions logged
* [ ] Billing state synchronized
* [ ] Background jobs monitored
* [ ] Errors observable
* [ ] Backups configured
* [ ] Recovery process documented

## Engineering Principle

> Design the system around data boundaries, permissions, and failure cases—not only the happy path.
