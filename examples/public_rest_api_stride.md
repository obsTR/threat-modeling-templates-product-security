# STRIDE Example: Public REST API for Partner Integrations

**Owner:** API Platform Team
**Date:** 2026-02-08
**Reviewer:** Application Security

## 1. System Description
This model covers a versioned public REST API used by external partners to access order, catalog, and inventory data.

## 2. Data Flow
* **Sources:** Partner systems via HTTPS, API keys/OAuth clients
* **Destinations:** API gateway, backend microservices, analytics pipeline
* **Trust Boundaries:** Internet edge, API gateway boundary, service mesh boundary

## 3. STRIDE Analysis

| Threat Category | Description | Applicable? | Mitigation Strategy | Ticket ID |
| :--- | :--- | :--- | :--- | :--- |
| **S**poofing | Stolen API key used by unauthorized client. | Yes | OAuth2 client credentials, mTLS for high-trust partners | API-101 |
| **T**ampering | Request parameters manipulated to bypass business rules. | Yes | Schema validation, signed webhooks, strict allowlists | API-102 |
| **R**epudiation | Partner disputes making a destructive API call. | Yes | Request signing, correlation IDs, immutable audit records | API-103 |
| **I**nformation Disclosure | Broken object-level auth exposes another tenant's data. | Yes | Tenant scoping and object-level authorization checks | API-104 |
| **D**enial of Service | Burst traffic saturates shared backend resources. | Yes | Token bucket limits, quotas, circuit breakers | API-105 |
| **E**levation of Privilege | Scope confusion allows write on read-only client. | Yes | Fine-grained scopes and explicit authorization mapping | API-106 |

## 4. Security Requirements
1. Enforce per-tenant authorization at every data access layer.
2. Add API abuse detection for credential stuffing and scraping.
3. Require version pinning and deprecation notices for breaking changes.
