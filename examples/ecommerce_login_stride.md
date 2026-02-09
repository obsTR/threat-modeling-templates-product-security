# STRIDE Example: Ecommerce Login Flow

**Owner:** Product Security Team
**Date:** 2026-02-08
**Reviewer:** Security Architect

## 1. System Description
This model covers customer login for an ecommerce web application using email/password authentication with optional MFA.

## 2. Data Flow
* **Sources:** User browser input, identity provider callbacks
* **Destinations:** Authentication API, user database, audit log service
* **Trust Boundaries:** Public internet, application VPC, internal database subnet

## 3. STRIDE Analysis

| Threat Category | Description | Applicable? | Mitigation Strategy | Ticket ID |
| :--- | :--- | :--- | :--- | :--- |
| **S**poofing | Bot attempts to impersonate user accounts via credential stuffing. | Yes | MFA, device fingerprinting, breached-password checks | SEC-101 |
| **T**ampering | Session token tampering through client-side manipulation. | Yes | Signed JWTs, short TTL, server-side token validation | SEC-102 |
| **R**epudiation | User disputes a login action. | Yes | Immutable audit logs with request metadata | SEC-103 |
| **I**nformation Disclosure | Leakage of sensitive error messages revealing account status. | Yes | Generic auth errors, log redaction, TLS 1.3 | SEC-104 |
| **D**enial of Service | Login endpoint flooded with high request volume. | Yes | WAF rate limits, adaptive throttling, autoscaling | SEC-105 |
| **E**levation of Privilege | Horizontal privilege escalation through flawed role checks. | Yes | Server-side RBAC checks per request, authz middleware tests | SEC-106 |

## 4. Security Requirements
1. Enforce MFA for admins and high-risk user sessions.
2. Apply adaptive rate limiting on login and password-reset endpoints.
3. Store passwords using Argon2id with application-managed pepper.
4. Emit security telemetry for failed logins and anomaly detection.